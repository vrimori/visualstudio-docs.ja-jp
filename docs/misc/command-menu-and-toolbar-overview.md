---
title: "コマンド、メニュー、ツール バーの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "メニューの基本事項 [Visual Studio SDK]"
  - "ツール バーの基本事項 [Visual Studio SDK]"
ms.assetid: cbdaceaa-7dd3-4a56-aea6-b759e48d83d6
caps.latest.revision: 19
caps.handback.revision: 19
manager: "douge"
---
# コマンド、メニュー、ツール バーの概要
メニューとツール バーは、ユーザーが VSPackage のコマンドに直感的にアクセスするための便利な方法です。 コマンドは、ドキュメントの印刷、ビューの更新、ファイルの新規作成などのタスクを実行する関数です。 メニューとツール バーは、ユーザーにコマンドをグラフィカルに表示する便利な方法です。 通常、関連するコマンドは、同じメニューやツール バーにまとめられます。  
  
-   メニューは通常、統合開発環境 \(IDE\) やツール ウィンドウの上部にある列にまとめられた 1 語の文字列として表示されます。 メニューは、右クリック イベントの結果として表示することもでき、これはそのコンテキストのショートカット メニューと呼ばれます。 クリックすると、メニューが展開して 1 つ以上のコマンドが表示されます。 コマンドをクリックすると、タスクを実行したり、追加のコマンドを含むサブメニューを起動したりすることができます。 よく知られているメニュー名には、\[ファイル\]、\[編集\]、\[表示\]、\[ウィンドウ\] などがあります。 詳細については、「[拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)」を参照してください。  
  
-   ツール バーは通常、ボタンと他のコントロール \(コンボ ボックス、リスト ボックス、テキスト ボックス、メニュー コント ローラーなど\) の行です。 すべてのツール バー コントロールは、コマンドに関連付けられます。 ツール バー ボタンをクリックすると、関連付けられているコマンドがアクティブ化されます。 ツール バー ボタンには、通常、\[印刷\] コマンド用のプリンターなどの基になるコマンドを示すアイコンがあります。 ドロップダウン リスト コントロールでは、リスト内の各項目は、異なるコマンドに関連付けられています。 メニュー コントローラーは、コントロールの一方の側がツール バー ボタン、もう一方の側が、クリックして追加のコマンドを表示する下矢印の組み合わせです。 詳細については、次のトピックを参照してください。[方法: ツール ウィンドウのツールバーを作成する](../misc/how-to-create-toolbars-for-tool-windows.md) および[メニュー コマンドにアイコンを追加します。](../extensibility/adding-icons-to-menu-commands.md).  
  
-   コマンドを作成するときは、コマンド用のイベント ハンドラーも作成する必要があります。 イベント ハンドラーでは、コマンドをいつ表示または有効にするかを決定し、コマンドのテキストを変更し、アクティブ化したときにコマンドが適切に応答する \(「ルーティングする」\) ようにすることができます。 ほとんどの場合、IDE では <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスを使用してコマンドを処理します。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ではコマンドは階層形式でルーティングし、ローカルの選択に基づいて最も内側のコマンド コンテキストから開始し、グローバルの選択に基づいて最も外側のコンテキストに進みます。 メイン メニューに追加したコマンドは、すぐにスクリプトに利用できます。 詳細については、次のトピックを参照してください。[MenuCommand と  OleMenuCommand](../misc/menucommands-vs-olemenucommands.md) および[コンテキスト オブジェクトの選択](../extensibility/internals/selection-context-objects.md).  
  
 新しいメニューやツール バーを定義するには、それらを Visual Studio コマンド テーブル \(.vsct\) ファイルで記述する必要があります。 Visual Studio パッケージ テンプレートでは、このファイルが、テンプレートで選択したすべてのコマンド、ツール バー、エディターをサポートするために必要な要素と共に作成されます。 または、「[VSCT XML スキーマ リファレンス](../extensibility/vsct-xml-schema-reference.md)」で説明されている XML スキーマを使用して、独自の .vsct ファイルを作成することもできます。  
  
 .vsct ファイルの使用方法の詳細については、「[Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)」、または「[ユーザー インターフェイス要素のチュートリアル](../misc/walkthroughs-for-user-interface-elements.md)」のいずれかを参照してください。  
  
 メニューとツール バーのさらに詳しい説明は、「[コマンドのデザイン](../extensibility/internals/command-design.md)」を参照してください。  
  
## 参照  
 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)   
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Vspackages にあります。](../extensibility/internals/vspackages.md)