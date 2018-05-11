---
title: 'チュートリアル: サーバー エクスプ ローラー拡張機能に SharePoint クライアント オブジェクト モデルを呼び出す |Microsoft ドキュメント'
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
ms.openlocfilehash: 4951d9960a3027e8d72bb0fbc72d551f123993ce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>チュートリアル: サーバー エクスプローラーの拡張機能から SharePoint クライアント オブジェクト モデルを呼び出す
  このチュートリアルのための拡張機能から SharePoint クライアント オブジェクト モデルを呼び出す方法、 **SharePoint 接続**内のノード**サーバー エクスプ ローラー**です。 SharePoint クライアント オブジェクト モデルを使用する方法の詳細については、次を参照してください。[の SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)です。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   作成する、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を拡張する拡張機能、 **SharePoint 接続**のノード**サーバー エクスプ ローラー**次のようにします。  
  
    -   拡張機能を追加、 **Web パーツ ギャラリー**ノードの下にある各 SharePoint サイト**サーバー エクスプ ローラー**です。 この新しいノードには、サイトの Web パーツ ギャラリーでは、各 Web パーツを表す子ノードが含まれています。  
  
    -   拡張機能では、Web パーツ インスタンスを表すノードの新しい型を定義します。 このノード型で、新しい子ノードの基礎となる**Web パーツ ギャラリー**ノード。 新しい Web パーツのノードの種類の情報が表示されます、**プロパティ**ノードが表す Web パーツのウィンドウ。  
  
-   拡張機能を配置する Visual Studio Extension (VSIX) パッケージを作成します。  
  
-   デバッグと、拡張機能をテストします。  
  
> [!NOTE]  
>  このチュートリアルで作成した拡張機能の拡張機能で作成するようになります[チュートリアル: サーバー エクスプ ローラー Web パーツの表示を拡張する](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)です。 チュートリアルは、SharePoint サーバー オブジェクト モデルを使用しますが、このチュートリアルは、クライアント オブジェクト モデルを使用して同じタスクを実行します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   サポート対象エディションの Windows、SharePoint、Visual Studio。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   Visual Studio SDK。 このチュートリアルでは、 **VSIX プロジェクト**sdk、拡張機能を配置するための VSIX パッケージを作成するテンプレートです。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツール拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)です。  
  
次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   SharePoint クライアント オブジェクト モデルを使用します。 詳細については、次を参照してください。[マネージ クライアント オブジェクト モデル](http://go.microsoft.com/fwlink/?LinkId=177797)です。  
  
-   SharePoint web パーツ。 詳細については、次を参照してください。 [Web パーツの概要](http://go.microsoft.com/fwlink/?LinkId=177803)です。  
  
## <a name="creating-the-projects"></a>プロジェクトの作成  
 このチュートリアルを完了するには、2 つのプロジェクトを作成する必要があります。  
  
-   VSIX プロジェクトを配置するための VSIX パッケージを作成する、**サーバー エクスプ ローラー**拡張機能です。  
  
-   実装するクラス ライブラリ プロジェクト、**サーバー エクスプ ローラー**拡張機能です。  
  
 この 2 つのプロジェクトを作成することから始めます。  
  
#### <a name="to-create-the-vsix-project"></a>VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#**または**Visual Basic** 、ノードを選択し**Extensibility**です。  
  
    > [!NOTE]  
    >  **Extensibility**ノードは、Visual Studio SDK をインストールする場合にのみ使用できます。 詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
4.  ダイアログ ボックスの上部には、次のように選択します。 **.NET Framework 4.5** 、.NET Framework のバージョンの一覧にします。  
  
     SharePoint ツール拡張機能では、このバージョンの .NET Framework の機能が必要です。  
  
5.  選択、 **VSIX プロジェクト**テンプレート。  
  
6.  **名前**ボックスに、入力**WebPartNode**を選択し、 **OK**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **WebPartNode**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
#### <a name="to-create-the-extension-project"></a>拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**でソリューション ノードのショートカット メニューを開き、**追加**を選択し**新しいプロジェクト**です。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#**または**Visual Basic** 、ノードを選択し**Windows**です。  
  
3.  ダイアログ ボックスの上部には、次のように選択します。 **.NET Framework 4.5** 、.NET Framework のバージョンの一覧にします。  
  
4.  プロジェクト テンプレートの一覧で選択**クラス ライブラリ**です。  
  
5.  **名前**ボックスに、入力**WebPartNodeExtension**を選択し、 **OK**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **WebPartNodeExtension**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。  
  
6.  Class1 コード ファイルをプロジェクトから削除します。  
  
## <a name="configuring-the-extension-project"></a>拡張機能プロジェクトの構成  
 拡張機能を作成するコードを記述する前に、コード ファイルおよびアセンブリ参照をプロジェクトに追加する必要があり、既定の名前空間を更新する必要があります。  
  
#### <a name="to-configure-the-project"></a>プロジェクトを構成するには  
  
1.  **WebPartNodeExtension**プロジェクト、SiteNodeExtension および WebPartNodeTypeProvider という 2 つのコード ファイルを追加します。  
  
2.  WebPartNodeExtension プロジェクトのショートカット メニューを開き、選択**参照の追加**です。  
  
3.  **参照マネージャー - WebPartNodeExtension**  ダイアログ ボックスで、選択、 **Framework**ノード、および、System.ComponentModel.Composition および system.windows.forms の各し、チェック ボックスをオンアセンブリ。  
  
4.  選択、**拡張**ノード、次のアセンブリの各チェック ボックスをオンにして、 **[ok]**ボタン。  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  ショートカット メニューを開き、 **WebPartNodeExtension**プロジェクトをクリックして**プロパティ**です。  
  
     **プロジェクト デザイナー**が開きます。  
  
6.  **[アプリケーション]** タブを選択します。  
  
7.  **既定の名前空間**ボックス (c#) または**ルート名前空間**ボックス (Visual Basic) を入力**ServerExplorer.SharePointConnections.WebPartNode**です。  
  
## <a name="creating-icons-for-the-new-nodes"></a>新しいノードのアイコンの作成  
 2 つのアイコンを作成、**サーバー エクスプ ローラー**拡張機能: 新しいアイコン**Web パーツ ギャラリー**ノードと各子 Web パーツのノードの下の別のアイコン、 **Web パーツ ギャラリー**ノードです。 このチュートリアルの後半でノードとこれらのアイコンを関連付けるコードを記述します。  
  
#### <a name="to-create-icons-for-the-nodes"></a>ノードのアイコンを作成するには  
  
1.  **プロジェクト デザイナー** WebPartNodeExtension プロジェクトを選択、**リソース**タブです。  
  
2.  リンクを選択**このプロジェクトに既定のリソース ファイルが含まれていません。作成するのにはここをクリックします。**  
  
     Visual Studio では、リソース ファイルが作成され、デザイナーで開かれます。  
  
3.  デザイナーの上部には、上の矢印を選択して、**リソースの追加**メニュー コマンドを使用し、**新しいアイコンの追加**です。  
  
4.  入力**WebPartsNode**新しいアイコンの名前を付けて、**追加**ボタンをクリックします。  
  
     新しいアイコンが表示されます、**イメージ エディター**です。  
  
5.  16 x 16 版のアイコンを編集して、デザイン簡単に識別できるようにします。  
  
6.  アイコンのサイズは 32 x 32 のバージョンについては、ショートカット メニューを開き、選択**イメージ タイプの削除**です。  
  
7.  手順 3. ~ 7. をプロジェクトのリソースに 2 番目のアイコンを追加して、このアイコンの名前を付けます**WebPart**です。  
  
8.  **ソリューション エクスプ ローラー**で、**リソース**用のフォルダー、 **WebPartNodeExtension**プロジェクト**WebPartsNode.ico**です。  
  
9. **プロパティ**ウィンドウを開いた、**ビルド アクション**一覧をクリックして**埋め込まれたリソース**です。  
  
10. 最後の 2 つの手順を繰り返します**WebPart.ico**です。  
  
## <a name="adding-the-web-part-gallery-node-to-server-explorer"></a>サーバー エクスプ ローラー Web パーツ ギャラリー ノードを追加します。  
 新しいを追加するクラスを作成**Web パーツ ギャラリー** SharePoint サイトの各ノードにノードです。 クラスを実装して、新しいノードを追加する、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>インターフェイスです。 既存のノードでの動作を拡張するには必ず、このインターフェイスを実装して**サーバー エクスプ ローラー**ノードに新しい子ノードを追加するなどです。  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>サーバー エクスプ ローラー Web パーツ ギャラリーのノードを追加するには  
  
1.  次のコードを貼り付け、 **SiteNodeExtension**のコード ファイル、 **WebPartNodeExtension**プロジェクト。  
  
    > [!NOTE]  
    >  このコードを追加した直後は、いくつかのコンパイル エラーが発生します。 これらのエラーは、この後の手順でコードを追加すると解消されます。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="defining-a-node-type-that-represents-a-web-part"></a>Web パーツを表すノードの種類の定義  
 Web パーツを表すノードの新しい型を定義するクラスを作成します。 Visual Studio で子ノードを表示するこの新しいノード型を使用して、 **Web パーツ ギャラリー**ノード。 これらの子ノードは、SharePoint サイトで単一の Web パーツを表します。  
  
 新しいノードの種類をクラスを実装を定義する、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>インターフェイスです。 内のノードの新しい型を定義するには必ず、このインターフェイスを実装して**サーバー エクスプ ローラー**です。  
  
#### <a name="to-define-the-web-part-node-type"></a>Web パーツのノード型を定義するには  
  
1.  次のコードを貼り付け、 **WebPartNodeTypeProvider**のコード ファイル、 **WebPartNodeExtension**プロジェクト。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## <a name="checkpoint"></a>チェックポイント  
 この時点で、チュートリアルでは、すべてのコードで、 **Web パーツ ギャラリー**ノードは、プロジェクトのようになりました。 ビルド、 **WebPartNodeExtension**エラーなくコンパイルできるかどうかを確認するプロジェクトです。  
  
#### <a name="to-build-the-project"></a>プロジェクトをビルドするには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **WebPartNodeExtension**プロジェクトをクリックして**ビルド**です。  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>拡張機能を配置する VSIX パッケージの作成  
 拡張機能を配置するには、ソリューションで VSIX プロジェクトを使用して VSIX パッケージを作成します。 最初に、プロジェクトに含まれている source.extension.vsixmanifest ファイルを変更して、VSIX パッケージを構成します。 ソリューションをビルドして VSIX パッケージを作成します。  
  
#### <a name="to-configure-the-vsix-package"></a>VSIX パッケージを構成するには  
  
1.  **ソリューション エクスプ ローラー**で、 **WebPartNode**プロジェクトを開き、 **source.extension.vsixmanifest**マニフェスト エディターでファイル。  
  
     source.extension.vsixmanifest ファイルが、すべての VSIX パッケージで必要になる extension.vsixmanifest ファイルの基礎となります。 このファイルの詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)です。  
  
2.  **Product Name**ボックスに、入力**用サーバー エクスプ ローラー Web パーツのギャラリー ノード**です。  
  
3.  **作成者**ボックスに、入力**Contoso**です。  
  
4.  **説明**ボックスに、入力**サーバー エクスプ ローラーで、[SharePoint 接続] ノードにカスタム Web パーツ ギャラリー ノードを追加**です。  
  
5.  **資産** タブ、エディターの選択、**新規**ボタンをクリックします。  
  
6.  **新しいアセットの追加** ダイアログ ボックスで、**型**一覧で、選択**Microsoft.VisualStudio.MefComponent**です。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MefComponent` 要素に対応します。 この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。 詳細については、次を参照してください。 [MEFComponent 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)です。  
  
7.  **ソース**一覧で、選択**現在のソリューション内のプロジェクト**です。  
  
8.  **プロジェクト**一覧で、選択**WebPartNodeExtension**を選択し、 **OK**ボタンをクリックします。  
  
9. メニュー バーで、次のように選択します。**ビルド**、**ソリューションのビルド**、し、ソリューションがコンパイル エラーが発生しないことを確認します。  
  
10. WebPartNode プロジェクトのビルド出力フォルダーに今すぐ WebPartNode.vsix ファイルが含まれていることを確認してください。  
  
     既定では、ビルド出力フォルダーは ..\bin\Debug で、プロジェクト ファイルが格納されているフォルダーの下にあります。  
  
## <a name="testing-the-extension"></a>拡張機能のテスト  
 新しいテストする準備が整いました**Web パーツ ギャラリー**内のノード**サーバー エクスプ ローラー**です。 まず、Visual Studio の実験用インスタンスで拡張機能プロジェクトのデバッグを開始します。 使用して、新しい**Web パーツ**Visual Studio の実験用インスタンス内のノードです。  
  
#### <a name="to-start-debugging-the-extension"></a>拡張機能のデバッグを開始するには  
  
1.  管理者の資格情報で Visual Studio を再起動を開き、 **WebPartNode**ソリューションです。  
  
2.  WebPartNodeExtension プロジェクトで開き、 **SiteNodeExtension**コード ファイル、およびコードの最初の行にブレークポイントを追加し、`NodeChildrenRequested`と`CreateWebPartNodes`メソッドです。  
  
3.  F5 キーを押してデバッグを開始します。  
  
     Visual Studio では、サーバー Explorer\1.0 用 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web パーツ ギャラリーのノードの拡張機能を拡張機能をインストールし、Visual Studio の実験用インスタンスを開始します。 このインスタンスの Visual Studio でプロジェクト項目をテストします。  
  
#### <a name="to-test-the-extension"></a>拡張機能をテストするには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで、次のように選択します。**ビュー**、**サーバー エクスプ ローラー**です。  
  
2.  テスト用に使用する SharePoint サイトが表示されることを確認してください、 **SharePoint 接続**内のノード**サーバー エクスプ ローラー**です。 表示されない場合は、次の手順に従います。  
  
    1.  ショートカット メニューを開き、 **SharePoint 接続**を選択し**接続の追加**です。  
  
    2.  **[SharePoint 接続の追加**] ダイアログ ボックスで、接続し、順に選択する SharePoint サイトの URL を入力、 **OK**ボタンをクリックします。  
  
         開発用コンピューター上の SharePoint サイトを指定する入力 **http://localhost**です。  
  
3.  サイト接続ノード (サイトの URL が表示されます) を展開し、サイトの子ノードを展開 (たとえば、**チーム サイト**)。  
  
4.  Visual Studio の他のインスタンス内のコードが以前に設定したブレークポイントで停止することを確認、`NodeChildrenRequested`メソッド、F5 キーをプロジェクトのデバッグを続行するとします。  
  
5.  Visual Studio の実験用インスタンスの展開、 **Web パーツ ギャラリー**ノードで、最上位のサイト ノード下に表示されます。  
  
6.  Visual Studio の他のインスタンス内のコードが以前に設定したブレークポイントで停止することを確認、`CreateWebPartNodes`メソッド、F5 キーをプロジェクトのデバッグを続行するとします。  
  
7.  Visual Studio の実験用インスタンスの接続サイト上のすべての Web パーツが表示されることを確認してください、 **Web パーツ ギャラリー**内のノード**サーバー エクスプ ローラー**です。  
  
8.  Web パーツのショートカット メニューを開きを選択し、**プロパティ**です。  
  
9. **プロパティ**ウィンドウで、Web パーツの詳細が表示されることを確認します。  
  
10. **サーバー エクスプ ローラー**、同じ Web パーツのショートカット メニューを開き、クリックして**メッセージを表示する**です。  
  
     メッセージ ボックスが表示されますが、選択、 **OK**ボタンをクリックします。  
  
## <a name="uninstalling-the-extension-from-visual-studio"></a>Visual Studio から拡張機能のアンインストール  
 拡張機能のテストが完了したら、Visual Studio からアンインストールします。  
  
#### <a name="to-uninstall-the-extension"></a>拡張機能をアンインストールするには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで、次のように選択します。**ツール**、**拡張機能と更新プログラム**です。  
  
     **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で選択**用サーバー エクスプ ローラー Web パーツのギャラリー ノード**を選択し、**アンインストール**ボタンをクリックします。  
  
3.  ダイアログ ボックスが表示されますが、選択、**はい**ボタンをクリックします。  
  
4.  選択、**今すぐ再起動**ボタンをクリックしてアンインストールを完了します。  
  
     プロジェクト項目もアンインストールされます。  
  
5.  Visual Studio (実験用インスタンスおよび WebPartNode ソリューションが開いている Visual Studio のインスタンス) の両方のインスタンスを閉じます。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint オブジェクト モデルの呼び出し](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張します。](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [チュートリアル: サーバー エクスプ ローラー Web パーツ表示するための拡張](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [アイコン用イメージ エディター](/cpp/windows/image-editor-for-icons)   
 [アイコンまたはその他のイメージの作成&#40;アイコン用イメージ エディター&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  