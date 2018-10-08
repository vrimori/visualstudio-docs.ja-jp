---
title: ソース管理パッケージのモデル |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 220d8596827c637b578e4ccb52796607b9bfd413
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537450"
---
# <a name="model-for-source-control-packages"></a>ソース管理パッケージのモデル
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ソース管理パッケージのモデル](https://docs.microsoft.com/visualstudio/extensibility/internals/model-for-source-control-packages)します。  
  
次のようなモデルでは、ソース コントロールの実装の例を表します。 モデルでは、インターフェイスを実装する必要があり、呼び出す必要のある環境のサービスを参照してください。 すべてのサービスと同様に実際には、サービスを使用して取得する特定のインターフェイスのメソッドを呼び出します。 クラスの名前は、ソース管理の実行方法を確認するが容易に識別されます。  
  
 ![SCC&#95;TUP 例](../../extensibility/internals/media/scc-tup.gif "SCC_TUP")  
ソース管理プロジェクトの例  
  
## <a name="interfaces"></a>インターフェイス  
 ソース管理は、次の表で示されるインターフェイスのリストを使用して Visual Studio で、新しいプロジェクトの種類を実装できます。  
  
|Interface|使用|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|プロジェクトと保存、または変更 (ダーティ) ファイルの前にエディターによって呼び出されます。 使用してこのインターフェイスをアクセス、<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>サービス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|追加、削除、またはファイルまたはディレクトリの名前を変更する許可を要求するプロジェクトによって呼び出されます。 このインターフェイスは、プロジェクトが完了すると、承認済みの追加、削除、またはアクションの名前を変更するときに、環境を通知するためとも呼ばれます。 使用してアクセス、<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>サービス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|プロジェクトの追加、名前の変更、またはファイルまたはディレクトリを削除するときに通知するように登録するすべてのエンティティによって実装されます。 イベント通知を登録するには、呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|ソース管理パッケージを登録して、ソース管理の状態に関する情報を取得するプロジェクトによって呼び出されます。 使用してこのインターフェイスをアクセス、<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>サービス。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|プロジェクト ファイルに関する情報のソース制御要求に応答して、プロジェクト ファイルに必要なコントロールの設定を取得するには、ソースによって実装されます。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [ソース管理のサポート](../../extensibility/internals/supporting-source-control.md)

