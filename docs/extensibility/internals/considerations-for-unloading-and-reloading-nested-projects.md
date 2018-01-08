---
title: "入れ子にプロジェクトのアンロードと再読み込みに関する考慮事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fd45ebf8be2732cded5c84f18338f104b76840cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>入れ子になったプロジェクトのアンロードと再読み込みに関する考慮事項
入れ子になったプロジェクトの種類を実装するときに、アンロード、プロジェクトを再読み込みすると、追加の手順を行う必要があります。 正しくソリューション イベントをリスナーに通知を正しく上げる必要があります、`OnBeforeUnloadProject`と`OnAfterLoadProject`イベント。  
  
 この方法でこれらのイベントを発生させる必要があります理由の 1 つは、ソース コード管理 (SCC) をサーバーからアイテムを削除し、追加として新しいものがある場合をしないようにする、 `Get` SCC から操作します。 この場合は、新しいファイルを SCC から読み込むされをアンロードし、それらが異なる場合に、すべてのファイルを再読み込みする必要があります。 SCC 呼び出し`ReloadItem`です。 その呼び出しの実装が、プロジェクトを削除して再作成し直して実装することによって、`IVsFireSolutionEvents`を呼び出す`OnBeforeUnloadProject`と`OnAfterLoadProject`です。 この実装を実行するときに、SCC は、プロジェクトの削除し、再追加が一時的に通知されます。 したがって、SCC は動作しませんプロジェクトの場合と、プロジェクトが実際には、サーバーから削除してから再び追加。  
  
## <a name="reloading-projects"></a>プロジェクトを再読み込み  
 実装する入れ子になったプロジェクトが再読み込みをサポートする、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>メソッドです。 実装で`ReloadItem`、再作成して、入れ子になったプロジェクトを閉じます。  
  
 通常、プロジェクトが再読み込みされるときに、IDE を発生させる、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A>と`M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)`イベント。 ただし、入れ子になったプロジェクトは削除され、再読み込みでは、親プロジェクトは、プロセスでは、IDE ではないを開始します。 親プロジェクトはソリューションのイベントを発生させません IDE には、プロセスの初期化に関する情報がないため、イベントは発生しません。  
  
 このプロセスでは、親プロジェクト呼び出しを処理するために`QueryInterface`上、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>オフ インターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>インターフェイスです。 `IVsFireSolutionEvents`発生するための IDE に指示する関数、`OnBeforeUnloadProject`を入れ子になったプロジェクトをアンロードし、発生するイベント、`OnAfterLoadProject`同じプロジェクトの再読み込みするイベントです。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [入れ子になったプロジェクト](../../extensibility/internals/nesting-projects.md)