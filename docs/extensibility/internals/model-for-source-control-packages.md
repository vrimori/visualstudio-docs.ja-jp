---
title: "ソース管理パッケージのモデル | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理 [Visual Studio SDK] モデル"
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# ソース管理パッケージのモデル
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次のモデルはソース管理の実装例を表します。  モデルで実行する必要があると照会する必要のある環境のサービスに会議のインターフェイス。  すべてのサービスと同様に実際にはサービスを通じて取得されたインターフェイスのメソッドを呼び出します。  クラス名はソース管理をどのように実行されるかを容易に識別されます。  
  
 ![SCC&#95;TUP の例](../../extensibility/internals/media/scc_tup.png "SCC\_TUP")  
ソース管理プロジェクトの例  
  
## インターフェイス  
 次の表に示すインターフェイスの一覧を使用してVisual Studio で新しいプロジェクトのソース管理を実行できます。  
  
|Interface|\[条件\]|  
|---------------|------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|\(ダーティ\) ファイルを保存または変更する前にプロジェクトおよびエディターによって呼び出されます。  このインターフェイスは <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> サービスを使用してアクセスします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|ファイルまたはディレクトリを追加削除または名前を変更するアクセス許可を要求するプロジェクトによって呼び出されます。  このインターフェイスは環境を通知するプロジェクトで承認がアクションがすべて追加削除または名前を変更すると呼び出されます。  これは <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> サービスを使用してアクセスします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|プロジェクトに追加するときに通知されるように登録する任意の要素によって実装され名前を変更したりファイルまたはディレクトリの削除します。  イベント通知を登録するには<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A> を呼び出します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|パッケージ ソース管理してソース管理のステータス情報を取得するプロジェクトによって呼び出されます。  このインターフェイスは <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> サービスを使用してアクセスします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|ファイルのソース管理の情報要求に応答しプロジェクト ファイルに必要なソース管理の設定を取得するプロジェクトによって実装されます。|  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [ソース管理をサポートします。](../../extensibility/internals/supporting-source-control.md)