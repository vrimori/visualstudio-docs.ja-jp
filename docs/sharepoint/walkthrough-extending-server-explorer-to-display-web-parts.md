---
title: 'チュートリアル: サーバー エクスプ ローラー Web パーツ表示するための拡張 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 34975f93b719c759707110907a3c19dabbd661c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-extending-server-explorer-to-display-web-parts"></a>チュートリアル: サーバー エクスプローラーを拡張して Web パーツを表示する
  Visual Studio で、使用することができます、 **SharePoint 接続**のノード**サーバー エクスプ ローラー**を SharePoint サイト上のコンポーネントを表示します。 ただし、**サーバー エクスプ ローラー**既定では一部のコンポーネントが表示されません。 このチュートリアルで拡張する**サーバー エクスプ ローラー** SharePoint サイトが接続されている各 Web パーツ ギャラリーで表示するようです。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   Visual Studio 拡張機能の作成を拡張**サーバー エクスプ ローラー**次のようにします。  
  
    -   拡張機能を追加、 **Web パーツ ギャラリー**ノードの下にある各 SharePoint サイト**サーバー エクスプ ローラー**です。 この新しいノードには、サイトの Web パーツ ギャラリーでは、各 Web パーツを表す子ノードが含まれています。  
  
    -   拡張機能では、Web パーツ インスタンスを表すノードの新しい型を定義します。 このノード型で、新しい子ノードの基礎となる**Web パーツ ギャラリー**ノード。 新しい Web パーツのノードの種類の情報が表示されます、**プロパティ**それが表す Web パーツのウィンドウ。 ノードの種類には、Web パーツに関連するその他のタスクを実行するための出発点として使用できるカスタムのショートカット メニュー項目も含まれています。  
  
-   2 つのカスタム SharePoint コマンドを作成する、拡張機能アセンブリの呼び出しです。 SharePoint コマンドは、SharePoint のサーバー オブジェクト モデルで Api を使用する拡張機能アセンブリを呼び出すことができるメソッドです。 このチュートリアルでは、開発用コンピューター上のローカルの SharePoint サイトから Web パーツの情報を取得するコマンドを作成します。 詳細については、次を参照してください。[の SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)です。  
  
-   拡張機能を配置する Visual Studio Extension (VSIX) パッケージを作成します。  
  
-   デバッグと、拡張機能をテストします。  
  
> [!NOTE]  
>  For SharePoint クライアント オブジェクト モデルを使用してそのサーバー オブジェクト モデルではなくこのチュートリアルの別のバージョンを参照してください。[チュートリアル: サーバー エクスプ ローラー拡張機能では、SharePoint クライアント オブジェクト モデルを呼び出す](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   Windows、SharePoint、および Visual Studio のエディションをサポートします。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   Visual Studio SDK。 このチュートリアルでは、 **VSIX プロジェクト**sdk をプロジェクト項目を配置するための VSIX パッケージを作成するテンプレートです。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツール拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)です。  
  
 次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   For SharePoint サーバー オブジェクト モデルを使用します。 詳細については、次を参照してください。 [SharePoint Foundation サーバー側オブジェクト モデルを使用して](http://go.microsoft.com/fwlink/?LinkId=177796)です。  
  
-   SharePoint ソリューションの web パーツ。 詳細については、次を参照してください。 [Web パーツの概要](http://go.microsoft.com/fwlink/?LinkId=177803)です。  
  
## <a name="creating-the-projects"></a>プロジェクトの作成  
 このチュートリアルを完了するには、3 つのプロジェクトを作成する必要があります。  
  
-   拡張機能を配置するための VSIX パッケージを作成する VSIX プロジェクト。  
  
-   拡張機能を実装するクラス ライブラリ プロジェクト。 このプロジェクトは、.NET Framework 4.5 を対象する必要があります。  
  
-   カスタムの SharePoint コマンドを定義するクラス ライブラリ プロジェクト。 このプロジェクトは .NET Framework 3.5 を対象にする必要があります。  
  
 この 2 つのプロジェクトを作成することから始めます。  
  
#### <a name="to-create-the-vsix-project"></a>VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#**または**Visual Basic** 、ノードを選択し、 **Extensibility**ノード。  
  
    > [!NOTE]  
    >  **Extensibility**ノードは、Visual Studio SDK をインストールする場合にのみ使用できます。 詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
4.  ダイアログ ボックスの上部には、次のように選択します。 **.NET Framework 4.5** 、.NET Framework のバージョンの一覧にします。  
  
5.  選択、 **VSIX プロジェクト**名では、プロジェクト テンプレートは、 **WebPartNode**を選択し、 **OK**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **WebPartNode**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
#### <a name="to-create-the-extension-project"></a>拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**でソリューション ノードのショートカット メニューを開き、**追加**を選択し**新しいプロジェクト**です。  
  
2.  **新しいプロジェクト**] ダイアログ ボックスで、展開、 **Visual c#**ノードまたは**Visual Basic**ノードを展開し、[ **Windows**ノード。  
  
3.  ダイアログ ボックスの上部には、次のように選択します。 **.NET Framework 4.5** 、.NET Framework のバージョンの一覧にします。  
  
4.  プロジェクト テンプレートの一覧で選択**クラス ライブラリ**、プロジェクトに名前を**WebPartNodeExtension**を選択し、 **OK**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **WebPartNodeExtension**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>SharePoint コマンド プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**でソリューション ノードのショートカット メニューを開き、**追加**を選択し**新しいプロジェクト**です。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#**ノードまたは**Visual Basic**  ノードを選択し、 **Windows**ノード。  
  
3.  ダイアログ ボックスの上部には、次のように選択します。 **.NET Framework 3.5** 、.NET Framework のバージョンの一覧にします。  
  
4.  
  
5.  プロジェクト テンプレートの一覧で選択**クラス ライブラリ**、プロジェクトに名前を**WebPartCommands**を選択し、 **OK**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **WebPartCommands**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。  
  
6.  Class1 コード ファイルをプロジェクトから削除します。  
  
## <a name="configuring-the-projects"></a>プロジェクトの構成  
 拡張機能を作成するコードを記述する前に、コード ファイルおよびアセンブリ参照を追加し、プロジェクト設定を構成する必要があります。  
  
#### <a name="to-configure-the-webpartnodeextension-project"></a>WebPartNodeExtension プロジェクトを構成するには  
  
1.  WebPartNodeExtension プロジェクトでは、次の名前を持つ 4 つのコード ファイルを追加します。  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  ショートカット メニューを開き、 **WebPartNodeExtension**プロジェクトをクリックして**参照の追加**です。  
  
3.  **参照マネージャー - WebPartNodeExtension**  ダイアログ ボックスで、選択、 **Framework**タブをクリックし、次のアセンブリの各チェック ボックスを選択。  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  選択、**拡張機能**] タブ、Microsoft.VisualStudio.SharePoint アセンブリのチェック ボックスを選択し、[、 **OK**ボタンをクリックします。  
  
5.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **WebPartNodeExtension**プロジェクト ノードをクリックして**プロパティ**です。  
  
     **プロジェクト デザイナー**が開きます。  
  
6.  **[アプリケーション]** タブを選択します。  
  
7.  **既定の名前空間**ボックス (c#) または**ルート名前空間**ボックス ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)])、入力**ServerExplorer.SharePointConnections.WebPartNode**です。  
  
#### <a name="to-configure-the-webpartcommands-project"></a>WebPartCommands プロジェクトを構成するには  
  
1.  プロジェクトで、WebPartCommands WebPartCommands というコード ファイルを追加します。  
  
2.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **WebPartCommands**プロジェクト ノードを選択して**追加**を選択し**既存項目の**.  
  
3.  **既存項目の追加** ダイアログ ボックスが WebPartNodeExtension プロジェクトのコード ファイルを含むフォルダーを参照し、WebPartNodeInfo と WebPartCommandIds コード ファイルを選択します。  
  
4.  横の矢印を選択、**追加**ボタンをクリックし、**リンクとして追加**表示されるメニュー。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] WebPartCommands プロジェクトへのリンクとしてコード ファイルを追加します。 この結果、WebPartNodeExtension プロジェクト内のコード ファイルにあるが、ファイル内のコードは WebPartCommands プロジェクトでもコンパイルします。  
  
5.  ショートカット メニューを開き、 **WebPartCommands**プロジェクトをもう一度、**参照の追加**です。  
  
6.  **参照マネージャー - WebPartCommands**  ダイアログ ボックスで、選択、**拡張** タブ、次のアセンブリの各チェック ボックスを選択し、、 **OK**ボタンをクリックします。  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **WebPartCommands**クリックして、もう一度、プロジェクト**プロパティ**です。  
  
     **プロジェクト デザイナー**が開きます。  
  
8.  **[アプリケーション]** タブを選択します。  
  
9. **既定の名前空間**ボックス (c#) または**ルート名前空間**ボックス ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)])、入力**ServerExplorer.SharePointConnections.WebPartNode**です。  
  
## <a name="creating-icons-for-the-new-nodes"></a>新しいノードのアイコンの作成  
 2 つのアイコンを作成、**サーバー エクスプ ローラー**拡張機能: 新しいアイコン**Web パーツ ギャラリー**ノード、および各子 Web パーツのノードの下の別のアイコン、 **Web パーツ ギャラリー**ノードです。 このチュートリアルの後半では、ノードにこれらのアイコンを関連付けるコードを記述します。  
  
#### <a name="to-create-icons-for-the-nodes"></a>ノードのアイコンを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **WebPartNodeExtension**プロジェクトをクリックして**プロパティ**です。  
  
2.  **プロジェクト デザイナー**が開きます。  
  
3.  選択、**リソース** タブをクリックして、**このプロジェクトに既定のリソース ファイルが含まれていません。作成するのにはここをクリックして**リンクします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] リソース ファイルを作成し、デザイナーで開かれます。  
  
4.  デザイナーの上部にあるに横に矢印をクリックして、**リソースの追加**メニュー コマンドを使用し、**新しいアイコンの追加**表示されるメニュー。  
  
5.  **新しいリソースの追加** ダイアログ ボックスに、名前、新規アイコン**WebPartsNode**を選択し、**追加**ボタンをクリックします。  
  
     新しいアイコンが表示されます、**イメージ エディター**です。  
  
6.  16 x 16 版のアイコンを編集して、デザイン簡単に識別できるようにします。  
  
7.  アイコンのサイズは 32 x 32 のバージョンについては、ショートカット メニューを開き、選択**イメージ タイプの削除**です。  
  
8.  手順 5. ~ 8. をプロジェクトのリソースに 2 番目のアイコンを追加して、このアイコンの名前を付けます**WebPart**です。  
  
9. **ソリューション エクスプ ローラー**下で、**リソース**用のフォルダー、 **WebPartNodeExtension**プロジェクトで、ショートカット メニューを開き、 **WebPartsNode.ico**.  
  
10. **プロパティ**ウィンドウで、横の矢印を選択**ビルド アクション**を選択し**埋め込まれたリソース**表示されるメニュー。  
  
11. 最後の 2 つの手順を繰り返します**WebPart.ico**です。  
  
## <a name="adding-the-web-part-gallery-node-to-server-explorer"></a>サーバー エクスプ ローラー Web パーツ ギャラリー ノードを追加します。  
 新しいを追加するクラスを作成**Web パーツ ギャラリー** SharePoint サイトの各ノードにノードです。 クラスを実装して、新しいノードを追加する、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>インターフェイスです。 既存のノードでの動作を拡張するには必ず、このインターフェイスを実装して**サーバー エクスプ ローラー**ノードに子ノードを追加するなどです。  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>サーバー エクスプ ローラー Web パーツ ギャラリーのノードを追加するには  
  
1.  WebPartNodeExtension プロジェクトで SiteNodeExtension コード ファイルを開くし、に、次のコードを貼り付けます。  
  
    > [!NOTE]  
    >  このコードを追加する、プロジェクトは、一部のコンパイル エラーが解消されます後に追加するとコード後の手順で。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="defining-a-node-type-that-represents-a-web-part"></a>Web パーツを表すノードの種類の定義  
 Web パーツを表すノードの新しい型を定義するクラスを作成します。 Visual Studio で子ノードを表示するこの新しいノード型を使用して、 **Web パーツ ギャラリー**ノード。 それぞれの子ノードでは、SharePoint サイトで単一の Web パーツを表します。  
  
 新しいノードの種類をクラスを実装を定義する、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>インターフェイスです。 内のノードの新しい型を定義するには必ず、このインターフェイスを実装して**サーバー エクスプ ローラー**です。  
  
#### <a name="to-define-the-web-part-node-type"></a>Web パーツのノード型を定義するには  
  
1.  WebPartNodeExtension プロジェクトで WebPartNodeTypeProvder コード ファイルを開くし、に、次のコードを貼り付けます。  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]  
  
## <a name="defining-the-web-part-data-class"></a>Web パーツのデータ クラスを定義します。  
 SharePoint サイトで単一の Web パーツに関するデータを格納するクラスを定義します。 このチュートリアルの後半では、サイト上の各 Web パーツに関するデータを取得し、このクラスのインスタンスにデータを割り当てますカスタム SharePoint コマンドを作成します。  
  
#### <a name="to-define-the-web-part-data-class"></a>Web パーツ データ クラスを定義するには  
  
1.  WebPartNodeExtension プロジェクトで WebPartNodeInfo コード ファイルを開くし、に、次のコードを貼り付けます。  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]  
  
## <a name="defining-the-ids-for-the-sharepoint-command"></a>SharePoint コマンドの Id を定義します。  
 カスタムの SharePoint コマンドを識別するいくつかの文字列を定義します。 このチュートリアルの後半では、これらのコマンドを実装します。  
  
#### <a name="to-define-the-command-ids"></a>コマンド Id を定義するには  
  
1.  WebPartNodeExtension プロジェクトで WebPartCommandIds コード ファイルを開くし、に、次のコードを貼り付けます。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]  
  
## <a name="creating-the-custom-sharepoint-commands"></a>カスタム SharePoint コマンドの作成  
 SharePoint サイト上の Web パーツに関するデータを取得するように SharePoint のサーバー オブジェクト モデルを呼び出すカスタム コマンドを作成します。 各コマンドはメソッドを持つ、<xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute>を適用します。  
  
#### <a name="to-define-the-sharepoint-commands"></a>SharePoint コマンドを定義するには  
  
1.  WebPartCommands プロジェクトで WebPartCommands コード ファイルを開くし、に、次のコードを貼り付けます。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]  
  
## <a name="checkpoint"></a>チェックポイント  
 この時点で、チュートリアルでは、すべてのコードで、 **Web パーツ ギャラリー**のプロジェクトでノードと SharePoint コマンドは現在します。 ソリューションをビルドして両方のプロジェクトがコンパイル エラーが発生しないことを確認してください。  
  
#### <a name="to-build-the-solution"></a>ソリューションをビルドするには  
  
1.  メニュー バーの **[ビルド]**、 **[ソリューションのビルド]**の順にクリックします。  
  
    > [!WARNING]  
    >  この時点で、VSIX マニフェスト ファイルでは、作成者の値がなかったために、WebPartNode プロジェクトは、ビルド エラーがあります。 このエラーは解消後の手順で値を追加する場合。  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>拡張機能を配置する VSIX パッケージの作成  
 拡張機能を配置するには、ソリューションで VSIX プロジェクトを使用して VSIX パッケージを作成します。 まず、VSIX プロジェクトの source.extension.vsixmanifest ファイルを変更することで、VSIX パッケージを構成します。 次に、ソリューションをビルドして VSIX パッケージを作成します。  
  
#### <a name="to-configure-the-vsix-package"></a>VSIX パッケージを構成するには  
  
1.  **ソリューション エクスプ ローラー**、WebPartNode プロジェクトを開く、 **source.extension.vsixmanifest**マニフェスト エディターでファイル。  
  
     source.extension.vsixmanifest ファイルが、すべての VSIX パッケージで必要になる extension.vsixmanifest ファイルの基礎となります。 このファイルの詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)です。  
  
2.  **Product Name**ボックスに、入力**用サーバー エクスプ ローラー Web パーツのギャラリー ノード**です。  
  
3.  **作成者**ボックスに、入力**Contoso**です。  
  
4.  **説明**ボックスに、入力**サーバー エクスプ ローラーで、[SharePoint 接続] ノードにカスタム Web パーツ ギャラリー ノードを追加します。この拡張機能では、カスタムの SharePoint コマンドを使用して、サーバー オブジェクト モデルを呼び出します。**  
  
5.  選択、**資産**エディターのタブを選択し、**新規**ボタンをクリックします。  
  
     **新しいアセットの追加** ダイアログ ボックスが表示されます。  
  
6.  **型**一覧で、選択**Microsoft.VisualStudio.MefComponent**です。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MefComponent` 要素に対応します。 この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。 詳細については、次を参照してください。 [MEFComponent 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)です。  
  
7.  **ソース**一覧で、選択**現在のソリューション内のプロジェクト**です。  
  
8.  **プロジェクト**一覧で、選択**WebPartNodeExtension**を選択し、 **OK**ボタンをクリックします。  
  
9. マニフェスト エディターで、選択、**新規**を再度クリックします。  
  
     **新しいアセットの追加** ダイアログ ボックスが表示されます。  
  
10. **型**ボックスに、入力**SharePoint.Commands.v4**です。  
  
    > [!NOTE]  
    >  この要素は、Visual Studio 拡張機能に追加するカスタム拡張機能を指定します。 詳細については、次を参照してください。[資産要素 (VSX Schema)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737)です。  
  
11. **ソース**一覧で、選択、**現在のソリューション内のプロジェクト**リスト項目。  
  
12. **プロジェクト**一覧で、選択**WebPartCommands**を選択し、 **OK**ボタンをクリックします。  
  
13. メニュー バーで、次のように選択します。**ビルド**、**ソリューションのビルド**、し、ソリューションがコンパイル エラーが発生しないことを確認します。  
  
14. WebPartNode プロジェクトのビルド出力フォルダーに今すぐ WebPartNode.vsix ファイルが含まれていることを確認してください。  
  
     既定では、ビルド出力フォルダーは ..\bin\Debug で、プロジェクト ファイルが格納されているフォルダーの下にあります。  
  
## <a name="testing-the-extension"></a>拡張機能のテスト  
 新しいテストする準備ができました**Web パーツ ギャラリー**内のノード**サーバー エクスプ ローラー**です。 まず、Visual Studio の実験用インスタンスで拡張機能のデバッグを開始します。 次に、新しい使用**Web パーツ**の実験用インスタンスでノード[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
#### <a name="to-start-debugging-the-extension"></a>拡張機能のデバッグを開始するには  
  
1.  再起動[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]管理者の資格情報と WebPartNode ソリューションを開きます。  
  
2.  WebPartNodeExtension プロジェクトで SiteNodeExtension コード ファイルを開くし、コードの最初の行にブレークポイントを追加、`NodeChildrenRequested`と`CreateWebPartNodes`メソッドです。  
  
3.  F5 キーを押してデバッグを開始します。  
  
     Visual Studio では、サーバー Explorer\1.0 用 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web パーツ ギャラリーのノードの拡張機能を拡張機能をインストールし、Visual Studio の実験用インスタンスを開始します。 このインスタンスの Visual Studio でプロジェクト項目をテストします。  
  
#### <a name="to-test-the-extension"></a>拡張機能をテストするには  
  
1.  実験用インスタンスで[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、メニュー バーで、次のように選択します。**ビュー**、**サーバー エクスプ ローラー**です。  
  
2.  テスト用に使用する SharePoint サイトが表示されない場合は、次の手順を実行、 **SharePoint 接続**内のノード**サーバー エクスプ ローラー**:  
  
    1.  **サーバー エクスプ ローラー**、ショートカット メニューを開き、 **SharePoint 接続**を選択し**接続の追加**です。  
  
    2.  **[SharePoint 接続の追加**] ダイアログ ボックスで、接続し、順に選択する SharePoint サイトの URL を入力、 **OK**ボタンをクリックします。  
  
         開発用コンピューター上には、SharePoint サイトを指定するには、入力 **http://localhost**です。  
  
3.  サイト接続ノード (サイトの URL が表示されます) を展開し、サイトの子ノードを展開 (たとえば、**チーム サイト**)。  
  
4.  いることを確認の他のインスタンス内のコード[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]前に設定したブレークポイントで停止、`NodeChildrenRequested`メソッド、し、f5 キーを押して、プロジェクトのデバッグを続行するとします。  
  
5.  Visual Studio の実験用インスタンスの新しいノードがという名前のことを確認します**Web パーツ ギャラリー**最上位のサイト ノード下に表示し、展開、 **Web パーツ ギャラリー**ノード。  
  
6.  Visual Studio の他のインスタンス内のコードが以前に設定したブレークポイントで停止することを確認、`CreateWebPartNodes`メソッド、F5 キーをプロジェクトのデバッグを続行するとします。  
  
7.  Visual Studio の実験用インスタンスの接続サイト上のすべての Web パーツが表示されることを確認してください、 **Web パーツ ギャラリー**内のノード**サーバー エクスプ ローラー**です。  
  
8.  **サーバー エクスプ ローラー**Web パーツの 1 つのショートカット メニューを開き、クリックして**プロパティ**です。  
  
9. インスタンスで[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、デバッグしているに Web パーツの詳細が表示されることを確認してください、**プロパティ**ウィンドウです。  
  
## <a name="uninstalling-the-extension-from-visual-studio"></a>Visual Studio から拡張機能のアンインストール  
 拡張機能のテストが完了したら、Visual Studio から、拡張機能をアンインストールします。  
  
#### <a name="to-uninstall-the-extension"></a>拡張機能をアンインストールするには  
  
1.  実験用インスタンスで[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、メニュー バーで、次のように選択します。**ツール**、**拡張機能と更新プログラム**です。  
  
     **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で選択**サーバー エクスプ ローラー用の Web パーツ ギャラリー ノード拡張**を選択し、**アンインストール**ボタンをクリックします。  
  
3.  ダイアログ ボックスが表示されますが、選択、 **[はい]** 、拡張機能をアンインストールし、選択することを確認するにはボタン、**今すぐ再起動**ボタンをクリックしてアンインストールを完了します。  
  
4.  Visual Studio (実験用インスタンスおよび WebPartNode ソリューションが開いている Visual Studio のインスタンス) の両方のインスタンスを閉じます。  
  
## <a name="see-also"></a>関連項目  
 [サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張します。](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [チュートリアル: サーバー エクスプ ローラー拡張機能に SharePoint クライアント オブジェクト モデルを呼び出す](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [アイコン用イメージ エディター](/cpp/windows/image-editor-for-icons)   
 [アイコンまたはその他のイメージの作成&#40;アイコン用イメージ エディター&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  