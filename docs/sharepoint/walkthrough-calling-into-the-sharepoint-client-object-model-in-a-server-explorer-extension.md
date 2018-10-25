---
title: 'チュートリアル: サーバー エクスプ ローラー拡張機能で、SharePoint クライアント オブジェクト モデルを呼び出す |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ef2a2800ecb46f12f9dde4357bf54711a1df8797
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934679"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>チュートリアル: サーバー エクスプ ローラー拡張機能では、SharePoint クライアント オブジェクト モデルを呼び出す
  このチュートリアルの拡張機能から SharePoint クライアント オブジェクト モデルを呼び出す方法、 **SharePoint 接続**ノード**サーバー エクスプ ローラー**します。 SharePoint クライアント オブジェクト モデルを使用する方法の詳細については、次を参照してください。[の SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)します。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]拡張機能を拡張する、 **SharePoint 接続**のノード**サーバー エクスプ ローラー**次の方法で。  
  
    -   拡張機能の追加、 **Web パーツ ギャラリー**内の各 SharePoint サイト ノード下にノード**サーバー エクスプ ローラー**します。 この新しいノードには、サイトの Web パーツ ギャラリーでは、各 Web パーツを表す子ノードが含まれています。  
  
    -   拡張機能は、新しい種類の Web パーツ インスタンスを表すノードを定義します。 この新しいノードの種類は、新しい子ノードの基礎**Web パーツ ギャラリー**ノード。 新しい Web パーツのノードの種類の情報が表示されます、**プロパティ**ノードが表す Web パーツのウィンドウ。  
  
-   拡張機能をデプロイする Visual Studio Extension (VSIX) パッケージを作成します。  
  
-   デバッグと、拡張機能をテストします。  
  
> [!NOTE]  
>  このチュートリアルで作成した拡張機能の拡張機能で作成するよう[チュートリアル: サーバー エクスプ ローラー web パーツを表示する拡張](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)します。 そのチュートリアルは、SharePoint サーバー オブジェクト モデルを使用しますが、このチュートリアルは、クライアント オブジェクト モデルを使用して同じタスクを実行します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   サポート対象エディションの Windows、SharePoint、Visual Studio。
  
-   Visual Studio SDK。 このチュートリアルでは、 **VSIX プロジェクト**sdk、拡張機能を配置するための VSIX パッケージを作成するテンプレート。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールを拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)します。  
  
次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   SharePoint クライアント オブジェクト モデルを使用します。 詳細については、次を参照してください。[マネージ クライアント オブジェクト モデル](http://go.microsoft.com/fwlink/?LinkId=177797)します。  
  
-   SharePoint web パーツ。 詳細については、次を参照してください。 [Web パーツの概要](http://go.microsoft.com/fwlink/?LinkId=177803)します。  
  
## <a name="create-the-projects"></a>プロジェクトを作成します。
 このチュートリアルを完了するには、2 つのプロジェクトを作成する必要があります。  
  
- VSIX プロジェクトを配置するための VSIX パッケージを作成、**サーバー エクスプ ローラー**拡張機能。  
  
- 実装するクラス ライブラリ プロジェクト、**サーバー エクスプ ローラー**拡張機能。  
  
  この 2 つのプロジェクトを作成することから始めます。  
  
#### <a name="to-create-the-vsix-project"></a>VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで、**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#** または**Visual Basic**ノードを選び、**拡張**。  
  
    > [!NOTE]  
    >  **Extensibility**ノードは、Visual Studio SDK をインストールする場合にのみ使用できます。 詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
4.  ダイアログ ボックスの上部にある次のように選択します。 **.NET Framework 4.5**で .NET Framework のバージョンの一覧。  
  
     SharePoint ツール拡張機能では、このバージョンの .NET Framework の機能が必要です。  
  
5.  選択、 **VSIX プロジェクト**テンプレート。  
  
6.  **名前**ボックスに「 **WebPartNode**、選択し、 **OK**ボタン。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **WebPartNode**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
#### <a name="to-create-the-extension-project"></a>拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ソリューション ノードのショートカット メニューを開き、**追加**を選び、**新しいプロジェクト**します。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#** または**Visual Basic**ノードを選び、 **Windows**します。  
  
3.  ダイアログ ボックスの上部にある次のように選択します。 **.NET Framework 4.5**で .NET Framework のバージョンの一覧。  
  
4.  プロジェクト テンプレートの一覧で選択**クラス ライブラリ**します。  
  
5.  **名前**ボックスに、入力**WebPartNodeExtension**、選択し、 **OK**ボタン。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **WebPartNodeExtension**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。  
  
6.  Class1 コード ファイルをプロジェクトから削除します。  
  
## <a name="configure-the-extension-project"></a>拡張機能プロジェクトを構成します。
 拡張機能を作成するコードを記述する前に、コード ファイルと、プロジェクトにアセンブリ参照を追加する必要があり、既定の名前空間を更新する必要があります。  
  
#### <a name="to-configure-the-project"></a>プロジェクトを構成するには  
  
1.  **WebPartNodeExtension**プロジェクトに、SiteNodeExtension および WebPartNodeTypeProvider という 2 つのコード ファイルを追加します。  
  
2.  WebPartNodeExtension プロジェクトのショートカット メニューを開き、選択し、**参照の追加**します。  
  
3.  **参照マネージャー - WebPartNodeExtension**  ダイアログ ボックスで、選択、 **Framework**ノード、および System.ComponentModel.Composition および System.Windows.Forms のチェック ボックスをオンアセンブリ。  
  
4.  選択、**拡張**ノードは、次のアセンブリの各チェック ボックスを選択し、、 **OK**ボタン。  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  ショートカット メニューを開き、 **WebPartNodeExtension**プロジェクトを選び、**プロパティ**します。  
  
     **プロジェクト デザイナー**が開きます。  
  
6.  **[アプリケーション]** タブを選択します。  
  
7.  **既定の名前空間**ボックス (c#) または**ルート名前空間**(Visual Basic) をボックスに、入力**ServerExplorer.SharePointConnections.WebPartNode**します。  
  
## <a name="create-icons-for-the-new-nodes"></a>新しいノードのアイコンを作成します。
 2 つのアイコンを作成、**サーバー エクスプ ローラー**拡張機能: 新しいアイコン**Web パーツ ギャラリー**ノードと各子 Web パーツのノードの下のもう 1 つのアイコン、 **Web パーツ ギャラリー**ノードです。 このチュートリアルで後でこれらのアイコンをノードに関連付けられるコードを記述します。  
  
#### <a name="to-create-icons-for-the-nodes"></a>ノードのアイコンを作成するには  
  
1.  **プロジェクト デザイナー** WebPartNodeExtension プロジェクトの選択、**リソース**タブ。  
  
2.  リンクを選択**このプロジェクトに既定のリソース ファイルが含まれていません。ここをクリックすると、1 つを作成します。**  
  
     Visual Studio では、リソース ファイルを作成し、デザイナーで開かれます。  
  
3.  デザイナーの上部にある矢印をクリックしてで、**リソースの追加**メニュー コマンドを選び、**新しいアイコンの追加**します。  
  
4.  入力**WebPartsNode**新しいアイコンの名前を付けて、**追加**ボタン。  
  
     新しいアイコンが表示、**イメージ エディター**します。  
  
5.  設計を容易に認識できるように、16 x 16 版のアイコンを編集します。  
  
6.  アイコンのサイズは 32 x 32 のバージョンのショートカット メニューを開き、選択し、**イメージ タイプの削除**します。  
  
7.  手順 3. ~ 7. プロジェクトのリソースへの 2 つ目のアイコンを追加して、このアイコンを名前**WebPart**します。  
  
8.  **ソリューション エクスプ ローラー**の**リソース**のフォルダー、 **WebPartNodeExtension**プロジェクトで、選択*WebPartsNode.ico*します。  
  
9. **プロパティ**ウィンドウを開いて、**ビルド アクション**一覧を選び、**埋め込みリソース**します。  
  
10. 最後の 2 つの手順を繰り返します*WebPart.ico*します。  
  
## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>サーバー エクスプ ローラー web パーツのギャラリーのノードを追加します。
 新しいを追加するクラスを作成**Web パーツ ギャラリー**ノードを各 SharePoint サイト ノード。 クラスの実装、新しいノードを追加する、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>インターフェイス。 既存のノードでの動作を拡張するときに、このインターフェイスを実装**サーバー エクスプ ローラー**ノードに新しい子ノードを追加するなど。  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>サーバー エクスプ ローラーに web パーツのギャラリーのノードを追加するには
  
1.  次のコードを貼り付け、 **SiteNodeExtension**のコード ファイル、 **WebPartNodeExtension**プロジェクト。  
  
    > [!NOTE]  
    >  このコードを追加した直後は、いくつかのコンパイル エラーが発生します。 これらのエラーは、この後の手順でコードを追加すると解消されます。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="define-a-node-type-that-represents-a-web-part"></a>Web パーツを表すノード型を定義します。
 Web パーツを表すノードの新しい型を定義するクラスを作成します。 Visual Studio は、下の子ノードを表示するこの新しいノードの種類を使用して、 **Web パーツ ギャラリー**ノード。 これらの子ノードは、SharePoint サイト上の 1 つの Web パーツを表します。  
  
 新しいノードの種類をクラスが実装を定義する、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>インターフェイス。 内のノードの新しい型を定義するときに、このインターフェイスを実装**サーバー エクスプ ローラー**します。  
  
#### <a name="to-define-the-web-part-node-type"></a>Web パーツのノード型を定義するには
  
1.  次のコードを貼り付け、 **WebPartNodeTypeProvider**のコード ファイル、 **WebPartNodeExtension**プロジェクト。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## <a name="checkpoint"></a>チェックポイント  
 この時点で、チュートリアルでは、すべてのコードを**Web パーツ ギャラリー**ノードは、プロジェクトのようになりました。 ビルド、 **WebPartNodeExtension**プロジェクトをエラーなしにコンパイルできるかどうかを確認します。  
  
#### <a name="to-build-the-project"></a>プロジェクトをビルドするには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **WebPartNodeExtension**プロジェクトを選び、**ビルド**します。  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>拡張機能をデプロイするため、VSIX パッケージを作成します。
 拡張機能を配置するには、ソリューションで VSIX プロジェクトを使用して VSIX パッケージを作成します。 最初に、プロジェクトに含まれている source.extension.vsixmanifest ファイルを変更することで、VSIX パッケージを構成します。 ソリューションをビルドして VSIX パッケージを作成します。  
  
#### <a name="to-configure-the-vsix-package"></a>VSIX パッケージを構成するには  
  
1.  **ソリューション エクスプ ローラー**の**WebPartNode**プロジェクトを開き、 **source.extension.vsixmanifest**マニフェスト エディターでファイル。  
  
     source.extension.vsixmanifest ファイルが、すべての VSIX パッケージで必要になる extension.vsixmanifest ファイルの基礎となります。 このファイルの詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)します。  
  
2.  **製品名**ボックスに、入力**for サーバー エクスプ ローラー Web パーツのギャラリー ノード**します。  
  
3.  **作成者**ボックスに、入力**Contoso**します。  
  
4.  **説明**ボックスに、入力**サーバー エクスプ ローラーで、[SharePoint 接続] ノードにカスタム Web パーツ ギャラリー ノードを追加します。** します。  
  
5.  **資産** タブ、エディターの選択、**新規**ボタンをクリックします。  
  
6.  **新しい資産の追加** ダイアログ ボックスで、**型**一覧で、選択**Microsoft.VisualStudio.MefComponent**します。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MefComponent` 要素に対応します。 この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。 詳細については、次を参照してください。 [MEFComponent 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)します。  
  
7.  **ソース**一覧で、選択**現在のソリューションでプロジェクトを**します。  
  
8.  **プロジェクト**一覧で、選択**WebPartNodeExtension**、選択し、 **OK**ボタン。  
  
9. メニュー バーで、**ビルド** > **ソリューションのビルド**、ソリューションがエラーなしでコンパイルされるかどうかを確認します。  
  
10. WebPartNode プロジェクトのビルド出力フォルダーに今すぐ WebPartNode.vsix ファイルが含まれていることを確認します。  
  
     既定では、ビルド出力フォルダーは ..\bin\Debug で、プロジェクト ファイルが格納されているフォルダーの下にあります。  
  
## <a name="test-the-extension"></a>拡張機能をテストします。
 新しいテストする準備が整いました**Web パーツ ギャラリー**ノード**サーバー エクスプ ローラー**します。 最初に、Visual Studio の実験用インスタンスで拡張機能プロジェクトのデバッグを開始します。 使用して、新しい**Web パーツ**Visual Studio の実験用インスタンスでノード。  
  
#### <a name="to-start-debugging-the-extension"></a>拡張機能のデバッグを開始するには  
  
1.  管理者の資格情報で Visual Studio を再起動し、開き、 **WebPartNode**ソリューション。  
  
2.  WebPartNodeExtension プロジェクトで開き、 **SiteNodeExtension**コード ファイル、およびコードの最初の行にブレークポイントを追加し、`NodeChildrenRequested`と`CreateWebPartNodes`メソッド。  
  
3.  選択、 **F5**キー デバッグを開始します。  
  
     Visual Studio では、Server Explorer\1.0 の %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web パーツ ギャラリーのノードの拡張機能を拡張機能をインストールし、Visual Studio の実験用インスタンスを開始します。 このインスタンスの Visual Studio でプロジェクト項目をテストします。  
  
#### <a name="to-test-the-extension"></a>拡張機能をテストするには  
  
1.  メニュー バーで、Visual Studio の実験用インスタンスで次のように選択します。**ビュー** > **サーバー エクスプ ローラー**します。  
  
2.  下のテストに使用する SharePoint サイトが表示されることを確認、 **SharePoint 接続**ノード**サーバー エクスプ ローラー**します。 表示されない場合は、次の手順に従います。  
  
    1.  ショートカット メニューを開き**SharePoint 接続**を選び、**接続の追加**します。  
  
    2.  **SharePoint 接続の追加** ダイアログ ボックスで、接続、および選択する SharePoint サイトの URL を入力、 **OK**ボタン。  
  
         開発用コンピューターに SharePoint サイトを指定する入力 **http://localhost**します。  
  
3.  (これは、サイトの URL が表示されます) のサイト接続ノードを展開し、子サイトのノードを展開 (たとえば、**チーム サイト**)。  
  
4.  Visual Studio の他のインスタンス内のコードを以前に設定したブレークポイントで停止することを確認、`NodeChildrenRequested`メソッドを選択し、 **F5**プロジェクトのデバッグを続行するキー。  
  
5.  Visual Studio の実験用インスタンスの展開、 **Web パーツ ギャラリー**ノードで、最上位のサイト ノード下に表示されます。  
  
6.  Visual Studio の他のインスタンス内のコードを以前に設定したブレークポイントで停止することを確認、`CreateWebPartNodes`メソッドを選択し、 **F5**プロジェクトのデバッグを続行するキー。  
  
7.  Visual Studio の実験用インスタンスの下に接続されているサイト上のすべての Web パーツが表示されることを確認します、 **Web パーツ ギャラリー**ノード**サーバー エクスプ ローラー**します。  
  
8.  Web パーツのショートカット メニューを開き、選択し、**プロパティ**します。  
  
9. **プロパティ**ウィンドウで、Web パーツの詳細が表示されることを確認します。  
  
10. **サーバー エクスプ ローラー**、同じ Web パーツのショートカット メニューを開き、選択し、**メッセージを表示する**します。  
  
     メッセージ ボックスが表示されますが、選択、 **OK**ボタンをクリックします。  
  
## <a name="uninstall-the-extension-from-visual-studio"></a>Visual Studio から拡張機能をアンインストールします。
 拡張機能のテストが完了したら、Visual Studio からアンインストールします。  
  
#### <a name="to-uninstall-the-extension"></a>拡張機能をアンインストールするには  
  
1.  メニュー バーで、Visual Studio の実験用インスタンスで次のように選択します。**ツール** > **拡張機能と更新**します。  
  
     **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で選択**for サーバー エクスプ ローラー Web パーツ ギャラリーのノード**、選択し、**アンインストール**ボタンをクリックします。  
  
3.  ダイアログ ボックスが表示されますが、選択、**はい**ボタンをクリックします。  
  
4.  選択、**今すぐ再起動**アンインストールを完了するボタンをクリックします。  
  
     プロジェクト アイテムもアンインストールされます。  
  
5.  Visual Studio (実験用インスタンスと WebPartNode ソリューションが開いている Visual Studio のインスタンス) の両方のインスタンスを閉じます。  
  
## <a name="see-also"></a>関連項目
 [SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張します。](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [チュートリアル: web パーツを表示するサーバー エクスプ ローラーの拡張します。](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [アイコン用イメージ エディター](/cpp/windows/image-editor-for-icons)   
 [アイコンまたはその他のイメージの作成&#40;アイコン用イメージ エディター&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)