---
title: "標準的なドキュメントの保存 | Microsoft Docs"
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
  - "標準的なドキュメントを保存するエディター [Visual Studio SDK]"
  - "プロジェクト [Visual Studio SDK] 標準ドキュメントの保存"
  - "永続性、標準的なドキュメントを保存します。"
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 標準的なドキュメントの保存
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

環境ハンドルは保存名前を付けて保存すべてのコマンドを保存します。  ユーザーが \[ENT4ENT\] を選択すると\[ENT8ENT\] メニューの  **名前を付けて保存** または  **すべて保存**  は **すべて保存**  によってソリューションを閉じます次のプロセスに発生します。  
  
 ![標準エディター](../../extensibility/internals/media/public.png "Public")  
\[名前を付けて保存し標準エディターで保存するすべてのコマンドを保存します。  
  
 このプロセスは次の手順で詳しく説明します :  
  
1.  **保存**  と  **名前を付けて保存**  のコマンドを選択すると環境はアクティブ ドキュメント ウィンドウを決定するために <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> サービスを使用してどの項目が格納されるかその。  アクティブ ドキュメント ウィンドウがわかっている場合は環境が実行中のドキュメントの表のドキュメントの階層のポインターと itemID アイテム ID \(\) を検索します。  詳細については、「[実行中のドキュメント テーブル](../../extensibility/internals/running-document-table.md)」を参照してください。  
  
     **すべて保存**  のコマンドを選択すると環境が実行中のドキュメントのテーブルに格納するすべての項目の一覧をコンパイルするために情報を使用します。  
  
2.  ソリューションは <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> の呼び出しを受信すると選択した項目 \(つまり<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> サービスが公開する複数選択\) のセットを反復処理します。  
  
3.  選択した項目ごとにソリューションは **Save** のメニュー コマンドが有効かどうかを確認するに <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> のメソッドを呼び出すことによって階層のポインターを使用します。  一つ以上の項目を汚れて場合**Save** のコマンドが有効になります。  階層が標準エディターを使用すると階層がエディターに <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> のメソッドを呼び出してダーティな状態の問い合わせに委任します。  
  
4.  がダーティ選択した各項目にソリューションは適切な階層の <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> のメソッドを呼び出すことによって階層のポインターを使用します。  
  
     これは階層でよくドキュメントを編集するために標準エディターを使用するとなります。  この場合エディターのドキュメント データ オブジェクトは <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> のインターフェイスをサポートする必要があります。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> のメソッド呼び出しを受け取るとプロジェクトはドキュメントがドキュメント データ オブジェクトに <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> のメソッドを呼び出して保存されるとエディターに通知します。  エディターは環境が <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> インターフェイスの `Query Service` を呼び出して ENT4ENT \[出力\] ダイアログ ボックスを処理を許可できます。  これは <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> インターフェイスへのポインターを返します。  エディターは`pPersistFile` のパラメーターにエディターの <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> の実装へのポインターを渡す <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> のメソッドを呼び出す必要があります。  環境は保存操作を実行しエディターに ENT4ENT \[出力\] ダイアログ ボックスが表示されます。  <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> のエディターに戻ります環境でを呼び出します。  
  
5.  ユーザーが未題のドキュメント \(以前に保存されていないドキュメント\) を格納すると名前を付けて保存\] コマンドを実際に実行されます。  
  
6.  \[名前を付けて保存\] コマンドに対して環境はファイル名の入力をユーザーに要求する名前を付けて保存\] ダイアログ ボックスが表示されます。  
  
     ファイルの名前が変更されている場合階層は <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>VSFPROPID\_MkDocument \(\) を呼び出してドキュメント フレームのキャッシュされた情報を更新する必要があります。  
  
 **名前を付けて保存**  のコマンドがドキュメントの場所を移動し階層が文書の場所に依存する場合階層が所有権のドキュメント ウィンドウに別の階層を渡すことを行います。  たとえばファイルはプロジェクトに関連する内部または外部のファイル \(そのほかのファイル\) かどうかプロジェクトを追跡する場合に発生します。  そのほかのファイル プロジェクトにファイルの所有権を変更するには次の手順を実行します。  
  
## ファイルの所有権の変更  
  
#### そのほかのファイルにファイルの所有権を変更するには  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> インターフェイスのクエリサービス。  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> へのポインターを返します。  
  
2.  新しい階層にドキュメントをコピーするに <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> \(`pszMkDocumentNew``punkWindowFrame`\) のメソッドを呼び出します。  \[名前を付けて保存\] コマンドを実行する階層によってこのメソッドが呼び出されます。  
  
## 参照  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [開く、プロジェクト項目を保存します。](../../extensibility/internals/opening-and-saving-project-items.md)