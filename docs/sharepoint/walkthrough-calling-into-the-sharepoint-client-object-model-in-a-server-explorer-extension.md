---
title: "Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, client object model"
  - "SharePoint commands [SharePoint development in Visual Studio]"
ms.assetid: 897d3798-42c1-4fff-b280-8b84b53d80c6
caps.latest.revision: 100
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 96
---
# Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension
  このチュートリアルでは、**サーバー エクスプローラー**の **\[SharePoint 接続\]** ノードの拡張機能から SharePoint クライアント オブジェクト モデルを呼び出す方法について説明します。  SharePointクライアント オブジェクト モデルを使用する方法の詳細については、[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)を参照してください。  
  
 このチュートリアルでは、次のタスクを実行します。  
  
-   **サーバー エクスプローラー**の **\[SharePoint 接続\]** ノードを拡張する [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 拡張機能を作成する。具体的には次の点を拡張します。  
  
    -   拡張子は **\[サーバー エクスプローラ\]**の各SharePointサイト ノードに **\[Web パーツ ギャラリー\]** のノードを追加します。  この新しいノードには、サイト上の Web パーツ ギャラリー内の個々の Web パーツを表す子ノードが表示されます。  
  
    -   拡張機能では、Webパーツのインスタンスを表す新しいノード型を定義します。  新しい **Web パーツ ギャラリー** ノードの子ノードには、このノード型が使用されます。  新しいWebパーツ ノード型は、ノードが表すWebパーツに関する **\[プロパティ\]** のウィンドウに表示します。  
  
-   拡張機能を配置するための Visual Studio Extension \(VSIX\) パッケージを構築する。  
  
-   拡張機能をデバッグしてテストする。  
  
> [!NOTE]  
>  このチュートリアルで作成する拡張機能は、[Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)で作成する拡張機能に似ています。  チュートリアルでは、SharePointサーバー オブジェクト モデル、このチュートリアルを使用することが同じタスクを実行するクライアント オブジェクト モデルを使用します。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   Windows SharePoint、およびサポートされるVisual Studioのエディション。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   Visual Studio SDK。  このチュートリアルでは、拡張機能を配置するための VSIX パッケージを、SDK の **VSIX プロジェクト** テンプレートを使用して作成します。  詳細については、「[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
 次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   SharePoint クライアント オブジェクト モデルの使用。  詳細については、「[Managed Client Object Model \(マネージ クライアント オブジェクト モデル\)](http://go.microsoft.com/fwlink/?LinkId=177797)」を参照してください。  
  
-   SharePoint Webパーツ。  詳細については、「[Web Parts Overview \(Web パーツの概要\)](http://go.microsoft.com/fwlink/?LinkId=177803)」を参照してください。  
  
## プロジェクトの作成  
 このチュートリアルを完了するには、2 つのプロジェクトを作成する必要があります。  
  
-   **サーバー エクスプローラー**の拡張機能を配置するために VSIX パッケージを作成する VSIX プロジェクト。  
  
-   **サーバー エクスプローラー**の拡張機能を実装するクラス ライブラリ プロジェクト。  
  
 この 2 つのプロジェクトを作成することから始めます。  
  
#### VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで **\[ファイル\]**、**\[新規\]**、**\[プロジェクト\]** の順にクリックします。  
  
3.  **\[新しいプロジェクト\]** のダイアログ ボックスで、**\[Visual C\#\]** または **\[Visual Basic\]** のノードを展開し、**\[機能拡張\]**を選択します。  
  
    > [!NOTE]  
    >  **\[機能拡張\]** のノードは、Visual Studio SDKをインストールするときだけです。  詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
4.  ダイアログ ボックスの上部に、.NET Frameworkのバージョンの **\[.NET Framework 4.5\]** リストのを選択します。  
  
     SharePointツールの拡張機能はバージョンの.NET Frameworkの機能が必要です。  
  
5.  **\[VSIX プロジェクト\]** テンプレートを選択します。  
  
6.  **\[名前\]** ボックスに" **\[WebPartNode\]**は、を **\[OK\]** のボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の**ソリューション エクスプローラー**に **WebPartNode** プロジェクトが追加されます。  
  
#### 拡張機能プロジェクトを作成するには  
  
1.  **\[ソリューション エクスプローラー\]**で、ソリューション ノードのショートカット メニューを開き、**\[追加\]**を選択し、を **\[新しいプロジェクト\]**を選択します。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトで**ソリューション エクスプローラー**にソリューション ノードが表示されるのは、[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/ja-jp/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)の **\[常にソリューションを表示\]** チェック ボックスがオンになっている場合だけです。  
  
2.  **\[新しいプロジェクト\]** のダイアログ ボックスで、**\[Visual C\#\]** または **\[Visual Basic\]** のノードを展開し、**\[ウィンドウ\]**を選択します。  
  
3.  ダイアログ ボックスの上部に、.NET Frameworkのバージョンの **\[.NET Framework 4.5\]** リストのを選択します。  
  
4.  プロジェクト テンプレートの一覧で、**\[クラス ライブラリ\]**を選択します。  
  
5.  **\[名前\]** ボックスに、**\[WebPartNodeExtension\]**を入力し、を **\[OK\]** のボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって、**WebPartNodeExtension** プロジェクトがソリューションに追加され、既定の Class1 コード ファイルが開きます。  
  
6.  Class1 コード ファイルをプロジェクトから削除します。  
  
## 拡張機能プロジェクトの構成  
 拡張機能を作成するためのコードを記述する前に、プロジェクトのコード ファイルおよびアセンブリ参照を追加して既定の名前空間を更新する必要があります。  
  
#### プロジェクトを構成するには  
  
1.  **\[WebPartNodeExtension\]** のプロジェクトでは、SiteNodeExtension、WebPartNodeTypeProviderという2種類のコード ファイルを追加します。  
  
2.  WebPartNodeExtensionプロジェクトのショートカット メニューを開き、**\[参照の追加\]**を選択します。  
  
3.  **\[マネージャーの– WebPartNodeExtensionを参照してください。\]** のダイアログ ボックスで、**\[Framework\]** のノードを選択し、System.ComponentModel.CompositionおよびSystem.Windows.Formsの各アセンブリのチェック ボックスをオンにします。  
  
4.  **\[拡張機能\]** のノードを選択し、次のアセンブリのチェック ボックスをオンに **\[OK\]** のボタンを選択する:  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  **\[WebPartNodeExtension\]** のプロジェクトのショートカット メニューを開き、**\[プロパティ\]**を選択します。  
  
     **プロジェクト デザイナー**が開きます。  
  
6.  **\[アプリケーション\]** のタブをクリックします。  
  
7.  **\[既定の名前空間\]** ボックス \(C\#\)、または **\[ルート名前空間\]** ボックス \(Visual Basic\) に、**ServerExplorer.SharePointConnections.WebPartNode**を入力します。  
  
## 新しいノードのアイコンの作成  
 **\[サーバー エクスプローラ\]** 拡張機能の2種類のアイコンを作成します: **\[Web パーツ ギャラリー\]** の新しいノードのアイコンと **\[Web パーツ ギャラリー\]** ノードの下の各子Webパーツのノードのアイコン。  後で、これらのアイコンをノードに関連付けるコードを記述します。  
  
#### ノードのアイコンを作成するには  
  
1.  WebPartNodeExtensionプロジェクトの **\[プロジェクト デザイナー\]** では、**\[リソース\]** のタブをクリックします。  
  
2.  この **プロジェクトで既定のリソース ファイルを含まないリンクを選択します。ファイルを作成するには、ここをクリックしてください。\]** をクリックします。  
  
     Visual Studioは、リソース ファイルが開きますをデザイナーで開きます作成します。  
  
3.  デザイナーの上部で、**\[リソースの追加\]** のメニュー コマンドの矢印をクリックし、**\[新しいアイコンの追加\]**を選択します。  
  
4.  新しいアイコン名の **WebPartsNode** を入力し、を **\[追加\]** のボタンをクリックします。  
  
     **イメージ エディター**に新しいアイコンが表示されます。  
  
5.  簡単に検証しやすいデザインとなるよう16x16版のアイコン ファイルを編集します。  
  
6.  32x32版のアイコンのショートカット メニューを開き、**\[イメージ タイプの削除\]**を選択します。  
  
7.  手順3からプロジェクト リソースに2番目のアイコンを追加する7を繰り返します。このアイコン **\[Web パーツ\]**を表示します。  
  
8.  **\[WebPartNodeExtension\]** のプロジェクトの **\[リソース\]** フォルダーの **\[ソリューション エクスプローラー\]**では、**\[WebPartsNode.ico\]**を選択します。  
  
9. **\[プロパティ\]** のペインで、**\[ビルド アクション\]** のリストを開き、**\[埋め込みリソース\]**を選択します。  
  
10. **WebPart.ico** について最後の 2 つの手順を繰り返します。  
  
## サーバー エクスプローラーへの Web パーツ ギャラリー ノードの追加  
 各 SharePoint サイト ノードに新しい **Web パーツ ギャラリー** ノードを追加するクラスを作成します。  新しいノードを追加するため、このクラスに <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> インターフェイスを実装します。  **サーバー エクスプローラー**の既存のノードの動作を拡張 \(ノードに新しい子ノードを追加するなど\) する場合は必ず、このインターフェイスを実装します。  
  
#### サーバー エクスプローラーに Web パーツ ギャラリー ノードを追加するには  
  
1.  **\[WebPartNodeExtension\]** のプロジェクトの **\[SiteNodeExtension\]** コード ファイルに次のコードを貼り付けます。  
  
    > [!NOTE]  
    >  このコードを追加すると、いくつかのコンパイル エラーがあります。  これらのエラーは、この後の手順でコードを追加すると解消されます。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/cs/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/vb/webpartnodeextension/sitenodeextension.vb#1)]  
  
## Web パーツを表すノード型の定義  
 Web パーツを表す新しいノード型を定義したクラスを作成します。  Visual Studioは、**\[Web パーツ ギャラリー\]** のノードの子ノードを表示するには、この新しいノード型を使用します。  それぞれの子ノードは、SharePoint サイト上の単一の Web パーツを表します。  
  
 新しいノード型を定義するため、このクラスに <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> インターフェイスを実装します。  このインターフェイスは、**サーバー エクスプローラー**に新しい種類のノードを定義する場合に必ず実装します。  
  
#### Web パーツ ノード型を定義するには  
  
1.  **\[WebPartNodeExtension\]** のプロジェクトの **\[WebPartNodeTypeProvider\]** コード ファイルに次のコードを貼り付けます。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/cs/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/vb/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## チェックポイント  
 この段階で、**Web パーツ ギャラリー** ノードに必要なすべてのコードがプロジェクトに揃ったことになります。  コンパイル エラーが発生しないことを確認 **\[WebPartNodeExtension\]** プロジェクトをビルドします。  
  
#### プロジェクトをビルドするには  
  
1.  **\[ソリューション エクスプローラー\]**では、**\[WebPartNodeExtension\]** のプロジェクトのショートカット メニューを開き、**\[ビルド\]**を選択します。  
  
## 拡張機能を配置するための VSIX パッケージの作成  
 拡張機能を配置するには、ソリューションで VSIX プロジェクトを使用して VSIX パッケージを作成します。  まず、プロジェクトに含まれているsource.extension.vsixmanifestファイルを変更して、VSIXパッケージを構成します。  ソリューションをビルドしてVSIXパッケージを作成します。  
  
#### VSIX パッケージを構成するには  
  
1.  **\[ソリューション エクスプローラー\]**では、**\[WebPartNode\]** のプロジェクトで、**\[source.extension.vsixmanifest\]** マニフェスト エディターでファイルを開きます。  
  
     source.extension.vsixmanifestファイルは、すべてのVSIXパッケージが必要とするextension.vsixmanifestファイルの基礎です。  このファイルの詳細については、「[VSIX 拡張機能のスキーマに関するリファレンス](http://msdn.microsoft.com/ja-jp/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)」を参照してください。  
  
2.  **\[製品名\]** ボックスに、**\[Web Part Gallery Node for Server Explorer\]**を入力します。  
  
3.  **\[作成者\]** ボックスに、**\[Contoso\]**を入力します。  
  
4.  **\[説明\]** ボックスに、**サーバー エクスプローラーの \[SharePoint接続\] ノードにカスタムWebパーツ ギャラリー ノードを追加します**を入力します。  
  
5.  エディターの **\[資産\]** のタブで、**\[新規作成\]** のボタンをクリックします。  
  
6.  **\[新しい資産の追加\]** のダイアログ ボックスで、**\[種類\]** の一覧で、**\[Microsoft.VisualStudio.MefComponent\]**を選択します。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MefComponent` 要素に対応します。  この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。  詳細については、「[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/ja-jp/8a813141-8b73-44c9-b80b-ca85bbac9551)」を参照してください。  
  
7.  **\[ソース\]** の一覧で、**\[現在のソリューション内のプロジェクト\]**を選択します。  
  
8.  **\[プロジェクト\]** の一覧で、**\[WebPartNodeExtension\]**を選択し、**\[OK\]** のボタンをクリックします。  
  
9. メニュー バーで、**\[ビルド\]**、**\[ソリューションのビルド\]**を選択し、次に、ソリューションのエラーなしでコンパイルしてください。  
  
10. WebPartNodeプロジェクトのビルド出力フォルダーにWebPartNode.vsixファイルが含まれていることを確認します。  
  
     既定では、プロジェクト ファイルに格納されているフォルダー  の ..\\bin\\Debug フォルダーがビルド出力フォルダーです。  
  
## 拡張機能のテスト  
 これで、**サーバー エクスプローラー**の新しい **Web パーツ ギャラリー** ノードをテストする準備ができました。  まず、Visual Studioの実験用インスタンスで拡張機能プロジェクトをデバッグを開始します。  次に、Visual Studioの実験用インスタンスで **\[Web パーツ\]** の新しいノードを使用します。  
  
#### 拡張機能のデバッグを開始するには  
  
1.  管理資格情報を使用してVisual Studioを再起動し、**\[WebPartNode\]** ソリューションを開きます。  
  
2.  WebPartNodeExtensionプロジェクトで、**\[SiteNodeExtension\]** コード ファイルを開き、`NodeChildrenRequested` と `CreateWebPartNodes` のメソッドのコードの先頭行にブレークポイントを追加します。  
  
3.  F5 キーを押してデバッグを開始します。  
  
     Visual Studioは、サーバーExplorer\\1.0の%UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Webのパーツ ギャラリー ノードの拡張機能に拡張機能をインストール、Visual Studioの実験用インスタンスを起動します。  Visual Studioでプロジェクト項目をテストします。この場合  
  
#### 拡張機能をテストするには  
  
1.  Visual Studioの実験用インスタンスで、メニュー バーで、**\[表示\]**、**\[サーバー エクスプローラ\]**を選択します。  
  
2.  テストに使用する SharePoint サイトが、**サーバー エクスプローラー**の **\[SharePoint 接続\]** ノードに表示されていることを確認します。  これが表示されない場合は、次の手順を実行する:  
  
    1.  **\[SharePoint 接続\]**のショートカット メニューを開き、**\[接続の追加\]**を選択します。  
  
    2.  **\[SharePoint 接続の追加\]** のダイアログ ボックスで、接続先の入力し、次に **\[OK\]** のボタンを選択します。SharePointサイトのURL。  
  
         開発コンピューター上の SharePoint サイトを指定するには、「**http:\/\/localhost**」と入力します。  
  
3.  \(サイトのURLを表示する\) サイト接続ノードを展開し、子サイト ノード \(たとえば、**\[チーム サイト\]**\) を展開します。  
  
4.  Visual Studioのもう一方のインスタンスで、コードがプロジェクトのデバッグが `NodeChildrenRequested` のメソッドの前に設定、つもりでF5キーを選択したブレークポイントで停止することを確認します。  
  
5.  Visual Studioの実験用インスタンスで、最上位のサイト ノードの下にある **\[Web パーツ ギャラリー\]** のノードを展開します。  
  
6.  Visual Studioのもう一方のインスタンスで、コードがプロジェクトのデバッグが `CreateWebPartNodes` のメソッドの前に設定、つもりでF5キーを選択したブレークポイントで停止することを確認します。  
  
7.  Visual Studio の実験用インスタンスで、**サーバー エクスプローラー**の **\[Web パーツ ギャラリー\]** ノードに、接続先サイトのすべての Web パーツが表示されていることを確認します。  
  
8.  Webパーツのショートカット メニューを開き、**\[プロパティ\]**を選択します。  
  
9. **\[プロパティ\]** ペインで、Webパーツに関する詳細が表示されることを確認します。  
  
10. **\[サーバー エクスプローラ\]**で、同じWebパーツのショートカット メニューを開き、**\[メッセージを表示する\]**を選択します。  
  
     表示されたメッセージ ボックスで、**\[OK\]** のボタンをクリックします。  
  
## Visual Studio からの拡張機能のアンインストール  
 拡張機能のテストが完了したら、Visual Studioからそれをアンインストールします。  
  
#### 拡張機能をアンインストールするには  
  
1.  Visual Studioの実験用インスタンスで、メニュー バーで、**\[ツール\]**、**\[拡張機能と更新プログラム\]**を選択します。  
  
     **\[拡張機能と更新プログラム\]** のダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で、**\[Web Part Gallery Node for Server Explorer\]**を選択し、**\[アンインストール\]** のボタンをクリックします。  
  
3.  表示されたダイアログ ボックスで、**\[○\]** のボタンをクリックします。  
  
4.  アンインストールを実行するに **\[今すぐ再起動\]** のボタンをクリックします。  
  
     プロジェクト項目もアンインストールされます。  
  
5.  Visual Studioの実験用インスタンスとインスタンス \(WebPartNodeソリューションが開いている\) Visual Studioの両方のインスタンスのインスタンスを閉じます。  
  
## 参照  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  