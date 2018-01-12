---
title: "チュートリアル: SharePoint プロジェクトに対するカスタムの配置手順の作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 036f8d135e535547e9e5f790135186bf1f5728bc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects"></a>チュートリアル: SharePoint プロジェクトに対するカスタムの配置手順の作成
  SharePoint プロジェクトを展開するときに、Visual Studio は、特定の順序で一連の展開の手順を実行します。 Visual Studio には、多くの組み込みの配置手順が含まれていますが、独自に作成することもできます。  
  
 このチュートリアルでは、SharePoint を実行しているサーバー上でソリューションをアップグレードするカスタムの配置手順を作成します。 Visual Studio には、多くのタスク、そのような取り消しや追加、ソリューションを組み込みの配置手順が含まれていますが、ソリューションのアップグレード用の配置手順は含まれません。 既定では、SharePoint ソリューションを展開するときに Visual Studio 最初、ソリューションを取り消します (これは、既に展開されている場合) とし、ソリューション全体を再配置します。 組み込みの配置手順の詳細については、次を参照してください。[を展開する、発行、および SharePoint ソリューション パッケージのアップグレード](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)です。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   次の 2 つの主要タスクを実行する Visual Studio の拡張機能を作成する。  
  
    -   拡張機能では、SharePoint ソリューションをアップグレードするカスタムの配置手順を定義します。  
  
    -   拡張機能では、特定のプロジェクトに実行される配置手順のセットである新しい配置構成を定義するプロジェクトの拡張機能を作成します。 新しい展開の構成には、カスタムの配置手順といくつかの組み込みの配置手順が含まれています。  
  
-   拡張機能のアセンブリを呼び出す 2 つのカスタム SharePoint コマンドを作成します。 SharePoint コマンドは、SharePoint のサーバー オブジェクト モデルで Api を使用する拡張機能アセンブリを呼び出すことができるメソッドです。 詳細については、次を参照してください。[の SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)です。  
  
-   アセンブリの両方を展開する Visual Studio Extension (VSIX) パッケージを作成します。  
  
-   新しい配置手順をテストします。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   サポート対象エディションの Windows、SharePoint、Visual Studio。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   Visual Studio SDK。 このチュートリアルでは、 **VSIX プロジェクト**sdk、拡張機能を配置するための VSIX パッケージを作成するテンプレートです。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツール拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)です。  
  
 次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   For SharePoint サーバー オブジェクト モデルを使用します。 詳細については、次を参照してください。 [SharePoint Foundation サーバー側オブジェクト モデルを使用して](http://go.microsoft.com/fwlink/?LinkId=177796)です。  
  
-   SharePoint ソリューションです。 詳細については、次を参照してください。[ソリューションの概要](http://go.microsoft.com/fwlink/?LinkId=169422)です。  
  
-   SharePoint ソリューションをアップグレードします。 詳細については、次を参照してください。[ソリューションをアップグレード](http://go.microsoft.com/fwlink/?LinkId=177802)です。  
  
## <a name="creating-the-projects"></a>プロジェクトの作成  
 このチュートリアルを完了するには、3 つのプロジェクトを作成する必要があります。  
  
-   拡張機能を配置するための VSIX パッケージを作成する VSIX プロジェクト。  
  
-   拡張機能を実装するクラス ライブラリ プロジェクト。 このプロジェクトは、.NET Framework 4.5 を対象する必要があります。  
  
-   カスタムの SharePoint コマンドを定義するクラス ライブラリ プロジェクト。 このプロジェクトは、.NET Framework 3.5 を対象する必要があります。  
  
 この 2 つのプロジェクトを作成することから始めます。  
  
#### <a name="to-create-the-vsix-project"></a>VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#**または**Visual Basic** 、ノードを選択し、 **Extensibility**ノード。  
  
    > [!NOTE]  
    >  **Extensibility**ノードは、Visual Studio SDK をインストールする場合にのみ使用できます。 詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
4.  ダイアログ ボックスの上部には、次のように選択します。 **.NET Framework 4.5** 、.NET Framework のバージョンの一覧にします。  
  
5.  選択、 **VSIX プロジェクト**名では、プロジェクト テンプレートは、 **UpgradeDeploymentStep**を選択し、 **OK**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]追加、 **UpgradeDeploymentStep**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
#### <a name="to-create-the-extension-project"></a>拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**で UpgradeDeploymentStep ソリューション ノードのショートカット メニューを開き、**追加**を選択し**新しいプロジェクト**です。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#**または**Visual Basic** 、ノードを選択し、 **Windows**ノード。  
  
3.  ダイアログ ボックスの上部には、次のように選択します。 **.NET Framework 4.5** 、.NET Framework のバージョンの一覧にします。  
  
4.  選択、**クラス ライブラリ**プロジェクト テンプレートをプロジェクトに名前を**DeploymentStepExtension**を選択し、 **OK**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]追加、 **DeploymentStepExtension**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
#### <a name="to-create-the-sharepoint-command-project"></a>SharePoint コマンド プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**で UpgradeDeploymentStep ソリューション ノードのショートカット メニューを開き、**追加**を選択し**新しいプロジェクト**です。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開**Visual c#**または**Visual Basic**を選択し、 **Windows**ノード。  
  
3.  ダイアログ ボックスの上部には、次のように選択します。 **.NET Framework 3.5** 、.NET Framework のバージョンの一覧にします。  
  
4.  選択、**クラス ライブラリ**プロジェクト テンプレートをプロジェクトに名前を**SharePointCommands**を選択し、 **OK**ボタンをクリックします。  
  
     Visual Studio は追加、 **SharePointCommands**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
## <a name="configuring-the-projects"></a>プロジェクトの構成  
 カスタム配置手順を作成するコードを記述する前に、コード ファイルおよびアセンブリ参照を追加する必要があり、プロジェクトを構成する必要があります。  
  
#### <a name="to-configure-the-deploymentstepextension-project"></a>DeploymentStepExtension プロジェクトを構成するには  
  
1.  **DeploymentStepExtension**プロジェクトで、次の名前を持つ 2 つのコード ファイルを追加します。  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  DeploymentStepExtension プロジェクトのショートカット メニューを開き、選択**参照の追加**です。  
  
3.  **Framework**  タブで、System.ComponentModel.Composition アセンブリのチェック ボックスをオンにします。  
  
4.  **拡張機能**] タブ、Microsoft.VisualStudio.SharePoint アセンブリのチェック ボックスを選択し、[、 **OK**ボタンをクリックします。  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>SharePointCommands プロジェクトを構成するには  
  
1.  **SharePointCommands**プロジェクト、Commands というコード ファイルを追加します。  
  
2.  **ソリューション エクスプ ローラー**のショートカット メニューを開き、 **SharePointCommands**プロジェクト ノードをクリックして**参照の追加**です。  
  
3.  **拡張機能** タブで、次のアセンブリのチェック ボックスをオンをクリックして、 **OK**ボタン  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## <a name="defining-the-custom-deployment-step"></a>カスタムの配置手順を定義します。  
 アップグレードの配置手順を定義するクラスを作成します。 配置の手順で、クラスによって実装を定義する、<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>インターフェイスです。 カスタムの配置手順を定義するときに、このインターフェイスを実装します。  
  
#### <a name="to-define-the-custom-deployment-step"></a>カスタムの配置手順を定義するには  
  
1.  **DeploymentStepExtension**プロジェクト、UpgradeStep コード ファイルを開きに、次のコードを貼り付けます。  
  
    > [!NOTE]  
    >  このコードを追加する、プロジェクトは、一部のコンパイル エラーが解消されます後に追加するとコード後の手順で。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]  
  
## <a name="creating-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>展開構成を作成するカスタムの配置手順が含まれています  
 いくつかの組み込みの配置手順と、新しいデプロイのアップグレード手順が含まれていますの新しい展開構成のプロジェクトの拡張機能を作成します。 この拡張機能を作成するには、SharePoint プロジェクトで、アップグレードの展開の手順を使用する SharePoint 開発者が役立ちます。  
  
 デプロイ構成は、クラスによって実装を作成する、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>インターフェイスです。 SharePoint プロジェクトの拡張機能を作成するときに、このインターフェイスを実装します。  
  
#### <a name="to-create-the-deployment-configuration"></a>展開構成を作成するには  
  
1.  
  
2.  **DeploymentStepExtension**プロジェクト、DeploymentConfigurationExtension コード ファイルを開きに、次のコードを貼り付けます。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## <a name="creating-the-custom-sharepoint-commands"></a>カスタム SharePoint コマンドの作成  
 For SharePoint サーバー オブジェクト モデルを呼び出す 2 つのカスタム コマンドを作成します。 1 つのコマンドは、ソリューションが既に展開されているかどうかを決定します。その他のコマンドでは、ソリューションをアップグレードします。  
  
#### <a name="to-define-the-sharepoint-commands"></a>SharePoint コマンドを定義するには  
  
1.  **SharePointCommands**プロジェクト、Commands コード ファイルを開きを次のコードを貼り付けます。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]  
  
## <a name="checkpoint"></a>チェックポイント  
 この時点で、チュートリアルでは、カスタムの配置手順と SharePoint コマンドのすべてのコードが追加されて、プロジェクトでします。 エラーなしでコンパイルすることを確認するように構築します。  
  
#### <a name="to-build-the-projects"></a>プロジェクトをビルドするには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **DeploymentStepExtension**プロジェクトをクリックして**ビルド**です。  
  
2.  ショートカット メニューを開き、 **SharePointCommands**プロジェクトをクリックして**ビルド**です。  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>拡張機能を配置する VSIX パッケージの作成  
 拡張機能を配置するには、ソリューションで VSIX プロジェクトを使用して VSIX パッケージを作成します。 まず、VSIX プロジェクトの source.extension.vsixmanifest ファイルを変更することで、VSIX パッケージを構成します。 ソリューションをビルドして VSIX パッケージを作成します。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX パッケージを構成および作成するには  
  
1.  **ソリューション エクスプ ローラー**下で、 **UpgradeDeploymentStep**プロジェクトで、ショートカット メニューを開き、 **source.extension.vsixmanifest**ファイル、およびを選択**開いている**です。  
  
     Visual Studio によってマニフェスト エディターでファイルが開きます。 source.extension.vsixmanifest ファイルが、すべての VSIX パッケージで必要になる extension.vsixmanifest ファイルの基礎となります。 このファイルの詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)です。  
  
2.  **Product Name**ボックスに、入力**SharePoint プロジェクト用の配置手順のアップグレード**です。  
  
3.  **作成者**ボックスに、入力**Contoso**です。  
  
4.  **説明**ボックスに、入力**の SharePoint プロジェクトに使用できるカスタムのデプロイのアップグレード手順を提供**です。  
  
5.  **資産** タブ、エディターの選択、**新規**ボタンをクリックします。  
  
     **新しいアセットの追加** ダイアログ ボックスが表示されます。  
  
6.  **型**一覧で、選択**Microsoft.VisualStudio.MefComponent**です。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MefComponent` 要素に対応します。 この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。 詳細については、次を参照してください。 [MEFComponent 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)です。  
  
7.  **ソース**一覧で、選択**現在のソリューション内のプロジェクト**です。  
  
8.  **プロジェクト**一覧で、選択**DeploymentStepExtension**を選択し、 **OK**ボタンをクリックします。  
  
9. マニフェスト エディターで、選択、**新規**を再度クリックします。  
  
     **新しいアセットの追加** ダイアログ ボックスが表示されます。  
  
10. **型**一覧で、入力**SharePoint.Commands.v4**です。  
  
    > [!NOTE]  
    >  この要素は、Visual Studio 拡張機能に追加するカスタム拡張機能を指定します。 詳細については、次を参照してください。[資産要素 (VSX Schema)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737)です。  
  
11. **ソース**一覧で、選択**現在のソリューション内のプロジェクト**です。  
  
12. **プロジェクト**一覧で、選択**SharePointCommands**を選択し、 **OK**ボタンをクリックします。  
  
13. メニュー バーで、次のように選択します。**ビルド**、**ソリューションのビルド**、し、ソリューションがコンパイル エラーが発生しないことを確認します。  
  
14. UpgradeDeploymentStep プロジェクトのビルド出力フォルダーに今すぐ UpgradeDeploymentStep.vsix ファイルが含まれていることを確認してください。  
  
     既定では、ビルド出力フォルダーは ..\bin\Debug で、プロジェクト ファイルが格納されているフォルダーの下にあります。  
  
## <a name="preparing-to-test-the-upgrade-deployment-step"></a>デプロイのアップグレード手順をテストする準備をしています  
 アップグレードの配置手順をテストするには、最初、SharePoint サイトにサンプル ソリューションを配置する必要があります。 Visual Studio の実験用インスタンスで拡張機能のデバッグを開始します。 リストの定義および配置手順のテストに使用するリスト インスタンスを作成し、し、SharePoint サイトに展開します。 次に、リストの定義とリスト インスタンスを変更し、既定の展開プロセスが、SharePoint サイトでソリューションを上書きする方法を示すために再配置します。  
  
 このチュートリアルの後半でリストの定義とリスト インスタンスを変更しがそれらをアップグレードする SharePoint サイトでします。  
  
#### <a name="to-start-debugging-the-extension"></a>拡張機能のデバッグを開始するには  
  
1.  管理者の資格情報で Visual Studio を再起動し、UpgradeDeploymentStep ソリューションを開きます。  
  
2.  DeploymentStepExtension プロジェクトで UpgradeStep コード ファイルを開くし、コードの最初の行にブレークポイントを追加、`CanExecute`と`Execute`メソッドです。  
  
3.  選択して、F5 キーを選択して、または、メニュー バーでのデバッグを開始**デバッグ**、**デバッグの開始**です。  
  
4.  Visual Studio では、%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade 配置手順に SharePoint Projects\1.0 の拡張機能をインストールし、Visual Studio の実験用インスタンスを開始します。 Visual Studio のこのインスタンスでは、アップグレードの展開の手順をテストします。  
  
#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>リストの定義およびリスト インスタンスと共に SharePoint プロジェクトを作成するには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで、次のように選択します。**ファイル**、**新規**、**プロジェクト**です。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#**ノードまたは**Visual Basic**  ノードを展開、 **SharePoint**  ノードを選択し**2010**ノード。  
  
3.  ダイアログ ボックスの上部にあることを確認**.NET Framework 3.5** .NET Framework のバージョンの一覧に表示されます。  
  
     用にプロジェクト[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]と[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]このバージョンの .NET Framework を必要とします。  
  
4.  プロジェクト テンプレートの一覧で選択**SharePoint 2010 プロジェクト**、プロジェクトに名前を**EmployeesListDefinition**を選択し、 **OK**ボタンをクリックします。  
  
5.  **SharePoint カスタマイズ ウィザード**、デバッグに使用するサイトの URL を入力します。  
  
6.  **この SharePoint ソリューションの信頼レベルはどの**、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックします。  
  
    > [!NOTE]  
    >  アップグレードの配置手順は、サンド ボックス ソリューションをサポートしていません。  
  
7.  選択、**完了**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]EmployeesListDefinition プロジェクトを作成します。  
  
8.  EmployeesListDefinition プロジェクトのショートカット メニューを開き、選択**追加**を選択し**新しい項目の**します。  
  
9. **新しい項目の追加 - EmployeesListDefinition**  ダイアログ ボックスで、展開、 **SharePoint**  ノードを選択し、 **2010**ノード。  
  
10. 選択、**リスト**項目テンプレート、項目の名前**従業員一覧**を選択し、**追加**ボタンをクリックします。  
  
     SharePoint カスタマイズ ウィザードが表示されます。  
  
11. **一覧の設定を選択して** ページで、次の設定を確認しを選択し、**完了**ボタン。  
  
    1.  **従業員一覧**に表示されます、**リストの表示する名前?**ボックス。  
  
    2.  **に基づいてカスタマイズ可能なリストを作成する:**オプション ボタンを選択します。  
  
    3.  **既定値 (空白)**で選択された、**に基づいてカスタマイズ可能なリストを作成する:**  ボックスの一覧です。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]タイトルの列と 1 つの空のインスタンスで従業員のリスト項目を作成し、リスト デザイナーを開きます。  
  
12. デザイナーで、一覧で、**列** タブで、選択、**新規または既存の列名を入力**行を次の列を追加して、**列の表示名**一覧。  
  
    1.  名  
  
    2.  会社  
  
    3.  勤務先電話番号  
  
    4.  電子メール  
  
13. すべてのファイルを保存し、リスト デザイナーを閉じます。  
  
14. **ソリューション エクスプ ローラー**、展開、**従業員一覧**ノードの順に展開し、**従業員のリスト インスタンス**子ノードです。  
  
15. Elements.xml ファイルに、このファイルの既定の XML を次の XML に置き換えます。 この XML にリストの名前を変更する**従業員**佐藤直樹という名前を持つ従業員の情報を追加します。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
        <Data>  
          <Rows>  
            <Row>  
              <Field Name="Title">Hance</Field>  
              <Field Name="FirstName">Jim</Field>  
              <Field Name="Company">Contoso</Field>  
              <Field Name="Business Phone">555-555-5555</Field>  
              <Field Name="E-Mail">jim@contoso.com</Field>  
            </Row>  
          </Rows>  
        </Data>  
      </ListInstance>  
    </Elements>  
    ```  
  
16. 保存して、Elements.xml ファイルを閉じます。  
  
17. EmployeesListDefinition プロジェクトのショートカット メニューを開き、選択**開く**または**プロパティ**です。  
  
     プロパティのデザイナーが開きます。  
  
18. **SharePoint**タブで、、**デバッグ後に自動取り消し**チェック ボックスをオンし、プロパティを保存します。  
  
#### <a name="to-deploy-the-list-definition-and-list-instance"></a>リストの定義とリスト インスタンスを展開するには  
  
1.  **ソリューション エクスプ ローラー**、選択、 **EmployeesListDefinition**プロジェクト ノードです。  
  
2.  **プロパティ**ウィンドウ、ことを確認して、**アクティブな配置構成**プロパティに設定されている**既定**です。  
  
3.  F5 キーを押すか、メニュー バーで、次のように選択します。**デバッグ**、**デバッグの開始**です。  
  
4.  プロジェクトが正常にビルドされる、SharePoint サイトに web ブラウザーを開くことを確認する、**を一覧表示**クイック起動バー内の項目が含まれていますが、新しい**従業員** ボックスの一覧と、 **従業員**佐藤直樹のエントリが一覧に含まれています。  
  
5.  Web ブラウザーを閉じます。  
  
#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>リストの定義とリスト インスタンスを変更し、再展開します。  
  
1.  EmployeesListDefinition プロジェクト内の子である Elements.xml ファイルを開き、**従業員のリスト インスタンス**プロジェクト項目です。  
  
2.  削除、`Data`要素とその子の一覧から佐藤直樹のエントリを削除します。  
  
     完了したら、ファイルは、次の XML を含める必要があります。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  保存して、Elements.xml ファイルを閉じます。  
  
4.  ショートカット メニューを開き、**従業員一覧**プロジェクト項目をクリックして**開く**または**プロパティ**です。  
  
5.  デザイナーで、リストを選択して、**ビュー**タブです。  
  
6.  **選択した列**一覧で、選択**添付ファイル**を選択し、< キーには、その列を移動する、**使用可能な列**リスト。  
  
7.  移動する前の手順を繰り返して、**勤務先電話番号**から列、**列を選択**の一覧を表示、**使用可能な列** ボックスの一覧。  
  
     この操作の既定のビューからのこれらのフィールドの削除、**従業員**SharePoint サイト上のリスト。  
  
8.  選択して、F5 キーを選択して、または、メニュー バーでのデバッグを開始**デバッグ**、**デバッグの開始**です。  
  
9. いることを確認、**配置競合** ダイアログ ボックスが表示されます。  
  
     このダイアログ ボックスでは、ソリューション (リスト インスタンス) を展開する際に Visual Studio をそのソリューションが既に展開済みの SharePoint サイトに表示されます。 このチュートリアルで後で、アップグレードの展開の手順を実行するときに、このダイアログ ボックスは表示されません。  
  
10. **配置競合** ダイアログ ボックスで、選択、**を自動的に解決**オプション ボタンをクリックします。  
  
     Visual Studio、SharePoint サイト上のリスト インスタンスを削除するには、プロジェクトで、リスト項目を展開および SharePoint サイトを開きます。  
  
11. **一覧**セクション、サイド バーの選択、**従業員**ボックスの一覧を次の詳細を確認してください。  
  
    -   **添付ファイル**と**自宅電話番号**一覧のこのビュー内の列に表示されません。  
  
    -   リストが空です。 使用したときに、**既定**、ソリューションを再配置する配置の構成、**従業員**一覧は、プロジェクトに新しい空のリストに置き換えられました。  
  
## <a name="testing-the-deployment-step"></a>配置手順のテスト  
 デプロイのアップグレード手順をテストする準備が整いました。 最初に、SharePoint でリスト インスタンスに項目を追加します。 リストの定義とリスト インスタンスを変更、SharePoint サイトでそれらをアップグレードおよびアップグレードの配置手順が、新しい項目を上書きしないことを確認します。  
  
#### <a name="to-manually-add-an-item-to-the-list"></a>一覧に項目を手動で追加するには  
  
1.  SharePoint サイトで、リボンの下にある、**リスト ツール** タブで、選択、**項目**タブです。  
  
2.  **新規**グループで、選択**新しい項目の**します。  
  
     代わりを選択できます、**新しい項目の追加**項目一覧自体にリンクします。  
  
3.  **従業員 - 新しいアイテム**ウィンドウで、**タイトル**ボックスに、入力**設備マネージャー**です。  
  
4.  **名**ボックスに、入力**Andy**です。  
  
5.  **会社**ボックスに、入力**Contoso**です。  
  
6.  選択、**保存**ボタンをクリックし、一覧で、新しい項目が表示されることを確認し、web ブラウザーを閉じます。  
  
     このチュートリアルで後では、この項目を使用して、デプロイのアップグレード手順がこの一覧の内容を上書きしないことを確認してください。  
  
#### <a name="to-test-the-upgrade-deployment-step"></a>デプロイのアップグレード手順をテストするには  
  
1.  Visual Studio の実験用インスタンスで**ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **EmployeesListDefinition**プロジェクト ノードをクリックして**プロパティ**.  
  
     プロパティ エディターとデザイナーが開きます。  
  
2.  **SharePoint**  タブで、設定、**アクティブな配置構成**プロパティを**アップグレード**です。  
  
     このカスタムの配置構成には、新しいデプロイのアップグレード手順が含まれています。  
  
3.  ショートカット メニューを開き、**従業員一覧**プロジェクト項目をクリックして**プロパティ**または**開く**です。  
  
     プロパティ エディターとデザイナーが開きます。  
  
4.  **ビュー**  タブで、選択、**電子メール** 列を選択し、  **<** キーから列を移動する、 **の列を選択**の一覧を表示、**使用可能な列** ボックスの一覧です。  
  
     この操作の既定のビューからのこれらのフィールドの削除、**従業員**SharePoint サイト上のリスト。  
  
5.  選択して、F5 キーを選択して、または、メニュー バーでのデバッグを開始**デバッグ**、**デバッグの開始**です。  
  
6.  Visual Studio のもう一方のインスタンスで、先ほど `CanExecute` メソッドに設定したブレークポイントで、コードが停止していることを確認します。  
  
7.  F5 キーをもう一度押すか、メニュー バーで、次のように選択します。**デバッグ**、**続行**です。  
  
8.  コードの前に設定したブレークポイントで停止することを確認、`Execute`メソッドです。  
  
9. F5 キーを押すか、メニュー バーで、次のように選択します。**デバッグ**、**続行**最終時刻。  
  
     Web ブラウザーでは、SharePoint サイトが開きます。  
  
10. **を一覧表示**セクションで、クイック起動領域の選択、**従業員**ボックスの一覧を次の詳細を確認してください。  
  
    -   以前 (Andy、設備マネージャー) を手動で追加した項目はリストです。  
  
    -   **勤務先電話番号**と**電子メール アドレス**一覧のこのビュー内の列に表示されません。  
  
     **アップグレード**展開構成の変更、既存**従業員**SharePoint サイト上のリスト インスタンス。 使用した場合、**既定**展開構成の代わりに、**アップグレード**構成では、配置の競合は発生します。 Visual Studio は置き換えることで、競合を解決すると、**従業員**リスト、および Andy、設備マネージャーの項目が削除されてしまいます。  
  
## <a name="cleaning-up-the-development-computer"></a>開発コンピューターのクリーンアップ  
 テストのアップグレードの展開手順が完了したらは、SharePoint サイトから、リスト インスタンスとリストの定義を削除し、Visual Studio から展開手順の拡張機能を削除します。  
  
#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>SharePoint サイトから、リスト インスタンスを削除するには  
  
1.  開く、**従業員**リストがまだ開いていない場合、SharePoint サイトで一覧表示します。  
  
2.  リボンでは、SharePoint サイトで、選択、**リスト ツール** タブをクリックして、**リスト** タブ。  
  
3.  **設定**グループで、選択、**一覧の設定**項目。  
  
4.  **権限と管理**、選択、**このリストの削除**コマンドを選択**OK**ごみ箱に一覧を送信し、web を終了することを確認ブラウザー。  
  
#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>SharePoint サイトから、リスト定義を削除するには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで、次のように選択します。**ビルド**、 **Retract**です。  
  
     Visual Studio には、SharePoint サイトから、リスト定義が取り消されます。  
  
#### <a name="to-uninstall-the-extension"></a>拡張機能をアンインストールするには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで、次のように選択します。**ツール**、**拡張機能と更新プログラム**です。  
  
     **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で選択**SharePoint プロジェクト用の配置手順のアップグレード**を選択し、**アンインストール**コマンド。  
  
3.  ダイアログ ボックスが表示されますが、選択**はい**、拡張機能をアンインストールし、選択することを確認**今すぐ再起動**してアンインストールを完了します。  
  
4.  Visual Studio (実験用インスタンスおよび UpgradeDeploymentStep ソリューションが開いている Visual Studio のインスタンス) の両方のインスタンスを閉じます。  
  
## <a name="see-also"></a>参照  
 [SharePoint のパッケージ化と配置の拡張](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  