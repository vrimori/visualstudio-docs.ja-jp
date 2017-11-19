---
title: "ソース管理パッケージのモデル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a8dacc0a3dfc230085c7575960238711d16d1ef8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="model-for-source-control-packages"></a>ソース管理パッケージのモデル
次のようなモデルでは、ソース コントロールの実装の例を表します。 モデルでは、インターフェイスを実装する必要があり、環境サービスを呼び出してくださいを参照してください。 すべてのサービスと同様には、実際には、サービスを使用して取得する特定のインターフェイスのメソッドを呼び出します。 クラスの名前は、ソース管理の実行方法を表示するが容易に識別されます。  
  
 ![SCC &#95;です。TUP 例](../../extensibility/internals/media/scc_tup.gif "SCC_TUP")  
ソース管理プロジェクトの例  
  
## <a name="interfaces"></a>インターフェイス  
 次の表に示されるインターフェイスのリストを使用して Visual Studio で、新しいプロジェクトの種類のソース管理を実装できます。  
  
|インターフェイス|用途|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|プロジェクトおよび変更 (ダーティ) ファイルまたは保存する前にエディターによって呼び出されます。 このインターフェイスを使用してアクセスは、<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>サービス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|追加、削除、またはファイルまたはディレクトリの名前を変更する許可を要求するプロジェクトによって呼び出されます。 このインターフェイスは、完全な承認された追加、削除、またはアクションの名前を変更するときに、環境を通知するためにプロジェクトによっても呼び出されます。 アクセスを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>サービス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|プロジェクトの追加、名前の変更、またはファイルまたはディレクトリを削除するときに通知を登録するすべてのエンティティによって実装されます。 イベント通知を登録するには、呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>です。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|ソース管理パッケージに登録して、ソース管理の状態に関する情報を取得プロジェクトによって呼び出されます。 このインターフェイスを使用してアクセスは、<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>サービス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|プロジェクト ファイルに関する情報のソース コントロールの要求に応答して、設定を取得するソース管理プロジェクト ファイルに必要なによって実装されます。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [ソース管理のサポート](../../extensibility/internals/supporting-source-control.md)