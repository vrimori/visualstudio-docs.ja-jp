---
title: "Walkthrough: Creating a Custom Deployment Step for SharePoint Projects"
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
  - "SharePoint commands"
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 4ba2d120-06b8-4ef3-84eb-c6c50ced9d82
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Walkthrough: Creating a Custom Deployment Step for SharePoint Projects
  SharePointプロジェクトを配置する場合、Visual Studioは、特定の順序で一連の配置手順が実行されます。  Visual Studio には、さまざまな組み込みの配置手順が用意されていますが、配置手順を独自に作成することもできます。  
  
 このチュートリアルでは、SharePointで実行しているサーバーのソリューションをアップグレードするカスタムの配置手順を作成します。  Visual Studioは、多くのタスク、このような取り消すか、または追加ソリューションの組み込みの配置手順が含まれますが、ソリューションをアップグレードするための配置手順が含まれていません。  SharePointソリューションを配置すると、既定では、Visual Studioは、まずソリューション \(既に配置されている場合\) 取り消し、ソリューション全体を再配置します。  組み込みの配置手順の詳細については、「[SharePoint ソリューションのパッケージの配置、発行、アップグレード](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)」を参照してください。  
  
 このチュートリアルでは、次のタスクを実行します。  
  
-   次の 2 つの主要タスクを実行する Visual Studio の拡張機能を作成する。  
  
    -   拡張機能では、SharePointソリューションのアップグレードするカスタムの配置手順を定義します。  
  
    -   拡張子は、特定のプロジェクトについて実行される一連の配置手順ですが、新しい配置構成を定義する、プロジェクトの拡張機能を作成します。  新しい配置構成には、カスタムの配置手順と、いくつかの組み込みの配置手順が含まれます。  
  
-   拡張機能アセンブリが呼び出す2とおりのカスタムSharePointコマンドを作成します。  SharePointコマンドは、SharePointのサーバー オブジェクト モデルのAPIを使用する拡張機能のアセンブリから呼び出すことのできるメソッドです。  詳細については、「[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)」を参照してください。  
  
-   両方のアセンブリを配置するための Visual Studio Extension \(VSIX\) パッケージを構築する。  
  
-   新しい配置手順をテストする。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   Windows SharePoint、およびサポートされるVisual Studioのエディション。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   Visual Studio SDK。  このチュートリアルでは、拡張機能を配置するための VSIX パッケージを、SDK の **VSIX プロジェクト** テンプレートを使用して作成します。  詳細については、「[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
 次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   SharePointのサーバー オブジェクト モデルの使用。  詳細については、「[Using the SharePoint Foundation Server\-Side Object Model \(SharePoint Foundation Server 側オブジェクト モデルの使用\)](http://go.microsoft.com/fwlink/?LinkId=177796)」を参照してください。  
  
-   SharePoint ソリューション。  詳細については、「[Solutions Overview \(ソリューションの概要\)](http://go.microsoft.com/fwlink/?LinkId=169422)」を参照してください。  
  
-   SharePoint ソリューションのアップグレード。  詳細については、「[Upgrading a Solution \(ソリューションのアップグレード\)](http://go.microsoft.com/fwlink/?LinkId=177802)」を参照してください。  
  
## プロジェクトの作成  
 このチュートリアルを完了するには、3種類のプロジェクトを作成する必要があります:  
  
-   拡張機能を配置するために VSIX パッケージを作成する VSIX プロジェクト。  
  
-   プロジェクトの拡張機能を実装するクラス ライブラリ プロジェクト。  このプロジェクトが.NET Framework 4.5を対象とする必要があります。  
  
-   カスタムの SharePoint コマンドを定義するクラス ライブラリ プロジェクト。  このプロジェクトが.NET Framework 3.5を対象とする必要があります。  
  
 この 2 つのプロジェクトを作成することから始めます。  
  
#### VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで **\[ファイル\]**、**\[新規\]**、**\[プロジェクト\]** の順にクリックします。  
  
3.  **\[新しいプロジェクト\]** のダイアログ ボックスで、**\[Visual C\#\]** または **\[Visual Basic\]** のノードを展開し、**\[機能拡張\]** のノードを選択します。  
  
    > [!NOTE]  
    >  **\[機能拡張\]** のノードは、Visual Studio SDKをインストールするときだけです。  詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
4.  ダイアログ ボックスの上部に、.NET Frameworkのバージョンの **\[.NET Framework 4.5\]** リストのを選択します。  
  
5.  **\[VSIX プロジェクト\]** テンプレートを選択し、プロジェクト **\[UpgradeDeploymentStep\]**を付けておくと、**\[OK\]** のボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の**ソリューション エクスプローラー**に **UpgradeDeploymentStep** プロジェクトが追加されます。  
  
#### 拡張機能プロジェクトを作成するには  
  
1.  **\[ソリューション エクスプローラー\]**では、UpgradeDeploymentStepソリューション ノードのショートカット メニューを開き、**\[追加\]**を選択し、を **\[新しいプロジェクト\]**を選択します。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトで**ソリューション エクスプローラー**にソリューション ノードが表示されるのは、[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/ja-jp/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)の **\[常にソリューションを表示\]** チェック ボックスがオンになっている場合だけです。  
  
2.  **\[新しいプロジェクト\]** のダイアログ ボックスで、**\[Visual C\#\]** または **\[Visual Basic\]** のノードを展開し、**\[ウィンドウ\]** のノードを選択します。  
  
3.  ダイアログ ボックスの上部に、.NET Frameworkのバージョンの **\[.NET Framework 4.5\]** リストのを選択します。  
  
4.  **\[クラス ライブラリ\]** のプロジェクト テンプレートを選択し、プロジェクト **\[DeploymentStepExtension\]**を付けておくと、**\[OK\]** のボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって、**DeploymentStepExtension** プロジェクトがソリューションに追加され、既定の Class1 コード ファイルが開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
#### SharePoint コマンド プロジェクトを作成するには  
  
1.  **\[ソリューション エクスプローラー\]**では、UpgradeDeploymentStepソリューション ノードのショートカット メニューを開き、**\[追加\]**を選択し、を **\[新しいプロジェクト\]**を選択します。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトで**ソリューション エクスプローラー**にソリューション ノードが表示されるのは、[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/ja-jp/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)の **\[常にソリューションを表示\]** チェック ボックスがオンになっている場合だけです。  
  
2.  **\[新しいプロジェクト\]** のダイアログ ボックスで、**\[Visual C\#\]** か **\[Visual Basic\]**を展開し、**\[ウィンドウ\]** のノードを選択します。  
  
3.  ダイアログ ボックスの上部に、.NET Frameworkのバージョンの **\[.NET Framework 3.5\]** リストのを選択します。  
  
4.  **\[クラス ライブラリ\]** のプロジェクト テンプレートを選択し、プロジェクト **\[SharePointCommands\]**を付けておくと、**\[OK\]** のボタンをクリックします。  
  
     ソリューションに **SharePointCommands** プロジェクトが追加され、既定の Class1 コード ファイルが開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
## プロジェクトの構成  
 カスタムの配置手順を作成するためのコードを記述する前に、コード ファイルおよびアセンブリ参照を追加してプロジェクトを構成する必要があります。  
  
#### DeploymentStepExtension プロジェクトを構成するには  
  
1.  **\[DeploymentStepExtension\]** のプロジェクトでは、次の名前を持つ2種類のコード ファイルを追加します:  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  DeploymentStepExtensionプロジェクトのショートカット メニューを開き、**\[参照の追加\]**を選択します。  
  
3.  **\[Framework\]** のタブで、System.ComponentModel.Compositionアセンブリのチェック ボックスをオンにします。  
  
4.  **\[拡張機能\]** のタブで、Microsoft.VisualStudio.SharePointアセンブリのチェック ボックスをオンにし、**\[OK\]** のボタンをクリックします。  
  
#### SharePointCommands プロジェクトを構成するには  
  
1.  **\[SharePointCommands\]** のプロジェクトでは、Commandsという名前のコード ファイルを追加します。  
  
2.  **\[ソリューション エクスプローラー\]**では、**\[SharePointCommands\]** のプロジェクト ノードのショートカット メニューを開き、**\[参照の追加\]**を選択します。  
  
3.  **\[拡張機能\]** のタブで、次のアセンブリのチェック ボックスをオンにし、を選択します **\[OK\]** のボタンをクリックします。  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## カスタムの配置手順の定義  
 アップグレードの配置手順を定義するクラスを作成します。  配置手順を定義するため、このクラスに <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> インターフェイスを実装します。  このインターフェイスは、カスタムの配置手順を定義する場合に必ず実装します。  
  
#### カスタムの配置手順を定義するには  
  
1.  **\[DeploymentStepExtension\]** のプロジェクトでは、UpgradeStepコード ファイルを開き、そのファイルに次のコードを貼り付けます。  
  
    > [!NOTE]  
    >  このコードを追加すると、いくつかのコンパイル エラーがありますが、後の手順のコードを追加すると解消されます。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/upgradestep.vb#1)]  
  
## カスタムの配置手順を含んだ配置構成の作成  
 いくつかの組み込みの配置手順と新しいアップグレードの配置手順を含んだ新しい配置構成のプロジェクトの拡張機能を作成します。  この拡張機能を作成することにより、SharePoint開発者がSharePointプロジェクトにアップグレードの配置手順を使用できます。  
  
 配置構成を作成するため、このクラスに <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> インターフェイスを実装します。  このインターフェイスは、SharePoint プロジェクトの拡張機能を作成する場合に必ず実装します。  
  
#### 配置構成を作成するには  
  
1.  **\[DeploymentStepExtension\]** のプロジェクトでは、DeploymentConfigurationExtensionコード ファイルを開き、そのファイルに次のコードを貼り付けます。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## カスタム SharePoint コマンドの作成  
 SharePointのサーバー オブジェクト モデルを呼び出す2とおりのカスタム コマンドを作成します。  1 つはソリューションが配置済みかどうかを判断するコマンドで、もう 1 つはソリューションをアップグレードするコマンドです。  
  
#### SharePoint コマンドを定義するには  
  
1.  **\[SharePointCommands\]** のプロジェクトのCommandsコード ファイルを開き、そのファイルに次のコードを貼り付けます。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/sharepointcommands/commands.vb#4)]  
  
## チェックポイント  
 この段階で、カスタムの配置手順および SharePoint コマンドに必要なすべてのコードがプロジェクトに揃ったことになります。  これらはコンパイル エラーが発生しないことを確認するために、それらをビルドします。  
  
#### プロジェクトをビルドするには  
  
1.  **\[ソリューション エクスプローラー\]**では、**\[DeploymentStepExtension\]** のプロジェクトのショートカット メニューを開き、**\[ビルド\]**を選択します。  
  
2.  **\[SharePointCommands\]** のプロジェクトのショートカット メニューを開き、**\[ビルド\]**を選択します。  
  
## 拡張機能を配置するための VSIX パッケージの作成  
 拡張機能を配置するには、ソリューションで VSIX プロジェクトを使用して VSIX パッケージを作成します。  まず、VSIXプロジェクトのsource.extension.vsixmanifestファイルを変更して、VSIXパッケージを構成します。  ソリューションをビルドしてVSIXパッケージを作成します。  
  
#### VSIX パッケージを構成および作成するには  
  
1.  **\[ソリューション エクスプローラー\]**では、**\[UpgradeDeploymentStep\]** のプロジェクトの下で、を開き、**\[source.extension.vsixmanifest\]** ファイルのショートカット メニューで、を **\[開く\]**を選択します。  
  
     Visual Studio によってマニフェスト エディターでファイルが開きます。  source.extension.vsixmanifestファイルは、すべてのVSIXパッケージが必要とするextension.vsixmanifestファイルの基礎です。  このファイルの詳細については、「[VSIX 拡張機能のスキーマに関するリファレンス](http://msdn.microsoft.com/ja-jp/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)」を参照してください。  
  
2.  **\[製品名\]** ボックスに、**\[Upgrade Deployment Step for SharePoint Projects\]**を入力します。  
  
3.  **\[作成者\]** ボックスに、**\[Contoso\]**を入力します。  
  
4.  **\[説明\]** ボックスに、**SharePointプロジェクトで使用できるカスタム アップグレードの配置手順が用意されています。**を入力します。  
  
5.  エディターの **\[資産\]** のタブで、**\[新規作成\]** のボタンをクリックします。  
  
     **\[新しい資産の追加\]** のダイアログ ボックスが表示されます。  
  
6.  **\[種類\]** の一覧で、**\[Microsoft.VisualStudio.MefComponent\]**を選択します。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MefComponent` 要素に対応します。  この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。  詳細については、「[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/ja-jp/8a813141-8b73-44c9-b80b-ca85bbac9551)」を参照してください。  
  
7.  **\[ソース\]** の一覧で、**\[現在のソリューション内のプロジェクト\]**を選択します。  
  
8.  **\[プロジェクト\]** の一覧で、**\[DeploymentStepExtension\]**を選択し、**\[OK\]** のボタンをクリックします。  
  
9. マニフェスト エディターで、**\[新規作成\]** のボタンをもう一度クリックします。  
  
     **\[新しい資産の追加\]** のダイアログ ボックスが表示されます。  
  
10. **\[種類\]** の一覧で、**\[SharePoint.Commands.v4\]**を入力します。  
  
    > [!NOTE]  
    >  Visual Studio の拡張機能に追加するカスタム拡張機能は、この要素によって指定されます。  詳細については、「[資産の要素 \(VSX スキーマ\)](http://msdn.microsoft.com/ja-jp/9fcfc098-edc7-484b-9d4c-acd17829d737)」を参照してください。  
  
11. **\[ソース\]** の一覧で、**\[現在のソリューション内のプロジェクト\]**を選択します。  
  
12. **\[プロジェクト\]** の一覧で、**\[SharePointCommands\]**を選択し、**\[OK\]** のボタンをクリックします。  
  
13. メニュー バーで、**\[ビルド\]**、**\[ソリューションのビルド\]**を選択し、次に、ソリューションのエラーなしでコンパイルしてください。  
  
14. UpgradeDeploymentStepプロジェクトのビルド出力フォルダーにUpgradeDeploymentStep.vsixファイルが含まれていることを確認します。  
  
     既定では、プロジェクト ファイルに格納されているフォルダー  の ..\\bin\\Debug フォルダーがビルド出力フォルダーです。  
  
## アップグレードの配置手順をテストする準備  
 アップグレードの配置手順をテストするために、まず、SharePoint サイトにサンプル ソリューションを配置する必要があります。  まず、Visual Studio の実験用インスタンスで拡張機能のデバッグを開始します。  次に、リスト定義を作成し、配置手順をテストするようにインスタンスを示します。次に、SharePointサイトに配置します。  次に、リスト定義を変更して、そのインスタンスが一覧表示され、既定の配置プロセスではSharePointサイトのソリューションにどのように上書きするかを示すには、変更を加えて再配置します。  
  
 このチュートリアルで後で、リスト定義とリスト インスタンスを変更し、SharePointサイトでアップグレードします。  
  
#### 拡張機能のデバッグを開始するには  
  
1.  管理資格情報を使用してVisual Studioを再起動し、UpgradeDeploymentStepソリューションを開きます。  
  
2.  DeploymentStepExtensionプロジェクトで、UpgradeStepコード ファイルを開き、`CanExecute` と `Execute` のメソッドのコードの先頭行にブレークポイントを追加します。  
  
3.  F5キーのまたはを選択する **\[デバッグ\]**、メニュー バーのをクリックしてデバッグを開始した **\[デバッグの開始\]**。  
  
4.  Visual Studioは、SharePoint Projects\\1.0の%UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Upgradeの配置手順に拡張機能をインストール、Visual Studioの実験用インスタンスを起動します。  Visual Studioのアップグレードの配置手順をテストします。この場合  
  
#### リスト定義とリストでSharePointプロジェクトを作成するには、この例に付けます。  
  
1.  Visual Studioの実験用インスタンスで、メニュー バーで、**\[ファイル\]**、**\[新規作成\]**、**\[プロジェクト\]**を選択します。  
  
2.  **\[新しいプロジェクト\]** のダイアログ ボックスで、**\[Visual C\#\]** の **\[Visual Basic\]** のノードまたはノードを展開し、**\[SharePoint\]** のノードを展開し、を **\[2010\]** のノードを選択します。  
  
3.  ダイアログ ボックスの上部に、**\[.NET Framework 3.5\]** が.NET Framework Versionの一覧に表示されることを確認します。  
  
     [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] および [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] のプロジェクトには、このバージョンの .NET Framework が必要です。  
  
4.  プロジェクト テンプレートの一覧で、**\[SharePoint 2010 プロジェクト\]**を選択し、プロジェクト **\[EmployeesListDefinition\]**を付けておくと、**\[OK\]** のボタンをクリックします。  
  
5.  **\[SharePoint カスタマイズ ウィザード\]**で、デバッグに使用するサイトのURLを入力します。  
  
6.  **\[What is the trust level for this SharePoint solution\]**の下に、**\[ファーム ソリューションとして配置する\]** のオプション ボタンを選択します。  
  
    > [!NOTE]  
    >  アップグレードの配置手順がサンドボックス ソリューションをサポートしていません。  
  
7.  **\[完了\]** のボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] はEmployeesListDefinitionプロジェクトを作成します。  
  
8.  EmployeesListDefinitionプロジェクトのショートカット メニューを開き、**\[追加\]**を選択し、を **\[新しい項目\]**を選択します。  
  
9. **\[新しい項目– EmployeesListDefinitionを追加します。\]** のダイアログ ボックスで、**\[SharePoint\]** のノードを展開し、**\[2010\]** のノードを選択します。  
  
10. **\[一覧\]** の項目テンプレートを選択し、項目 **\[Employees List\]**を付けておくと、**\[追加\]** のボタンをクリックします。  
  
     SharePointカスタマイズ ウィザードが表示されます  
  
11. **\[リストの設定を選択\]** のページに次の設定を確認し、**\[完了\]** のボタンを選択する:  
  
    1.  **\[Employees List\]** は **\[リストに表示する名前\]** ボックスに表示されます。  
  
    2.  **\[Create a customizable list based on:\]** のオプション ボタンが選択されます。  
  
    3.  **\[既定値 \(null\)\]** は **\[Create a customizable list based on:\]** の一覧で選択されます。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] はタイトル列を持つ従業員一覧の項目を作成し、単一インスタンスはデザイナーで開くリストを空にします。  
  
12. リストのデザイナーで、**\[列\]** のタブで、**\[新規または既存の列名を入力します\]** の行を選択し、**\[列の表示名\]** の一覧の次の列を追加します:  
  
    1.  \[名\]  
  
    2.  \[会社\]  
  
    3.  \[会社電話番号\]  
  
    4.  \[電子メール\]  
  
13. すべてのファイルを保存し、リストのデザイナーを閉じます。  
  
14. **\[ソリューション エクスプローラー\]**では、**\[Employees List\]** のノードを展開し、**\[Employees List Instance\]** の子ノードを展開します。  
  
15. Elements.xmlファイルで、次のXMLにこのファイルの既定XMLに置き換えます。  このXMLは **\[従業員\]** にリストの名前を変更し、Jim Hanceの従業員の情報を追加します。  
  
    ```  
  
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
  
16. Elements.xmlファイルを保存して閉じます。  
  
17. EmployeesListDefinitionプロジェクトのショートカット メニューを開き、**\[開く\]** か **\[プロパティ\]**を選択します。  
  
     プロパティのデザイナーが開きます。  
  
18. **\[SharePoint\]** のタブで、**\[デバッグ後に自動取り消し\]** のチェック ボックスをオフにし、プロパティを保存します。  
  
#### リスト定義とリスト インスタンスを配置するには  
  
1.  **\[ソリューション エクスプローラー\]**では、**\[EmployeesListDefinition\]** のプロジェクト ノードを選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、**\[アクティブな配置構成\]** プロパティが **\[既定\]** に設定されていることを確認します。  
  
3.  F5キーをまたはで、メニュー バーのをクリックするか、**\[デバッグ\]**、**\[デバッグの開始\]**を選択します。  
  
4.  のクイック起動バーの **\[リスト\]** の項目が **\[従業員\]** の新しいリストを含むこと、および **\[従業員\]** の一覧がJim Hanceのエントリが含まれることをWebブラウザーがSharePointサイトに開くとプロジェクトが正常にビルドして確認してください。  
  
5.  Webブラウザーを閉じます。  
  
#### リスト定義とリスト インスタンスに変更を加えて再配置するには  
  
1.  EmployeesListDefinitionプロジェクトで、**\[Employee List Instance\]** プロジェクト項目の子であるElements.xmlファイルを開きます。  
  
2.  `Data` 要素とその子を削除し、リストから Jim Hance のエントリを削除します。  
  
     終了すると、ファイルは次のXMLを含める必要があります。  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  Elements.xmlファイルを保存して閉じます。  
  
4.  **\[Employees List\]** プロジェクト項目に対するショートカット メニューを開き、**\[開く\]** か **\[プロパティ\]**を選択します。  
  
5.  リストのデザイナーで、**\[ビュー\]** のタブをクリックします。  
  
6.  **\[選択された列\]** の一覧で、**\[添付ファイル\]**を選択し、\< **\[使用可能な列\]** の一覧に移動キー列を選択します。  
  
7.  **\[選択された列\]** の一覧から **\[使用可能な列\]** の一覧に **\[会社電話番号\]** の列を移動するには、前の手順を繰り返します。  
  
     SharePoint サイトの **Employees** リストの既定の表示から、これらのフィールドが削除されます。  
  
8.  F5キーのまたはを選択する **\[デバッグ\]**、メニュー バーのをクリックしてデバッグを開始した **\[デバッグの開始\]**。  
  
9. **\[配置競合\]** ダイアログ ボックスが表示されます。  
  
     このダイアログ ボックスは、Visual Studioがそのソリューションが配置されているSharePointサイトにソリューション \(リスト インスタンス\) を配置しようとすると表示されます。  このダイアログ ボックスでは、このチュートリアルのアップグレードの配置手順を実装するされません。  
  
10. **\[配置競合\]** のダイアログ ボックスで、**\[自動的に解決\]** のオプション ボタンを選択します。  
  
     Visual Studioは、SharePointサイトのリスト インスタンスを削除し、プロジェクト リスト項目を展開して、SharePointサイトが開きます。  
  
11. のクイック起動バーの **\[リスト\]** のセクションでは、**\[従業員\]** のリストをクリックし、次の事項を確認する:  
  
    -   **\[添付ファイル\]** とは **\[自宅電話番号\]** の列がこのリストのビューに表示されません。  
  
    -   リストは空です。  **既定**の配置構成を使用してソリューションを再配置した場合、**Employees** リストが、プロジェクト内の新しい空のリストに置き換えられます。  
  
## 配置手順のテスト  
 これで、アップグレードの配置手順をテストする準備ができました。  まず、SharePoint でリスト インスタンスに項目を追加します。  次に、リスト定義を変更して、インスタンスを一覧し、SharePointサイトでアップグレードし、アップグレードの配置手順が新しい項目が上書きします。  
  
#### リストに手動で項目を追加するには  
  
1.  SharePointサイトのリボンで、**\[リスト ​​ツール\]** のタブで、**\[項目\]** のタブをクリックします。  
  
2.  **\[新規作成\]** のグループで、**\[新しい項目\]**を選択します。  
  
     別の方法として、項目のリストの **\[新しい項目の追加\]** 自体のリンクを選択できます。  
  
3.  **\[従業員–の新しい項目\]** のペインで、**\[タイトル\]** ボックスに、**機能マネージャー**を入力します。  
  
4.  **\[名\]** ボックスに、**アンディー**を入力します。  
  
5.  **\[会社\]** ボックスに、**\[Contoso\]**を入力します。  
  
6.  **\[保存\]** のボタンを選択し、新しい項目がリストに表示される確認し、Webブラウザーを閉じます。  
  
     後の手順で、アップグレードの配置手順では、このリストの内容を上書きしないことを確認するために、この項目を使用します。  
  
#### アップグレードの配置手順をテストするには  
  
1.  Visual Studioの実験用インスタンスで、**\[ソリューション エクスプローラー\]**で、を開き、**\[EmployeesListDefinition\]** のプロジェクト ノードのショートカット メニューで、を **\[プロパティ\]**を選択します。  
  
     プロパティ エディターまたはデザイナーが開きます。  
  
2.  **\[SharePoint\]** のタブで、**\[アップグレード\]**に **\[アクティブな配置構成\]** のプロパティを設定します。  
  
     このカスタムの配置構成には、新しいアップグレードの配置手順が含まれます。  
  
3.  **\[Employees List\]** プロジェクト項目に対するショートカット メニューを開き、**\[プロパティ\]** か **\[開く\]**を選択します。  
  
     プロパティ エディターまたはデザイナーが開きます。  
  
4.  **\[ビュー\]** のタブで、**\[電子メール\]** の列を選択し、**\[選択された列\]** の一覧から **\[使用可能な列\]** の一覧に列を移動することに **\[\<\]** のキーを選択します。  
  
     SharePoint サイトの **Employees** リストの既定の表示から、これらのフィールドが削除されます。  
  
5.  F5キーのまたはを選択する **\[デバッグ\]**、メニュー バーのをクリックしてデバッグを開始した **\[デバッグの開始\]**。  
  
6.  Visual Studio のもう一方のインスタンスで、先ほど `CanExecute` メソッドに設定したブレークポイントで、コードが停止していることを確認します。  
  
7.  F5キーをまたはで、メニュー バーで再度選択するか、**\[デバッグ\]**、**\[続行\]**を選択します。  
  
8.  先ほど `Execute` メソッドに設定したブレークポイントで、コードが停止していることを確認します。  
  
9. F5キーをまたはで、メニュー バーのをクリックするか、**\[デバッグ\]**、最終的な時間 **\[続行\]** を選択します。  
  
     WebブラウザーでSharePointサイトが開きます。  
  
10. クイック起動領域の **\[リスト\]** のセクションでは、**\[従業員\]** のリストをクリックし、次の事項を確認する:  
  
    -   は、手動で前に追加した項目には、リスト \(アンディー、機能マネージャー\) に存在します。  
  
    -   **\[会社電話番号\]** とは **\[電子メール アドレス\]** の列がこのリストのビューに表示されません。  
  
     **アップグレード**の配置構成によって、SharePoint サイト上の既存の **Employees** リスト インスタンスが変更されます。  仮に**アップグレード**ではなく、**既定**の配置構成を使用した場合、配置の競合が発生します。  Visual Studioは、**\[従業員\]** のリストを置き換えることによって競合を解決し、アンディーの項目、機能マネージャーは削除されます。  
  
## 開発コンピューターのクリーンアップ  
 アップグレードの配置手順のテストが終わったら、リスト インスタンスおよびリスト定義を SharePoint サイトから削除し、さらに配置手順の拡張機能を Visual Studio から削除します。  
  
#### SharePoint サイトからリスト インスタンスを削除するには  
  
1.  リストがまだ開いていないときは、SharePointサイトの **\[従業員\]** の一覧を表示します。  
  
2.  SharePointサイトのリボンで、**\[リスト ​​ツール\]** のタブをクリックし、**\[一覧\]** のタブをクリックします。  
  
3.  **\[設定\]** のグループで、**\[リストの設定\]** の項目を選択します。  
  
4.  **\[権限と管理\]**の下に、**\[このリストを削除します\]** のコマンドをごみ箱にリストを送信する次に閉じられるWebブラウザーを選択します。ことを確認するために **\[OK\]** を選択します。  
  
#### SharePoint サイトからリスト定義を削除するには  
  
1.  Visual Studioの実験用インスタンスで、メニュー バーで、**\[ビルド\]**、**\[取り消し\]**を選択します。  
  
     SharePoint サイトからリスト定義が取り消されます。  
  
#### 拡張機能をアンインストールするには  
  
1.  Visual Studioの実験用インスタンスで、メニュー バーで、**\[ツール\]**、**\[拡張機能と更新プログラム\]**を選択します。  
  
     **\[拡張機能と更新プログラム\]** のダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で、**\[Upgrade Deployment Step for SharePoint Projects\]**を選択し、**\[アンインストール\]** のコマンドを選択します。  
  
3.  表示されたダイアログ ボックスで、拡張機能をアンインストールする選択し、アンインストールを実行するに **\[今すぐ再起動\]** を選択します。ことを確認するためにを **\[○\]**。  
  
4.  Visual Studioの実験用インスタンスとインスタンス \(UpgradeDeploymentStepソリューションが開いている\) Visual Studioの両方のインスタンスのインスタンスを閉じます。  
  
## 参照  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  