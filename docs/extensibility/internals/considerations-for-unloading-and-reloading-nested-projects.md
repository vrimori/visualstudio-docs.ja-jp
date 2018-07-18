---
title: 入れ子にプロジェクトのアンロードと再読み込みに関する考慮事項 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7f22575c4affa6e6a13ea80b32674a3e517202fb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127928"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>入れ子になったプロジェクトのアンロードと再読み込みに関する考慮事項

入れ子になったプロジェクトの種類を実装するときに、アンロード、プロジェクトを再読み込みすると、追加の手順を行う必要があります。 正しくソリューション イベントをリスナーに通知を正しく上げる必要があります、`OnBeforeUnloadProject`と`OnAfterLoadProject`イベント。

これらのイベントを発生させる理由の 1 つは、ソース コード管理 (SCC) です。 SCC は、サーバーから項目を削除し、それらを追加したくないとして再度*新しい*がある場合、 `Get` SCC から操作します。 その場合は、新しいファイルを SCC 外読み込まれるとします。 アンロードし、は異なり、場合に、すべてのファイルを再読み込みする必要があります。

ソース コード コントロール呼び出し`ReloadItem`です。 実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>を呼び出すインターフェイス`OnBeforeUnloadProject`と`OnAfterLoadProject`をプロジェクトを削除し、再作成します。 この方法で、インターフェイスを実装するときに、プロジェクトの削除し、再追加が一時的に SCC に通知します。 したがって、SCC しないように動作プロジェクトのプロジェクトが*実際に*削除し、再追加されました。

## <a name="reloading-projects"></a>プロジェクトを再読み込み

実装する入れ子になったプロジェクトが再読み込みをサポートする、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>メソッドです。 実装で`ReloadItem`、再作成して、入れ子になったプロジェクトを閉じます。

通常、プロジェクトが再読み込みされるときに、IDE を発生させる、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>イベント。 ただし、入れ子になったプロジェクトが削除され、再読み込みでは、親プロジェクトは、プロセスでは、IDE ではないを開始します。 親プロジェクトがソリューションのイベントを発生しないため、IDE は、プロセスの初期化に関する情報を持たないイベントは発生します。

このプロセスでは、親プロジェクト呼び出しを処理するために`QueryInterface`上、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>インターフェイスです。 `IVsFireSolutionEvents` 発生するための IDE に指示する関数、`OnBeforeUnloadProject`を入れ子になったプロジェクトをアンロードし、発生するイベント、`OnAfterLoadProject`同じプロジェクトの再読み込みするイベントです。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [入れ子になったプロジェクト](../../extensibility/internals/nesting-projects.md)