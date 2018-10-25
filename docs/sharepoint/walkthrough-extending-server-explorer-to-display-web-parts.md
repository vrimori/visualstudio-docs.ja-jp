---
title: 'チュートリアル: Web パーツを表示するサーバー エクスプ ローラーの拡張 |Microsoft Docs'
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
ms.openlocfilehash: dc6b015058445ddf35e5d247847a40d01e691047
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915816"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>チュートリアル: web パーツを表示するサーバー エクスプ ローラーの拡張します。
  Visual Studio で使用することができます、 **SharePoint 接続**のノード**サーバー エクスプ ローラー** SharePoint サイトにコンポーネントを表示します。 ただし、**サーバー エクスプ ローラー**一部のコンポーネントが既定では表示されません。 このチュートリアルで拡張します**サーバー エクスプ ローラー** SharePoint サイトが接続されている各 Web パーツ ギャラリーで表示するようです。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   拡張する Visual Studio 拡張機能を作成する**サーバー エクスプ ローラー**次のようにします。  
  
    -   拡張機能の追加、 **Web パーツ ギャラリー**内の各 SharePoint サイト ノード下にノード**サーバー エクスプ ローラー**します。 この新しいノードには、サイトの Web パーツ ギャラリーでは、各 Web パーツを表す子ノードが含まれています。  
  
    -   拡張機能は、新しい種類の Web パーツ インスタンスを表すノードを定義します。 この新しいノードの種類は、新しい子ノードの基礎**Web パーツ ギャラリー**ノード。 新しい Web パーツのノードの種類の情報が表示されます、**プロパティ**それが表す Web パーツのウィンドウ。 ノードの種類には、Web パーツに関連するその他のタスクを実行するための開始点として使用できるカスタムのショートカット メニュー項目も含まれています。  
  
-   拡張機能のアセンブリを呼び出す 2 つのカスタム SharePoint コマンドを作成します。 SharePoint コマンドは、SharePoint のサーバー オブジェクト モデルでの Api を使用する拡張機能アセンブリを呼び出すことができる方法です。 このチュートリアルでは、開発用コンピューター上のローカルの SharePoint サイトから Web パーツの情報を取得するコマンドを作成します。 詳細については、次を参照してください。[の SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)します。  
  
-   拡張機能をデプロイする Visual Studio Extension (VSIX) パッケージを作成します。  
  
-   デバッグと、拡張機能をテストします。  
  
> [!NOTE]  
>  For SharePoint サーバー オブジェクト モデルではなく、クライアント オブジェクト モデルを使用するこのチュートリアルの代替バージョンを参照してください。[チュートリアル: サーバー エクスプ ローラー拡張機能では、SharePoint クライアント オブジェクト モデルを呼び出す](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
- Windows、SharePoint、Visual Studio のエディションがサポートされています。  
  
- Visual Studio SDK。 このチュートリアルでは、 **VSIX プロジェクト**sdk プロジェクト アイテムを配置するための VSIX パッケージを作成するテンプレート。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールを拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)します。  
  
  次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
- For SharePoint サーバー オブジェクト モデルを使用します。 詳細については、次を参照してください。 [SharePoint Foundation サーバー側オブジェクト モデルを使用して](http://go.microsoft.com/fwlink/?LinkId=177796)します。  
  
- SharePoint ソリューションの web パーツ。 詳細については、次を参照してください。 [Web パーツの概要](http://go.microsoft.com/fwlink/?LinkId=177803)します。  
  
## <a name="create-the-projects"></a>プロジェクトを作成します。
 このチュートリアルを完了するには、3 つのプロジェクトを作成する必要があります。  
  
- 拡張機能をデプロイする VSIX パッケージを作成する VSIX プロジェクト。  
  
- 拡張機能を実装するクラス ライブラリ プロジェクト。 このプロジェクトは、.NET Framework 4.5 をターゲットする必要があります。  
  
- カスタムの SharePoint コマンドを定義するクラス ライブラリ プロジェクト。 このプロジェクトは .NET Framework 3.5 を対象にする必要があります。  
  
  この 2 つのプロジェクトを作成することから始めます。  
  
#### <a name="to-create-the-vsix-project"></a>VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで、**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#** または**Visual Basic**ノードを選択し、**機能拡張**ノード。  
  
    > [!NOTE]  
    >  **Extensibility**ノードは、Visual Studio SDK をインストールする場合にのみ使用できます。 詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
4.  ダイアログ ボックスの上部にある次のように選択します。 **.NET Framework 4.5**で .NET Framework のバージョンの一覧。  
  
5.  選択、 **VSIX プロジェクト**名では、プロジェクト テンプレートは、 **WebPartNode**、選択し、 **OK**ボタン。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **WebPartNode**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
#### <a name="to-create-the-extension-project"></a>拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ソリューション ノードのショートカット メニューを開き、**追加**を選び、**新しいプロジェクト**します。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#** ノードまたは**Visual Basic**ノードと選択**Windows**ノード。  
  
3.  ダイアログ ボックスの上部にある次のように選択します。 **.NET Framework 4.5**で .NET Framework のバージョンの一覧。  
  
4.  プロジェクト テンプレートの一覧で選択**クラス ライブラリ**、プロジェクトに名前を**WebPartNodeExtension**、選択し、 **OK**ボタン。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **WebPartNodeExtension**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>SharePoint コマンド プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ソリューション ノードのショートカット メニューを開き、**追加**を選び、**新しいプロジェクト**します。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#** ノードまたは**Visual Basic**ノードを選択し、 **Windows**ノード。  
  
3.  ダイアログ ボックスの上部にある次のように選択します。 **.NET Framework 3.5**で .NET Framework のバージョンの一覧。  
  
4.  プロジェクト テンプレートの一覧で選択**クラス ライブラリ**、プロジェクトに名前を**WebPartCommands**、選択し、 **OK**ボタン。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **WebPartCommands**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
## <a name="configure-the-projects"></a>プロジェクトを構成します。
 拡張機能を作成するコードを記述する前に、コード ファイルおよびアセンブリ参照を追加およびプロジェクトの設定を構成する必要があります。  
  
#### <a name="to-configure-the-webpartnodeextension-project"></a>WebPartNodeExtension プロジェクトを構成するには
  
1.  WebPartNodeExtension プロジェクトでは、次の名前を持つ 4 つのコード ファイルを追加します。  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  ショートカット メニューを開き、 **WebPartNodeExtension**プロジェクトを選び、**参照の追加**します。  
  
3.  **参照マネージャー - WebPartNodeExtension**  ダイアログ ボックスで、選択、 **Framework**  タブし、次のアセンブリの各チェック ボックスを選択。  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  選択、**拡張機能**タブ、Microsoft.VisualStudio.SharePoint アセンブリのチェック ボックスを選択し、、 **OK**ボタンをクリックします。  
  
5.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **WebPartNodeExtension**プロジェクト ノードを選び、**プロパティ**します。  
  
     **プロジェクト デザイナー**が開きます。  
  
6.  **[アプリケーション]** タブを選択します。  
  
7.  **既定の名前空間**ボックス (c#) または**ルート名前空間**ボックス ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)])、入力**ServerExplorer.SharePointConnections.WebPartNode**します。  
  
#### <a name="to-configure-the-webpartcommands-project"></a>Webpartcommands プロジェクトを構成するには
  
1.  WebPartCommands プロジェクトでは、WebPartCommands というコード ファイルを追加します。  
  
2.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **WebPartCommands**プロジェクト ノードを選択**追加**を選び、**既存項目の**.  
  
3.  **既存項目の追加**ダイアログ ボックスが WebPartNodeExtension プロジェクトのコード ファイルを含むフォルダーを参照して、WebPartNodeInfo と WebPartCommandIds コード ファイルを選択します。  
  
4.  横にある矢印を選択、**追加**ボタンをクリックし、**リンクとして追加**で表示されるメニューです。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] コード ファイルをリンクとして WebPartCommands プロジェクトに追加します。 その結果、WebPartNodeExtension プロジェクトでコード ファイルにあるが、WebPartCommands プロジェクトで、ファイル内のコードがコンパイルされてもします。  
  
5.  ショートカット メニューを開き、 **WebPartCommands**プロジェクトをもう一度、**参照の追加**します。  
  
6.  **参照マネージャー - WebPartCommands**  ダイアログ ボックスで、選択、**拡張機能**タブ、次のアセンブリの各チェック ボックスを選択し、選択、 **OK**ボタンをクリックします。  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **WebPartCommands**プロジェクトをもう一度、**プロパティ**します。  
  
     **プロジェクト デザイナー**が開きます。  
  
8.  **[アプリケーション]** タブを選択します。  
  
9. **既定の名前空間**ボックス (c#) または**ルート名前空間**ボックス ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)])、入力**ServerExplorer.SharePointConnections.WebPartNode**します。  
  
## <a name="create-icons-for-the-new-nodes"></a>新しいノードのアイコンを作成します。
 2 つのアイコンを作成、**サーバー エクスプ ローラー**拡張機能: 新しいアイコン**Web パーツ ギャラリー**ノード、および各子 Web パーツのノードの下のもう 1 つのアイコン、 **Web パーツ ギャラリー**ノードです。 このチュートリアルで後では、これらのアイコンをノードに関連付けられるコードを記述します。  
  
#### <a name="to-create-icons-for-the-nodes"></a>ノードのアイコンを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **WebPartNodeExtension**プロジェクトを選び、**プロパティ**します。  
  
2.  **プロジェクト デザイナー**が開きます。  
  
3.  選択、**リソース**タブをクリックして、**このプロジェクトに既定のリソース ファイルが含まれていません。ここをクリックすると、1 つを作成する**リンク。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] リソース ファイルを作成し、デザイナーが開きます。  
  
4.  デザイナーの上部にある場合は、横に矢印を選択して、**リソースの追加**メニュー コマンドを選び、**新しいアイコンの追加**で表示されるメニューです。  
  
5.  **新しいリソースの追加**ダイアログ ボックスで、名前の新しいアイコン**WebPartsNode**、選択し、**追加**ボタンをクリックします。  
  
     新しいアイコンが表示、**イメージ エディター**します。  
  
6.  設計を容易に認識できるように、16 x 16 版のアイコンを編集します。  
  
7.  アイコンのサイズは 32 x 32 のバージョンのショートカット メニューを開き、選択し、**イメージ タイプの削除**します。  
  
8.  手順 5 ~ 8 プロジェクトのリソースへの 2 つ目のアイコンを追加して、このアイコンを名前**WebPart**します。  
  
9. **ソリューション エクスプ ローラー**下で、**リソース**のフォルダー、 **WebPartNodeExtension**プロジェクトでショートカット メニューを開き、 **WebPartsNode.ico**.  
  
10. **プロパティ**ウィンドウで、横にある矢印を選択**ビルド アクション**を選び、**埋め込まれたリソース**表示されたメニュー。  
  
11. 最後の 2 つの手順を繰り返します**WebPart.ico**します。  
  
## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>サーバー エクスプ ローラーに Web パーツ ギャラリー ノードを追加します。
 新しいを追加するクラスを作成**Web パーツ ギャラリー**ノードを各 SharePoint サイト ノード。 クラスの実装、新しいノードを追加する、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>インターフェイス。 既存のノードでの動作を拡張するときに、このインターフェイスを実装**サーバー エクスプ ローラー**ノードに子ノードを追加するなど。  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>サーバー エクスプ ローラー Web パーツ ギャラリーのノードを追加するには
  
1.  WebPartNodeExtension プロジェクトで SiteNodeExtension コード ファイルを開くし、次のコードを貼り付けます。  
  
    > [!NOTE]  
    >  後はこのコードを追加する、プロジェクトは、一部のコンパイル エラーになりますが、表示されなくなるときにコードを追加する後の手順でします。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="define-a-node-type-that-represents-a-web-part"></a>Web パーツを表すノード型を定義します。
 Web パーツを表すノードの新しい型を定義するクラスを作成します。 Visual Studio は、下の子ノードを表示するこの新しいノードの種類を使用して、 **Web パーツ ギャラリー**ノード。 各子ノードでは、SharePoint サイト上の 1 つの Web パーツを表します。  
  
 新しいノードの種類をクラスが実装を定義する、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>インターフェイス。 内のノードの新しい型を定義するときに、このインターフェイスを実装**サーバー エクスプ ローラー**します。  
  
#### <a name="to-define-the-web-part-node-type"></a>Web パーツのノード型を定義するには
  
1.  WebPartNodeExtension プロジェクトで WebPartNodeTypeProvder コード ファイルを開くし、次のコードを貼り付けます。  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]  
  
## <a name="define-the-web-part-data-class"></a>Web パーツのデータ クラスを定義します。
 SharePoint サイト上の 1 つの Web パーツに関するデータを格納するクラスを定義します。 このチュートリアルで後で、サイトの場合は、各 Web パーツに関するデータを取得し、このクラスのインスタンスにデータを割り当てますカスタム SharePoint コマンドを作成します。  
  
#### <a name="to-define-the-web-part-data-class"></a>Web パーツのデータ クラスを定義するには
  
1.  WebPartNodeExtension プロジェクトで WebPartNodeInfo コード ファイルを開くし、次のコードを貼り付けます。  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]  
  
## <a name="define-the-ids-for-the-sharepoint-commands"></a>SharePoint コマンドの Id を定義します。
 カスタムの SharePoint コマンドを識別するいくつかの文字列を定義します。 このチュートリアルの後半では、これらのコマンドを実装します。  
  
#### <a name="to-define-the-command-ids"></a>コマンド Id を定義するには
  
1.  WebPartNodeExtension プロジェクトで WebPartCommandIds コード ファイルを開くし、次のコードを貼り付けます。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]  
  
## <a name="create-the-custom-sharepoint-commands"></a>カスタムの SharePoint コマンドを作成します。
 SharePoint サイト上の Web パーツに関するデータを取得するように SharePoint のサーバー オブジェクト モデルを呼び出すカスタム コマンドを作成します。 各コマンドは、メソッドを持つ、<xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute>を適用します。  
  
#### <a name="to-define-the-sharepoint-commands"></a>SharePoint コマンドを定義するには  
  
1.  WebPartCommands プロジェクトで WebPartCommands コード ファイルを開くし、次のコードを貼り付けます。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]  
  
## <a name="checkpoint"></a>チェックポイント  
 この時点で、チュートリアルでは、すべてのコードを**Web パーツ ギャラリー**でプロジェクト ノード、および SharePoint コマンドはようになりました。 両方のプロジェクトがエラーなしでコンパイルするかどうかを確認するソリューションをビルドします。  
  
#### <a name="to-build-the-solution"></a>ソリューションをビルドするには  
  
1.  メニュー バーで、**[ビルド]** > **[ソリューションのビルド]** の順にクリックします。  
  
    > [!WARNING]  
    >  この時点では、VSIX のマニフェスト ファイルでは、作成者の値がないために、WebPartNode プロジェクトはビルド エラーがあります。 後の手順で値を追加するときに、このエラーは表示されなく。  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>拡張機能をデプロイするため、VSIX パッケージを作成します。
 拡張機能を配置するには、ソリューションで VSIX プロジェクトを使用して VSIX パッケージを作成します。 最初に、VSIX プロジェクトの source.extension.vsixmanifest ファイルを変更することで、VSIX パッケージを構成します。 次に、ソリューションをビルドして VSIX パッケージを作成します。  
  
#### <a name="to-configure-the-vsix-package"></a>VSIX パッケージを構成するには  
  
1.  **ソリューション エクスプ ローラー**、WebPartNode プロジェクトで開き、 **source.extension.vsixmanifest**マニフェスト エディターでファイル。  
  
     source.extension.vsixmanifest ファイルが、すべての VSIX パッケージで必要になる extension.vsixmanifest ファイルの基礎となります。 このファイルの詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)します。  
  
2.  **製品名**ボックスに、入力**for サーバー エクスプ ローラー Web パーツのギャラリー ノード**します。  
  
3.  **作成者**ボックスに、入力**Contoso**します。  
  
4.  **説明**ボックスに、入力**サーバー エクスプ ローラーで、[SharePoint 接続] ノードにカスタム Web パーツ ギャラリー ノードを追加します。この拡張機能では、カスタムの SharePoint コマンドを使用して、サーバー オブジェクト モデルを呼び出します。**  
  
5.  選択、**資産**エディターのタブをクリックして、**新規**ボタンをクリックします。  
  
     **新しい資産の追加** ダイアログ ボックスが表示されます。  
  
6.  **型**一覧で、選択**Microsoft.VisualStudio.MefComponent**します。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MefComponent` 要素に対応します。 この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。 詳細については、次を参照してください。 [MEFComponent 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)します。  
  
7.  **ソース**一覧で、選択**現在のソリューションでプロジェクトを**します。  
  
8.  **プロジェクト**一覧で、選択**WebPartNodeExtension**選択し、 **OK**ボタン。  
  
9. マニフェストのエディターで選択、**新規**もう一度ボタンをクリックします。  
  
     **新しい資産の追加** ダイアログ ボックスが表示されます。  
  
10. **型**ボックスに、入力**SharePoint.Commands.v4**します。  
  
    > [!NOTE]  
    >  この要素は、Visual Studio 拡張機能に含めるカスタム拡張機能を指定します。 詳細については、次を参照してください。[資産要素 (VSX Schema)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737)します。  
  
11. **ソース**一覧で、選択、**現在のソリューションでプロジェクトを**リスト項目。  
  
12. **プロジェクト**一覧で、選択**WebPartCommands**、選択し、 **OK**ボタン。  
  
13. メニュー バーで、**ビルド** > **ソリューションのビルド**、ソリューションがエラーなしでコンパイルされるかどうかを確認します。  
  
14. WebPartNode プロジェクトのビルド出力フォルダーに今すぐ WebPartNode.vsix ファイルが含まれていることを確認します。  
  
     既定では、ビルド出力フォルダーは ..\bin\Debug で、プロジェクト ファイルが格納されているフォルダーの下にあります。  
  
## <a name="test-the-extension"></a>拡張機能をテストします。
 新しいテストする準備ができました**Web パーツ ギャラリー**ノード**サーバー エクスプ ローラー**します。 まず、Visual Studio の実験用インスタンスで拡張機能のデバッグを開始します。 次に、新しい使用**Web パーツ**の実験用インスタンスでノード[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。  
  
#### <a name="to-start-debugging-the-extension"></a>拡張機能のデバッグを開始するには  
  
1.  再起動[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]管理者の資格情報と WebPartNode ソリューションを開きます。  
  
2.  WebPartNodeExtension プロジェクトで SiteNodeExtension コード ファイルを開くし、コードの最初の行にブレークポイントを追加し、`NodeChildrenRequested`と`CreateWebPartNodes`メソッド。  
  
3.  選択、 **F5**キー デバッグを開始します。  
  
     Visual Studio では、Server Explorer\1.0 の %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web パーツ ギャラリーのノードの拡張機能を拡張機能をインストールし、Visual Studio の実験用インスタンスを開始します。 このインスタンスの Visual Studio でプロジェクト項目をテストします。  
  
#### <a name="to-test-the-extension"></a>拡張機能をテストするには  
  
1.  実験用インスタンスで[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、メニュー バーで、**ビュー** > **サーバー エクスプ ローラー**します。  
  
2.  テスト用に使用する SharePoint サイトが表示されない場合は、次の手順を実行、 **SharePoint 接続**ノード**サーバー エクスプ ローラー**:  
  
    1.  **サーバー エクスプ ローラー**、ショートカット メニューを開き**SharePoint 接続**を選び、**接続の追加**します。  
  
    2.  **SharePoint 接続の追加** ダイアログ ボックスで、接続、および選択する SharePoint サイトの URL を入力、 **OK**ボタン。  
  
         開発用コンピューターに SharePoint サイトを指定する入力 **http://localhost**します。  
  
3.  (これは、サイトの URL が表示されます) のサイト接続ノードを展開し、子サイトのノードを展開 (たとえば、**チーム サイト**)。  
  
4.  確認しますの他のインスタンス内のコード[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]前に設定したブレークポイントで停止、`NodeChildrenRequested`メソッドを選び、 **f5 キーを押して**プロジェクトのデバッグを続行します。  
  
5.  Visual Studio の実験用インスタンスのという名前の新しいノードを確認します**Web パーツ ギャラリー**最上位サイトのノードの下に表示し、展開、 **Web パーツ ギャラリー**ノード。  
  
6.  Visual Studio の他のインスタンス内のコードを以前に設定したブレークポイントで停止することを確認、`CreateWebPartNodes`メソッドを選択し、 **F5**プロジェクトのデバッグを続行するキー。  
  
7.  Visual Studio の実験用インスタンスの下に接続されているサイト上のすべての Web パーツが表示されることを確認します、 **Web パーツ ギャラリー**ノード**サーバー エクスプ ローラー**します。  
  
8.  **サーバー エクスプ ローラー**Web パーツでは、いずれかのショートカット メニューを開き、選択し、**プロパティ**します。  
  
9. インスタンスで[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、デバッグしているに Web パーツの詳細が表示されることを確認、**プロパティ**ウィンドウ。  
  
## <a name="uninstall-the-extension-from-visual-studio"></a>Visual Studio から拡張機能をアンインストールします。
 拡張機能のテストが完了したら、Visual Studio から拡張機能をアンインストールします。  
  
#### <a name="to-uninstall-the-extension"></a>拡張機能をアンインストールするには  
  
1.  実験用インスタンスで[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、メニュー バーで、**ツール** > **拡張機能と更新**します。  
  
     **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で選択**for サーバー エクスプ ローラー Web パーツ ギャラリー ノード拡張**、選択し、**アンインストール**ボタンをクリックします。  
  
3.  ダイアログ ボックスが表示されますが、選択、**はい**ボタンをクリックして、拡張機能をアンインストールすることを確認します、**今すぐ再起動**アンインストールを完了するボタン。  
  
4.  Visual Studio (実験用インスタンスと WebPartNode ソリューションが開いている Visual Studio のインスタンス) の両方のインスタンスを閉じます。  
  
## <a name="see-also"></a>関連項目
 [サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張します。](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [チュートリアル: は、サーバー エクスプ ローラー拡張機能では、SharePoint クライアント オブジェクト モデルを呼び出す](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [アイコン用イメージ エディター](/cpp/windows/image-editor-for-icons)   
 [アイコンまたはその他のイメージの作成&#40;アイコン用イメージ エディター&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
