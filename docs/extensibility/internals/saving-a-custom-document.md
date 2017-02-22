---
title: "カスタム ドキュメントの保存 | Microsoft Docs"
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
  - "永続化、カスタム ドキュメントの保存"
  - "プロジェクト [Visual Studio SDK] カスタム ドキュメントの保存"
  - "カスタムの文書を保存するエディター [Visual Studio SDK]"
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# カスタム ドキュメントの保存
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

環境 **Save** ハンドル**Save As** と **Save All** コマンド。  ユーザーが \[ENT0ENT\] をクリックすると **名前を付けて保存** ENT4ENT \[入力\] メニューの **\*\*\* or Save All \*\*\*** はすべて保存によってソリューションを閉じます次のプロセスに発生します。  
  
 ![カスタマー エディター保存](../../extensibility/internals/media/private.gif "Private")  
\[名前を付けて保存保存しカスタム エディターのイベントを処理するすべてのコマンドを保存します。  
  
 このプロセスは次の手順で詳しく説明します :  
  
1.  **保存**  と  **名前を付けて保存**  のコマンドでは環境はアクティブ ドキュメント ウィンドウを決定するために <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> サービスを使用してどの項目が格納されるかその。  アクティブ ドキュメント ウィンドウがわかっている場合は環境が実行中のドキュメントの表のドキュメントの階層のポインターと itemID アイテム ID \(\) を検索します。  詳細については、「[実行中のドキュメント テーブル](../../extensibility/internals/running-document-table.md)」を参照してください。  
  
     保存にすべてのコマンドを実行してドキュメントのテーブルに格納するには環境すべての項目の一覧をコンパイルするために情報を使用します。  
  
2.  ソリューションは <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> の呼び出しを受信すると選択した項目 \(つまり<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> サービスが公開する複数選択\) のセットを反復処理します。  
  
3.  選択した項目ごとにソリューションは保存のメニュー コマンドが有効かどうかを確認するに <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> のメソッドを呼び出すことによって階層のポインターを使用します。  一つ以上の項目を汚れて場合保存\] コマンドが有効になります。  階層が標準エディターを使用すると階層がエディターに <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> のメソッドを呼び出してダーティな状態の問い合わせに委任します。  
  
4.  がダーティ選択した各項目にソリューションは適切な階層の <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> のメソッドを呼び出すことによって階層のポインターを使用します。  
  
     カスタム エディターの場合はドキュメント データ オブジェクトとプロジェクト間の通信はプライベートです。  したがって特別な永続性の問題がこの二つのオブジェクト間で処理されます。  
  
    > [!NOTE]
    >  独自の永続性を実装する場合はメソッドを <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> の時間を節約するために呼び出すください。  このメソッドはファイルを保存しても安全であることを確認します \(たとえばファイルが読み取り専用ではありません\)。  
  
## 参照  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [開く、プロジェクト項目を保存します。](../../extensibility/internals/opening-and-saving-project-items.md)