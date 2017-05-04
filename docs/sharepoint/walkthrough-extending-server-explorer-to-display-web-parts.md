---
title: "Walkthrough: Extending Server Explorer to Display Web Parts | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint commands"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 5b1f104a-0eaf-4929-9f1f-d7afcfc8b707
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Walkthrough: Extending Server Explorer to Display Web Parts
  Visual Studioでは、SharePointサイトのコンポーネントを表示するために **\[サーバー エクスプローラ\]** の **\[SharePoint 接続\]** のノードを使用できます。  ただし、**\[サーバー エクスプローラ\]** は、コンポーネントが既定では表示されません。  このチュートリアルでは、接続されている各SharePointサイトのWebパーツ ギャラリーを表示できるように **\[サーバー エクスプローラ\]** を拡張します。  
  
 このチュートリアルでは、次のタスクを実行します。  
  
-   **サーバー エクスプローラー**を拡張する Visual Studio 拡張機能を作成する。具体的には、次の点を拡張します。  
  
    -   拡張子は **\[サーバー エクスプローラ\]**の各SharePointサイト ノードに **\[Web パーツ ギャラリー\]** のノードを追加します。  この新しいノードには、サイト上の Web パーツ ギャラリー内の個々の Web パーツを表す子ノードが表示されます。  
  
    -   拡張機能では、Webパーツのインスタンスを表す新しいノード型を定義します。  新しい **Web パーツ ギャラリー** ノードの子ノードには、このノード型が使用されます。  新しい Web パーツ ノード型が表す Web パーツについての情報は、**\[プロパティ\]** ウィンドウに表示されます。  ノード型には、Webパーツに関連する他のタスクの開始点として使用できるカスタム ショートカット メニュー項目があります。  
  
-   拡張機能アセンブリが呼び出す2とおりのカスタムSharePointコマンドを作成します。  SharePointコマンドは、SharePointのサーバー オブジェクト モデルのAPIを使用する拡張機能のアセンブリから呼び出すことのできるメソッドです。  このチュートリアルでは、開発コンピューター上のローカル SharePoint サイトから Web パーツ情報が取得するコマンドを作成します。  詳細については、「[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)」を参照してください。  
  
-   拡張機能を配置するための Visual Studio Extension \(VSIX\) パッケージを構築する。  
  
-   拡張機能をデバッグしてテストする。  
  
> [!NOTE]  
>  サーバー オブジェクト モデルの代わりにSharePointのクライアント オブジェクト モデルを使用して、このチュートリアルの代替バージョンについては、[Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   Windows SharePoint、およびサポートされるVisual Studioのエディション。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   Visual Studio SDK。  このチュートリアルでは、SDK の **VSIX プロジェクト** テンプレートを使用して、プロジェクト項目を配置するための VSIX パッケージを作成します。  詳細については、「[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
 次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   SharePointのサーバー オブジェクト モデルの使用。  詳細については、「[Using the SharePoint Foundation Server\-Side Object Model \(SharePoint Foundation Server 側オブジェクト モデルの使用\)](http://go.microsoft.com/fwlink/?LinkId=177796)」を参照してください。  
  
-   SharePoint ソリューションの Web パーツ。  詳細については、「[Web Parts Overview \(Web パーツの概要\)](http://go.microsoft.com/fwlink/?LinkId=177803)」を参照してください。  
  
## プロジェクトの作成  
 このチュートリアルを完了するには、3種類のプロジェクトを作成する必要があります:  
  
-   拡張機能を配置するために VSIX パッケージを作成する VSIX プロジェクト。  
  
-   プロジェクトの拡張機能を実装するクラス ライブラリ プロジェクト。  このプロジェクトが.NET Framework 4.5を対象とする必要があります。  
  
-   カスタムの SharePoint コマンドを定義するクラス ライブラリ プロジェクト。  このプロジェクトは .NET Framework 3.5 を対象にする必要があります。  
  
 この 2 つのプロジェクトを作成することから始めます。  
  
#### VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで **\[ファイル\]**、**\[新規\]**、**\[プロジェクト\]** の順にクリックします。  
  
3.  **\[新しいプロジェクト\]** のダイアログ ボックスで、**\[Visual C\#\]** または **\[Visual Basic\]** のノードを展開し、**\[機能拡張\]** のノードを選択します。  
  
    > [!NOTE]  
    >  **\[機能拡張\]** のノードは、Visual Studio SDKをインストールするときだけです。  詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
4.  ダイアログ ボックスの上部に、.NET Frameworkのバージョンの **\[.NET Framework 4.5\]** リストのを選択します。  
  
5.  **\[VSIX プロジェクト\]** テンプレートを選択し、プロジェクト **\[WebPartNode\]**を付けておくと、**\[OK\]** のボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の**ソリューション エクスプローラー**に **WebPartNode** プロジェクトが追加されます。  
  
#### 拡張機能プロジェクトを作成するには  
  
1.  **\[ソリューション エクスプローラー\]**で、ソリューション ノードのショートカット メニューを開き、**\[追加\]**を選択し、を **\[新しいプロジェクト\]**を選択します。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトで**ソリューション エクスプローラー**にソリューション ノードが表示されるのは、[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/ja-jp/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)の **\[常にソリューションを表示\]** チェック ボックスがオンになっている場合だけです。  
  
2.  次に **\[新しいプロジェクト\]** のダイアログ ボックスで、**\[Visual C\#\]** のノードまたはノードを **\[Visual Basic\]**、およびオプションの **\[ウィンドウ\]** のノードを展開します。  
  
3.  ダイアログ ボックスの上部に、.NET Frameworkのバージョンの **\[.NET Framework 4.5\]** リストのを選択します。  
  
4.  プロジェクト テンプレートの一覧で、**\[クラス ライブラリ\]**を選択し、プロジェクト **\[WebPartNodeExtension\]**を付けておくと、**\[OK\]** のボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって、**WebPartNodeExtension** プロジェクトがソリューションに追加され、既定の Class1 コード ファイルが開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
#### SharePoint コマンド プロジェクトを作成するには  
  
1.  **\[ソリューション エクスプローラー\]**で、ソリューション ノードのショートカット メニューを開き、**\[追加\]**を選択し、を **\[新しいプロジェクト\]**を選択します。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトで**ソリューション エクスプローラー**にソリューション ノードが表示されるのは、[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/ja-jp/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)の **\[常にソリューションを表示\]** チェック ボックスがオンになっている場合だけです。  
  
2.  **\[新しいプロジェクト\]** のダイアログ ボックスで、**\[Visual C\#\]** の **\[Visual Basic\]** のノードまたはノードを展開し、**\[ウィンドウ\]** のノードを選択します。  
  
3.  ダイアログ ボックスの上部に、.NET Frameworkのバージョンの **\[.NET Framework 3.5\]** リストのを選択します。  
  
4.  プロジェクト テンプレートの一覧で、**\[クラス ライブラリ\]**を選択し、プロジェクト **\[WebPartCommands\]**を付けておくと、**\[OK\]** のボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって、**WebPartCommands** プロジェクトがソリューションに追加され、既定の Class1 コード ファイルが開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
## プロジェクトの構成  
 拡張機能を作成するためのコードを記述する前に、コード ファイルおよびアセンブリ参照を追加し、プロジェクトの設定を構成します。  
  
#### WebPartNodeExtension プロジェクトを構成するには  
  
1.  WebPartNodeExtensionプロジェクトで、次の名前を持つ4種類のコード ファイルを追加します:  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  **\[WebPartNodeExtension\]** のプロジェクトのショートカット メニューを開き、**\[参照の追加\]**を選択します。  
  
3.  **\[マネージャーの– WebPartNodeExtensionを参照してください。\]** のダイアログ ボックスで、**\[Framework\]** のタブをクリックし、次のアセンブリのチェック ボックスをオンにします:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  **\[拡張機能\]** のタブをクリックし、Microsoft.VisualStudio.SharePointアセンブリのチェック ボックスをオンに **\[OK\]** のボタンをクリックします。  
  
5.  **\[ソリューション エクスプローラー\]**では、**\[WebPartNodeExtension\]** のプロジェクト ノードのショートカット メニューを開き、**\[プロパティ\]**を選択します。  
  
     **プロジェクト デザイナー**が開きます。  
  
6.  **\[アプリケーション\]** のタブをクリックします。  
  
7.  **\[既定の名前空間\]** ボックス \(C\#\)、または **\[ルート名前空間\]** ボックス \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) では、**ServerExplorer.SharePointConnections.WebPartNode**を入力します。  
  
#### WebPartCommands プロジェクトを構成するには  
  
1.  WebPartCommandsでは、WebPartCommandsという名前のコード ファイルをプロジェクトを追加します。  
  
2.  **\[ソリューション エクスプローラー\]**では、**\[WebPartCommands\]** のプロジェクト ノードのショートカット メニューを開き、**\[追加\]**を選択し、を **\[既存の項目\]**を選択します。  
  
3.  **\[既存項目の追加\]** のダイアログ ボックスで、WebPartNodeExtensionプロジェクトのコード ファイルが格納されているフォルダーを参照し、WebPartNodeInfoおよびWebPartCommandIdsのコード ファイル フォルダーを選択します。  
  
4.  矢印を **\[追加\]** のボタンの横にあるを選択し、表示されるメニューの **\[リンクとして追加\]** を選択します。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] により、WebPartCommands プロジェクトにリンクとしてコード ファイルが追加されます。  その結果、コード ファイルはWebPartNodeExtensionプロジェクトにありますが、そのファイル内のコードは、WebPartCommandsプロジェクトでコンパイルされます。  
  
5.  **\[WebPartCommands\]** のプロジェクトのショートカット メニューを再度開き、**\[参照の追加\]**を選択します。  
  
6.  **\[マネージャーの– WebPartCommandsを参照してください。\]** のダイアログ ボックスで、**\[拡張機能\]** のタブをクリックし、次のアセンブリのチェック ボックスをオンに **\[OK\]** のボタンを選択する:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  **\[ソリューション エクスプローラー\]**では、**\[WebPartCommands\]** のプロジェクトのショートカット メニューを再度開き、**\[プロパティ\]**を選択します。  
  
     **プロジェクト デザイナー**が開きます。  
  
8.  **\[アプリケーション\]** のタブをクリックします。  
  
9. **\[既定の名前空間\]** ボックス \(C\#\)、または **\[ルート名前空間\]** ボックス \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) では、**ServerExplorer.SharePointConnections.WebPartNode**を入力します。  
  
## 新しいノードのアイコンの作成  
 **サーバー エクスプローラー**の拡張機能に対して 2 つのアイコンを作成します。新しい **Web パーツ ギャラリー** ノードのアイコンと、**Web パーツ ギャラリー** ノード下に存在するそれぞれの子 Web パーツ ノードのアイコンです。  これらのアイコンをノードに関連付けるコードは後で作成します。  
  
#### ノードのアイコンを作成するには  
  
1.  **\[ソリューション エクスプローラー\]**では、**\[WebPartNodeExtension\]** のプロジェクトのショートカット メニューを開き、**\[プロパティ\]**を選択します。  
  
2.  **プロジェクト デザイナー**が開きます。  
  
3.  **\[リソース\]** タブをクリックし、この**プロジェクトを含まない既定のリソース ファイルを選択します。1** 種類のリンクを作成するには、ここをクリックしてください。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は、リソース ファイルと開き、デザイナーで開かれます作成します。  
  
4.  デザイナーの上部で、下向きの矢印を **\[リソースの追加\]** のメニュー コマンドの横にあるを選択し、表示されるメニューの **\[新しいアイコンの追加\]** を選択します。  
  
5.  **\[新しいリソースの追加\]** のダイアログ ボックスでは、新しいアイコンを **WebPartsNode**し、**\[追加\]** のボタンをクリックします。  
  
     **イメージ エディター**に新しいアイコンが表示されます。  
  
6.  簡単に検証しやすいデザインとなるよう16x16版のアイコン ファイルを編集します。  
  
7.  32x32版のアイコンのショートカット メニューを開き、**\[イメージ タイプの削除\]**を選択します。  
  
8.  手順5からプロジェクト リソースに2番目のアイコンを追加する8を繰り返します。このアイコン **\[Web パーツ\]**を表示します。  
  
9. **\[WebPartNodeExtension\]** のプロジェクトの **\[リソース\]** フォルダーの下の **\[ソリューション エクスプローラー\]**では、を開きます **\[WebPartsNode.ico\]**のショートカット メニュー。  
  
10. **\[プロパティ\]** のペインで、の横の矢印を **\[ビルド アクション\]**選択し、表示されるメニューの **\[埋め込みリソース\]** を選択します。  
  
11. **WebPart.ico** について最後の 2 つの手順を繰り返します。  
  
## サーバー エクスプローラーへの Web パーツ ギャラリー ノードの追加  
 各 SharePoint サイト ノードに新しい **Web パーツ ギャラリー** ノードを追加するクラスを作成します。  新しいノードを追加するため、このクラスに <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> インターフェイスを実装します。  **\[サーバー エクスプローラ\]**の既存のノードの動作を拡張する場合に必ずノードに子ノードの追加など、このインターフェイスを実装します。  
  
#### サーバー エクスプローラーに Web パーツ ギャラリー ノードを追加するには  
  
1.  WebPartNodeExtensionプロジェクトで、SiteNodeExtensionコード ファイルを開き、そのファイルに次のコードを貼り付けます。  
  
    > [!NOTE]  
    >  このコードを追加すると、いくつかのコンパイル エラーがありますが、後の手順のコードを追加すると解消されます。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/sitenodeextension.vb#1)]  
  
## Web パーツを表すノード型の定義  
 Web パーツを表す新しいノード型を定義したクラスを作成します。  Visual Studioは、**\[Web パーツ ギャラリー\]** のノードの子ノードを表示するには、この新しいノード型を使用します。  それぞれの子ノードは、SharePointサイト上の単一のWebパーツを表します。  
  
 新しいノード型を定義するため、このクラスに <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> インターフェイスを実装します。  このインターフェイスは、**サーバー エクスプローラー**に新しい種類のノードを定義する場合に必ず実装します。  
  
#### Web パーツ ノード型を定義するには  
  
1.  WebPartNodeExtensionプロジェクトで、WebPartNodeTypeProvderコード ファイルを開き、そのファイルに次のコードを貼り付けます。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## Web パーツ データ クラスの定義  
 SharePoint サイト上の単一の Web パーツについてのデータを格納するクラスを定義します。  後の手順で、サイトの各Webパーツに関するデータを取得して、このクラスのインスタンスにデータを割り当てるカスタムSharePointコマンドを作成します。  
  
#### Web パーツ データ クラスを定義するには  
  
1.  WebPartNodeExtensionプロジェクトで、WebPartNodeInfoコード ファイルを開き、そのファイルに次のコードを貼り付けます。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodeinfo.cs#3)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodeinfo.vb#3)]  
  
## SharePoint コマンドに対する ID の定義  
 カスタム SharePoint コマンドを識別する文字列をいくつか定義します。  これらのコマンドについては、このチュートリアルの後半で実装します。  
  
#### コマンドの ID を定義するには  
  
1.  WebPartNodeExtensionプロジェクトで、WebPartCommandIdsのコード ファイルを開き、そのファイルに次のコードを貼り付けます。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartcommandids.vb#4)]  
  
## カスタム SharePoint コマンドの作成  
 SharePointサイトのWebパーツに関するデータを取得するには、SharePointのサーバー オブジェクト モデルを呼び出すカスタム コマンドを作成します。  どちらのコマンドも、<xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> が適用されたメソッドです。  
  
#### SharePoint コマンドを定義するには  
  
1.  WebPartCommandsプロジェクトでは、WebPartCommandsコード ファイルを開き、そのファイルに次のコードを貼り付けます。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartcommands/webpartcommands.vb#6)]  
  
## チェックポイント  
 この段階で、**Web パーツ ギャラリー** ノードおよび SharePoint コマンドに必要なすべてのコードがプロジェクトに揃ったことになります。  エラーが発生することなく 2 つのプロジェクトをコンパイルできるかどうか、ソリューションをビルドして確認してください。  
  
#### ソリューションをビルドするには  
  
1.  メニュー バーで、**\[ビルド\]**、**\[ソリューションのビルド\]**を選択します。  
  
    > [!WARNING]  
    >  この時点で、WebPartNodeプロジェクトは、VSIXマニフェスト ファイルに作成者の値がないため、ビルド エラーがある場合があります。  このエラーは、後の手順の値を追加すると解消されます。  
  
## 拡張機能を配置するための VSIX パッケージの作成  
 拡張機能を配置するには、ソリューションで VSIX プロジェクトを使用して VSIX パッケージを作成します。  まず、VSIXプロジェクトのsource.extension.vsixmanifestファイルを変更して、VSIXパッケージを構成します。  次に、ソリューションをビルドして VSIX パッケージを作成します。  
  
#### VSIX パッケージを構成するには  
  
1.  **\[ソリューション エクスプローラー\]**では、WebPartNodeプロジェクトの下で、を開きマニフェスト エディターでファイル **\[source.extension.vsixmanifest\]**。  
  
     source.extension.vsixmanifestファイルは、すべてのVSIXパッケージが必要とするextension.vsixmanifestファイルの基礎です。  このファイルの詳細については、「[VSIX 拡張機能のスキーマに関するリファレンス](http://msdn.microsoft.com/ja-jp/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)」を参照してください。  
  
2.  **\[製品名\]** ボックスに、**\[Web Part Gallery Node for Server Explorer\]**を入力します。  
  
3.  **\[作成者\]** ボックスに、**\[Contoso\]**を入力します。  
  
4.  **\[Description\]** ボックスで、追加**するサーバー エクスプローラーの\[SharePoint接続\]ノードにカスタムWebパーツ ギャラリー ノードを入力します。This extension uses a custom SharePoint command to call into the server object model.**」と入力します。  
  
5.  エディターの **\[資産\]** のタブをクリックし、**\[新規作成\]** のボタンをクリックします。  
  
     **\[新しい資産の追加\]** のダイアログ ボックスが表示されます。  
  
6.  **\[種類\]** の一覧で、**\[Microsoft.VisualStudio.MefComponent\]**を選択します。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MefComponent` 要素に対応します。  この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。  詳細については、「[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/ja-jp/8a813141-8b73-44c9-b80b-ca85bbac9551)」を参照してください。  
  
7.  **\[ソース\]** の一覧で、**\[現在のソリューション内のプロジェクト\]**を選択します。  
  
8.  **\[プロジェクト\]** の一覧で、**\[WebPartNodeExtension\]** を選択し、**\[OK\]** のボタンをクリックします。  
  
9. マニフェスト エディターで、**\[新規作成\]** のボタンをもう一度クリックします。  
  
     **\[新しい資産の追加\]** のダイアログ ボックスが表示されます。  
  
10. **\[種類\]** ボックスに、**\[SharePoint.Commands.v4\]**を入力します。  
  
    > [!NOTE]  
    >  Visual Studio の拡張機能に追加するカスタム拡張機能は、この要素によって指定されます。  詳細については、「[資産の要素 \(VSX スキーマ\)](http://msdn.microsoft.com/ja-jp/9fcfc098-edc7-484b-9d4c-acd17829d737)」を参照してください。  
  
11. **\[ソース\]** の一覧で、**\[現在のソリューション内のプロジェクト\]** の一覧の項目を選択します。  
  
12. **\[プロジェクト\]** の一覧で、**\[WebPartCommands\]**を選択し、**\[OK\]** のボタンをクリックします。  
  
13. メニュー バーで、**\[ビルド\]**、**\[ソリューションのビルド\]**を選択し、次に、ソリューションのエラーなしでコンパイルしてください。  
  
14. WebPartNodeプロジェクトのビルド出力フォルダーにWebPartNode.vsixファイルが含まれていることを確認します。  
  
     既定では、プロジェクト ファイルに格納されているフォルダー  の ..\\bin\\Debug フォルダーがビルド出力フォルダーです。  
  
## 拡張機能のテスト  
 **\[サーバー エクスプローラ\]**の **\[Web パーツ ギャラリー\]** の新しいノードをテストする準備ができました。  まず、Visual Studio の実験用インスタンスで拡張機能のデバッグを開始します。  次に、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の実験用インスタンスで新しい **\[Web パーツ\]** ノードを使用します。  
  
#### 拡張機能のデバッグを開始するには  
  
1.  管理資格情報を使用してを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を再起動し、WebPartNodeソリューションを開きます。  
  
2.  WebPartNodeExtensionプロジェクトで、SiteNodeExtensionコード ファイルを開き、`NodeChildrenRequested` と `CreateWebPartNodes` のメソッドのコードの先頭行にブレークポイントを追加します。  
  
3.  F5 キーを押してデバッグを開始します。  
  
     Visual Studioは、サーバーExplorer\\1.0の%UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Webのパーツ ギャラリー ノードの拡張機能に拡張機能をインストール、Visual Studioの実験用インスタンスを起動します。  このインスタンスの Visual Studio でプロジェクト項目をテストします。  
  
#### 拡張機能をテストするには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]の実験用インスタンスで、メニュー バーで、**\[表示\]**、**\[サーバー エクスプローラ\]**を選択します。  
  
2.  まず、テストに使用するSharePointサイトが **\[サーバー エクスプローラ\]**の **\[SharePoint 接続\]** のノードの下に表示されていない場合は、次の手順を実行します:  
  
    1.  **\[サーバー エクスプローラ\]**では、**\[SharePoint 接続\]**のショートカット メニューを開き、**\[接続の追加\]**を選択します。  
  
    2.  **\[SharePoint 接続の追加\]** のダイアログ ボックスで、接続先の入力し、次に **\[OK\]** のボタンを選択します。SharePointサイトのURL。  
  
         開発用コンピューター上のSharePointサイトを指定するには、**http:\/\/localhost**を入力します。  
  
3.  \(サイトのURLを表示する\) サイト接続ノードを展開し、子サイト ノード \(たとえば、**\[チーム サイト\]**\) を展開します。  
  
4.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の他のインスタンスのコードがプロジェクトのデバッグが `NodeChildrenRequested` のメソッドの前に設定、つもりでF5キーを選択したブレークポイントで停止することを確認します。  
  
5.  Visual Studioの実験用インスタンスで、**\[Web パーツ ギャラリー\]** という名前の新しいノードが最上位のサイト ノードの下にある認識し、**\[Web パーツ ギャラリー\]** のノードを展開します。  
  
6.  Visual Studioのもう一方のインスタンスで、コードがプロジェクトのデバッグが `CreateWebPartNodes` のメソッドの前に設定、つもりでF5キーを選択したブレークポイントで停止することを確認します。  
  
7.  Visual Studioの実験用インスタンスで、接続先サイトのすべてのWebパーツが **\[サーバー エクスプローラ\]**の **\[Web パーツ ギャラリー\]** ノードの下にあることを確認します。  
  
8.  **\[サーバー エクスプローラ\]**にWebパーツの1人のショートカット メニューを開き、**\[プロパティ\]**を選択します。  
  
9. デバッグ [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のインスタンスでWebパーツに関する詳細が **\[プロパティ\]** のペインに表示されることを確認します。  
  
## Visual Studio からの拡張機能のアンインストール  
 拡張機能のテストが完了したら、拡張機能を Visual Studio からアンインストールします。  
  
#### 拡張機能をアンインストールするには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]の実験用インスタンスで、メニュー バーで、**\[ツール\]**、**\[拡張機能と更新プログラム\]**を選択します。  
  
     **\[拡張機能と更新プログラム\]** のダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で、**\[Web Part Gallery Node Extension for Server Explorer\]**を選択し、**\[アンインストール\]** のボタンをクリックします。  
  
3.  表示されたダイアログ ボックスで、拡張機能をアンインストールする選択し、アンインストールを実行するに **\[今すぐ再起動\]** のボタンを選択します。ことを確認するために **\[○\]** のボタンをクリックします。  
  
4.  Visual Studioの実験用インスタンスとインスタンス \(WebPartNodeソリューションが開いている\) Visual Studioの両方のインスタンスのインスタンスを閉じます。  
  
## 参照  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  