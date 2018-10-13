---
title: 入れ子にプロジェクトのアンロードと再ロードに関する考慮事項 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1712c05ab1bd6dbf32537d4306517ddf189b4084
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49277563"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>入れ子になったプロジェクトのアンロードと再ロードに関する考慮事項
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

入れ子になったプロジェクトの種類を実装するときに、アンロード、プロジェクトの再読み込みすると、追加の手順を行う必要があります。 ソリューションのイベント リスナーを正しく通知するを上げる必要があります正しく、`OnBeforeUnloadProject`と`OnAfterLoadProject`イベント。  
  
 この方法でこれらのイベントを発生させる必要があります理由の 1 つは、ソース コード管理、サーバーから、項目を削除し、追加として新しいものがある場合 (SCC) をしないようにする、 `Get` SCC から操作します。 その場合は、新しいファイルはソース コード管理から読み込まれます、アンロードし、は異なる場合に、すべてのファイルを再読み込みする必要があります。 SCC 呼び出し`ReloadItem`します。 その呼び出しの実装では、プロジェクトの削除を再実装することでもう一度作成`IVsFireSolutionEvents`を呼び出す`OnBeforeUnloadProject`と`OnAfterLoadProject`します。 この実装を実行するときに、SCC は、プロジェクトの削除し、追加をもう一度が一時的に通知されます。 そのため、SCC は動作しません、プロジェクトのプロジェクトが実際には、サーバーから削除し、もう一度追加し、まるで。  
  
## <a name="reloading-projects"></a>プロジェクトを再読み込み  
 実装する入れ子になったプロジェクトの再読み込みをサポートする、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>メソッド。 実装で`ReloadItem`、再作成して、入れ子になったプロジェクトを閉じます。  
  
 通常、プロジェクトの再読み込みが、IDE が発生、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A>と`M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)`イベント。 ただし、親プロジェクトは削除され、再読み込みする入れ子になったプロジェクトでは、IDE ではない、プロセスを開始します。 親プロジェクトでは、ソリューションのイベントは発生しません、IDE には、プロセスの初期化に関する情報がないため、イベントは発生しません。  
  
 このプロセスでは、親プロジェクトの呼び出しを処理する`QueryInterface`上、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>オフ インターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>インターフェイス。 `IVsFireSolutionEvents` 関数を生成するための IDE に指示するには、`OnBeforeUnloadProject`を入れ子になったプロジェクトをアンロードし、発生させるイベント、`OnAfterLoadProject`同じプロジェクトを再読み込みイベント。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [入れ子になったプロジェクト](../../extensibility/internals/nesting-projects.md)

