---
title: "ソース管理の構成の詳細 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理 [Visual Studio SDK] 構成の詳細"
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# ソース管理の構成の詳細
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソース管理を実装するには適切なプロジェクト システム エディターまたは次のように構成する必要があります :  
  
-   変更された状態への遷移へアクセス許可の要求  
  
-   ファイルを保存するためのアクセス許可  
  
-   プロジェクト ファイルを追加削除または名前を変更するアクセス許可を要求します。  
  
## 変更された状態への遷移へアクセス許可の要求  
 プロジェクトまたはエディターで変更された \(ダーティ\) 状態に遷移します <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> を呼び出してアクセス許可を要求する必要があります。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> を実行する各エディターは <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> を呼び出し`M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)` の `True` を返す前に環境からドキュメントを変更するための承認を受信する必要があります。  プロジェクトは基本的にプロジェクト ファイルのエディターでテキスト エディターでファイルの場合と同様にこのためプロジェクト ファイルで追跡している状態変更を実装するための同じ必要があります。  環境ハンドル ソリューションの状態が変更されたソリューションの参照オブジェクトで変更された状態を処理する必要がありますがプロジェクト ファイルや項目などに保存されません。  一般にプロジェクトまたは項目がエディターの永続性を管理する必要がある場合その状態変更の追跡を実行する必要があります。  
  
 `IVsQueryEditQuerySave2::QueryEditFiles` の呼び出しに対して環境は次のことがあります :  
  
-   エディターまたはプロジェクトをインバリアント \(\) クリーンな状態にある場合は変更する呼び出しを拒否します。  
  
-   ドキュメント データに再度読み込む必要があることを示します。  プロジェクトの場合環境はプロジェクト データを再読み込みします。  エディターはディスクから <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> の実装によってデータを再読み込みする必要があります。  いずれの場合もデータが再び読み込まれるとプロジェクトのコンテキストまたはエディターで変更できます。  
  
 また既存のコード ベースに `IVsQueryEditQuerySave2::QueryEditFiles` の適切な呼び出しを行うだけ複雑ななりです。  したがってこれらの呼び出しはプロジェクトまたはエディターの作成時に統合されます。  
  
## ファイルを保存するためのアクセス許可  
 プロジェクトまたはエディターでファイルを保存する前に<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> または <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> を呼び出す必要があります。  プロジェクト ファイルの場合この呼び出しによってプロジェクト ファイルを保存するかを確認するソリューションで自動的に実行されます。  エディターが `IVsPersistDocData2` エディターの実装でヘルパー関数の <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> を使用するこれらの呼び出しを行います。  エディターが `IVsPersistDocData2` をこのように実装する場合はの `IVsQueryEditQuerySave2::QuerySaveFile` または `IVsQueryEditQuerySave2::QuerySaveFiles` の呼び出しが行われます。  
  
> [!NOTE]
>  エディターでキャンセルを受け取ることができる場合優先これらの呼び出しは常にします。  
  
## プロジェクト ファイルを追加削除または名前を変更するためのアクセス許可  
 プロジェクトではファイルまたはディレクトリを追加するか名前を変更または削除する前に環境のアクセス許可を要求する `IVsTrackProjectDocuments2::OnQuery*` のメソッドを呼び出す必要があります。  アクセス許可が付与されると操作が完了すると操作を完了し環境を通知するために `IVsTrackProjectDocuments2::OnAfter*` のメソッドを呼び出す必要があります。  プロジェクトはすべてのファイル \(たとえば特殊なファイル\) と親ファイルの <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> インターフェイスのメソッドを呼び出す必要があります。  ファイルの呼び出しが必要ですがディレクトリの呼び出しは省略可能です。  プロジェクトのディレクトリの情報がある場合推論するディレクトリ情報を <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> の適切なメソッドこの情報がない場合は環境を呼び出す必要があります。  
  
 プロジェクトにはプロジェクトのように `IVsTrackProjectDocuments2` のメソッドを呼び出すかまたは閉じる必要があります。  起動時にこの情報が必要なリスナーは <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> のイベントを待機してからソリューションに必要な情報を見つけるに反復処理することもできます。  シャットダウン時にこの情報は必要ではありません。  `IVsTrackProjectDocuments2` は <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> から提供されます。  
  
 それぞれに追加し名前を変更してアクションを削除します `OnQuery*`のメソッドと `OnAfter*` のメソッドがあります。  ファイルまたはディレクトリを追加名前の変更または削除を行うアクセス許可を求める `OnQuery*` のメソッドを呼び出します。  ファイルまたはディレクトリとプロジェクトの状態を反映する新しい状態を追加や名前を変更したりまたは削除され後 `OnAfter*` のメソッドを呼び出します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [ソース管理をサポートします。](../../extensibility/internals/supporting-source-control.md)