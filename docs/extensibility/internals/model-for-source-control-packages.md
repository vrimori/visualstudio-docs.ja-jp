---
title: ソース管理パッケージのモデル |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 992fd9a6f45d607538f1091eb7a652984595cc34
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954501"
---
# <a name="model-for-source-control-packages"></a>ソース管理パッケージのモデル
次のようなモデルでは、ソース コントロールの実装の例を表します。 モデルでは、インターフェイスを実装する必要があり、呼び出す必要のある環境のサービスを参照してください。 すべてのサービスと同様に実際には、サービスを使用して取得する特定のインターフェイスのメソッドを呼び出します。 クラスの名前は、ソース管理の実行方法を確認するが容易に識別されます。  
  
 ![SCC&#95;TUP 例](../../extensibility/internals/media/scc_tup.gif "SCC_TUP")  
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