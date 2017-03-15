---
title: "コマンド、メニューのおよびツールバー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "メニュー [Visual Studio SDK] コマンド"
  - "コマンド [Visual Studio]"
  - "ツールバー [Visual Studio] コマンド"
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: 60
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 60
---
# コマンド、メニューのおよびツールバー
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

メニューとツールバーは、ユーザー、VSPackage でのコマンドにアクセスします。 コマンドは、印刷するドキュメント、ビューの更新ファイルの新規作成などのタスクを実行する関数です。 メニューとツールバーは、コマンドをユーザーに提示する便利なグラフィカルな手段です。 通常、関連するコマンドが密集している同じメニューまたはツールバー上。  
  
-   メニューは通常、統合開発環境 \(IDE\) やツール ウィンドウの上部にある列にクラスター化されて 1 単語の文字列として表示されます。 メニューは、右クリックのイベントの結果として表示されることができますので、そのコンテキストのショートカット メニューと呼びます。 クリックすると、1 つまたは複数のコマンドを表示するメニューを展開します。 コマンドをクリックするでは、タスクを実行したり、その他のコマンドを含むサブメニューを起動することができます。 いくつかのよく知られているメニュー名は、ファイル、編集、ビュー、およびウィンドウです。 詳細については、「[拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)」を参照してください。  
  
-   ツールバーは、ボタンとコンボ ボックス、リスト ボックス、テキスト ボックス、およびメニュー コント ローラーなど他のコントロールの行を通常です。 すべてのツール バー コントロールは、コマンドに関連付けられます。 ツール バー ボタンをクリックすると、関連付けられているコマンドがアクティブ化されます。 ツール バー ボタンには、通常、\[印刷\] コマンド用のプリンターなどの基になるコマンドを示すアイコンがあります。 ドロップダウン リスト コントロールでは、一覧内の各項目は、別のコマンドに関連付けられます。 メニューの \[コント ローラーは、コントロールの 1 つの辺がツール バー ボタン、もう一方の側がクリックされたときにその他のコマンドを示す下向きの矢印でのハイブリッドです。 詳細については、「[ツールバー\] メニューの \[コント ローラーの追加](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)」を参照してください。  
  
-   コマンドを作成するときに作成することも必要があります、イベント ハンドラーにします。 では、テキストを変更するコマンドを表示するか、有効な場合、イベント ハンドラーを決定し、コマンドが適切に応答することにより、\(「ルート」\) でアクティブ化されるときです。 大半の場合、IDE の処理コマンドを使用して、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスです。 コマンドを [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 以降では、ローカルの選択に基づくし、グローバルの選択に基づいて、最も外側のコンテキストを続行する、最も内側にあるコマンド コンテキストは階層的にルーティングします。 メイン メニューに追加されたコマンドは、スクリプトを実行してすぐに利用可能です。 詳細については、次のトピックを参照してください。[MenuCommand と  OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md) および[コンテキスト オブジェクトの選択](../../extensibility/internals/selection-context-objects.md).  
  
 新しいメニューおよびツールバーを定義するには、Visual Studio コマンド テーブル \(.vsct\) ファイル内に説明する必要があります。 Visual Studio パッケージ テンプレートでは、どのようなコマンド、ツールバー、およびテンプレートで選択されているエディターをサポートするために必要な要素と共に、このファイルを作成します。 また、ファイルを作成し、独自 .vsct、ここで説明されている xml スキーマを使用して: [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)です。  
  
 .Vsct ファイルの使用に関する詳細については、次を参照してください。 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)します。  
  
 このセクションのトピックでは、Vspackage でのコマンド、メニューのおよびツールバーのしくみについて説明します。  
  
## このセクションの内容  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 コマンド テーブルの書式指定の詳細な説明です。  
  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 XML ベースの構文とコマンド テーブルのためにコンパイラについて説明します。  
  
 [既定のコマンド、グループ、およびツールバーの配置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 定義済みのコマンド、グループ、メニューのおよびツールバーについて説明します。  
  
 [IDE 定義コマンド、メニューのおよびグループ](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 定義済みのメニューのコマンド、およびコマンド グループで使用可能な指定、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE です。  
  
 [コマンドのデザイン](../../extensibility/internals/command-design.md)  
 コマンドをデザインする方法について説明します。  
  
 [メニューとツールバーのコマンドを最適化します。](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 コマンドについてのガイドラインを提供します。  
  
 [コマンドを使用できるようにします。](../../extensibility/internals/making-commands-available.md)  
 Visual Studio でのコマンドを使用できるようにする方法について説明します。  
  
 [コマンドと相互運用機能アセンブリを使用してメニュー](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 相互運用機能アセンブリを使用するコマンドを実装する方法について説明します。  
  
## 関連項目  
 [Vspackage でルーティング コマンド](../../extensibility/internals/command-routing-in-vspackages.md)  
 Vspackage でのコマンドのルーティングについて説明します。