---
title: 入れ子にプロジェクトのアンロードと再ロードに関する考慮事項 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b5738a5e8cf01466dd632797c3f92ffd135a44
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942741"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>アンロード中で入れ子になったプロジェクトを再読み込みに関する考慮事項

入れ子になったプロジェクトの種類を実装するときに、アンロード、プロジェクトの再読み込みすると、追加の手順を行う必要があります。 ソリューションのイベント リスナーを正しく通知するを上げる必要があります正しく、`OnBeforeUnloadProject`と`OnAfterLoadProject`イベント。

これらのイベントを発生させる理由の 1 つが、ソース コード管理 (SCC) です。 サーバーから項目を削除し、それらを追加するには、ソース コード管理をしたくないとして*新しい*がある場合、 `Get` SCC から操作します。 その場合は、新しいファイルは、SCC から読み込まれます。 アンロードし、は異なり、場合、すべてのファイルを再読み込みする必要があります。

ソース コード コントロール呼び出し`ReloadItem`します。 実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>インターフェイスを呼び出す`OnBeforeUnloadProject`と`OnAfterLoadProject`をプロジェクトを削除して再作成します。 この方法でインターフェイスを実装すると、SCC は、プロジェクトの削除し、追加をもう一度が一時的に通知されます。 そのため、SCC はプロジェクトの操作として動作がプロジェクトに*実際に*削除され、再度追加します。

## <a name="reload-projects"></a>プロジェクトの再読み込み

実装する入れ子になったプロジェクトの再読み込みをサポートする、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>メソッド。 実装で`ReloadItem`、再作成して、入れ子になったプロジェクトを閉じます。

通常、プロジェクトの再読み込みが、IDE が発生、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>イベント。 ただし、親プロジェクトが削除され、再読み込みされる入れ子になったプロジェクトでは、IDE ではありません、プロセスを開始します。 親プロジェクトはソリューションのイベントを発生させる、IDE には、プロセスの初期化に関する情報がないため、イベントは発生します。

このプロセスでは、親プロジェクトの呼び出しを処理する`QueryInterface`上、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>インターフェイス。 `IVsFireSolutionEvents` 関数を生成するための IDE に指示するには、`OnBeforeUnloadProject`を入れ子になったプロジェクトをアンロードし、発生させるイベント、`OnAfterLoadProject`同じプロジェクトを再読み込みイベント。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [入れ子のプロジェクト](../../extensibility/internals/nesting-projects.md)