---
title: "Walkthrough: Creating a SharePoint Project Extension"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: 5547e2ed-47a3-48f1-9619-42149c03df76
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Walkthrough: Creating a SharePoint Project Extension
  このチュートリアルでは、SharePoint プロジェクトの拡張機能を作成する方法について説明します。  プロジェクトが追加、削除、または名前変更されたときにプロジェクト レベルのイベント \(など\) に応答のプロジェクトの拡張機能を使用できます。  また、プロパティ値の変更時にカスタム プロパティを追加したり、応答したりすることもできます。  プロジェクト項目の拡張機能とは異なり、プロジェクトの拡張機能を特定の SharePoint プロジェクトの種類に関連付けることはできません。  プロジェクトの拡張機能を作成すると、いずれかの種類の SharePoint プロジェクトが [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で開かれたときに、その拡張機能が読み込まれます。  
  
 このチュートリアルでは、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で作成された SharePoint プロジェクトに追加するカスタムのブール型プロパティを作成します。  **True** に設定すると、新しいプロパティによって Images リソース フォルダーがプロジェクトに追加されるか、マップされます。  **False** に設定すると、Images フォルダーがある場合には、そのフォルダーが削除されます。  詳細については、「[方法: マップされたフォルダーを追加および削除する](../sharepoint/how-to-add-and-remove-mapped-folders.md)」を参照してください。  
  
 このチュートリアルでは、次のタスクを実行します。  
  
-   次の処理を行う SharePoint プロジェクトの [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 拡張機能を作成する。  
  
    -   カスタム プロジェクト プロパティを \[プロパティ\] ウィンドウに追加します。  追加したプロパティが SharePoint プロジェクトに適用されます。  
  
    -   SharePoint プロジェクトのオブジェクト モデルを使用して、マップされたフォルダーをプロジェクトに追加します。  
  
    -   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のオートメーション オブジェクト モデル \(DTE\) を使用して、マップされたフォルダーをプロジェクトから削除します。  
  
-   プロジェクト プロパティの拡張機能のアセンブリを配置するための [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Visual Studio Extension \(VSIX\) パッケージを構築する。  
  
-   プロジェクト プロパティのデバッグとテストを行う。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   サポート対象エディションの [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]、SharePoint、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。  このチュートリアルでは、プロジェクト プロパティ拡張機能を配置するための VSIX パッケージを、[!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] の **VSIX プロジェクト** テンプレートを使用して作成します。  詳細については、「[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## プロジェクトの作成  
 このチュートリアルを完了するには、2 つのプロジェクトを作成する必要があります。  
  
-   プロジェクトの拡張機能を配置するために VSIX パッケージを作成する VSIX プロジェクト  
  
-   プロジェクトの拡張機能を実装するクラス ライブラリ プロジェクト  
  
 この 2 つのプロジェクトを作成することから始めます。  
  
#### VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで **\[ファイル\]**、**\[新規\]**、**\[プロジェクト\]** の順にクリックします。  
  
3.  **\[新しいプロジェクト\]** のダイアログ ボックスで、**\[Visual C\#\]** または **\[Visual Basic\]** のノードを展開し、**\[機能拡張\]** のノードを選択します。  
  
    > [!NOTE]  
    >  このノードは、Visual Studio SDKをインストールするときだけです。  詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
4.  ダイアログ ボックスの上部に、.NET Frameworkのバージョンの一覧の **\[.NET Framework 4.5\]** を選択し、**\[VSIX プロジェクト\]** テンプレートを選択します。  
  
5.  **\[名前\]** ボックスに、**\[ProjectExtensionPackage\]**を入力し、を **\[OK\]** のボタンをクリックします。  
  
     **\[ProjectExtensionPackage\]** のプロジェクトは **\[ソリューション エクスプローラー\]**に表示されます。  
  
#### 拡張機能プロジェクトを作成するには  
  
1.  **\[ソリューション エクスプローラー\]**で、ソリューション ノードのショートカット メニューを開き、**\[追加\]**を選択し、を **\[新しいプロジェクト\]**を選択します。  
  
    > [!NOTE]  
    >  [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] のプロジェクトでは、ソリューション ノードが **\[ソリューション エクスプローラー\]** で **\[常にソリューションを表示\]** のチェック ボックスが [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/ja-jp/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)で選択されている場合にのみ表示されます。  
  
2.  **\[新しいプロジェクト\]** のダイアログ ボックスで、**\[Visual C\#\]** または **\[Visual Basic\]** のノードを展開し、**\[ウィンドウ\]**を選択します。  
  
3.  ダイアログ ボックスの上部に、.NET Frameworkのバージョンの一覧の **\[.NET Framework 4.5\]** を選択し、**\[クラス ライブラリ\]** のプロジェクト テンプレートを選択します。  
  
4.  **\[名前\]** ボックスに、**\[ProjectExtension\]**を入力し、を **\[OK\]** のボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって、**ProjectExtension** プロジェクトがソリューションに追加され、既定の Class1 コード ファイルが開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
## プロジェクトの構成  
 プロジェクトの拡張機能を作成するためのコードを記述する前に、コード ファイルおよびアセンブリ参照を拡張機能プロジェクトに追加します。  
  
#### プロジェクトを構成するには  
  
1.  ProjectExtensionプロジェクトへの **CustomProperty** という名前のコード ファイルを追加します。  
  
2.  **\[ProjectExtension\]** のプロジェクトのショートカット メニューを開き、**\[参照の追加\]**を選択します。  
  
3.  **\[CustomPropertyマネージャー–を参照してください。\]** のダイアログ ボックスで、**\[Framework\]** のノードを選択し、System.ComponentModel.CompositionおよびSystem.Windows.Formsの各アセンブリの横にあるチェック ボックスをオンにします。  
  
4.  **\[拡張機能\]** のノードを選択すると、Microsoft.VisualStudio.SharePoint EnvDTEアセンブリの横にあるチェック ボックスをオンにし、**\[OK\]** のボタンをクリックします。  
  
5.  **\[ProjectExtension\]** のプロジェクトの **\[参照\]** フォルダーの下の **\[ソリューション エクスプローラー\]**では、**\[EnvDTE\]**を選択します。  
  
6.  **\[プロパティ\]** ウィンドウで、**\[相互運用型の埋め込み\]** プロパティを **False** に変更します。  
  
## 新しい SharePoint プロジェクト プロパティの定義  
 プロジェクトの拡張機能および新しいプロジェクト プロパティの動作を定義するクラスを作成します。  新しいプロジェクトの拡張機能を定義するため、このクラスに <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> インターフェイスを実装します。  このインターフェイスは、SharePoint プロジェクトの拡張機能を定義する場合に必ず実装します。  さらに、このクラスに <xref:System.ComponentModel.Composition.ExportAttribute> メソッドを追加します。  この属性によって、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> の実装を検出し、読み込むことができます。  この属性のコンストラクターには <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 型を渡します。  
  
#### 新しい SharePoint プロジェクト プロパティを定義するには  
  
1.  CustomPropertyコード ファイルに次のコードを貼り付けます。  
  
     [!code-csharp[SPExt_ProjectExtension#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_projectextension/cs/projectextension/customproperty.cs#1)]
     [!code-vb[SPExt_ProjectExtension#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_projectextension/vb/projectextension/customproperty.vb#1)]  
  
## ソリューションのビルド  
 エラーが発生することなくソリューションをコンパイルできるかどうか、ソリューションをビルドして確認してください。  
  
#### ソリューションをビルドするには  
  
1.  メニュー バーで、**\[ビルド\]**、**\[ソリューションのビルド\]**を選択します。  
  
## プロジェクト プロパティの拡張機能を配置するための VSIX パッケージの作成  
 プロジェクトの拡張機能を配置するためにソリューションで VSIX プロジェクトを使用して VSIX パッケージを作成するには  まず、VSIX プロジェクトに含まれている source.extension.vsixmanifest ファイルを変更して、VSIX パッケージを構成します。  次に、ソリューションをビルドして VSIX パッケージを作成します。  
  
#### VSIX パッケージを構成および作成するには  
  
1.  **\[ソリューション エクスプローラー\]**では、source.extension.vsixmanifestファイルのショートカット メニューを開き、**\[開く\]** のボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] はマニフェスト デザイナーでファイルを開きます。  **\[メタデータ\]** のタブで、表示される情報は **\[拡張機能と更新プログラム\]**に表示されます。すべてのVSIXパッケージは、extension.vsixmanifestファイルが必要です。  このファイルの詳細については、「[VSIX 拡張機能のスキーマに関するリファレンス](http://msdn.microsoft.com/ja-jp/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)」を参照してください。  
  
2.  **\[製品名\]** ボックスに、**カスタム プロジェクト プロパティ**を入力します。  
  
3.  **\[作成者\]** ボックスに、**\[Contoso\]**を入力します。  
  
4.  **\[説明\]** ボックスに、**プロジェクトにイメージ リソースのフォルダー マップを切り替えるカスタムのSharePointプロジェクト プロパティ**を入力します。  
  
5.  **\[資産\]** のタブをクリックし、**\[新規作成\]** のボタンをクリックします。  
  
     **\[新しい資産の追加\]** のダイアログ ボックスが表示されます。  
  
6.  **\[種類\]** の一覧で、**\[Microsoft.VisualStudio.MefComponent\]**を選択します。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MEFComponent` 要素に対応します。  この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。  詳細については、「[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/ja-jp/8a813141-8b73-44c9-b80b-ca85bbac9551)」を参照してください。  
  
7.  **\[ソース\]** の一覧で、**\[現在のソリューション内のプロジェクト\]** のオプション ボタンを選択します。  
  
8.  **\[プロジェクト\]** の一覧で、**\[ProjectExtension\]**を選択します。  
  
     この値は、プロジェクトでビルドされたアセンブリの名前を指定します。  
  
9. **\[新しい資産の追加\]** のダイアログ ボックスを閉じるに **\[OK\]** を選択します。  
  
10. メニュー バーで、終了選択し、マニフェスト デザイナーを閉じるとき **\[ファイル\]**、を **\[すべて保存\]**。  
  
11. メニュー バーで、**\[ビルド\]**、**\[ソリューションのビルド\]**を選択し、次に、プロジェクトがエラーなしでコンパイルしてください。  
  
12. **\[ソリューション エクスプローラー\]**では、**\[ProjectExtensionPackage\]** のプロジェクトのショートカット メニューを開き、**\[エクスプローラーでフォルダーを開く\]** のボタンをクリックします。  
  
13. **\[エクスプローラー\]**では、ProjectExtensionPackageプロジェクトのビルド出力フォルダーを開き、フォルダーがProjectExtensionPackage.vsixという名前のファイルが含まれていることを確認します。  
  
     既定では、プロジェクト ファイルに格納されているフォルダー  の ..\\bin\\Debug フォルダーがビルド出力フォルダーです。  
  
## プロジェクト プロパティのテスト  
 カスタム プロジェクト プロパティをテストする準備ができました。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]の実験用インスタンスで新しいプロジェクト プロパティの拡張機能のデバッグ、テストが容易になります。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のこのインスタンスは、VSIXまたは他の機能拡張プロジェクトを実行するときに作成されます。  プロジェクトをデバッグした後、拡張機能をシステムにインストールされて、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]の通常のインスタンスで拡張デバッグとテストを行うことができます。  
  
#### Visual Studio の実験用のインスタンスで拡張機能のデバッグとテストを行うには  
  
1.  管理資格情報を使用してを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を再起動し、ProjectExtensionPackageソリューションを開きます。  
  
2.  **\[F5\]** のキーを選択して、プロジェクトのデバッグ ビルドをまたは、**\[デバッグ\]**を選択するメニュー バーで **\[デバッグの開始\]**起動します。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は%UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\CustomのプロジェクトProperty\\1.0に拡張機能をインストール、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]の実験用インスタンスを起動します。  
  
3.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]の実験用インスタンスで、ファーム ソリューションのSharePointプロジェクトを作成し、そのほかの値のウィザードで既定値を使用します。  
  
    1.  メニュー バーで **\[ファイル\]**、**\[新規\]**、**\[プロジェクト\]** の順にクリックします。  
  
    2.  **\[新しいプロジェクト\]** のダイアログ ボックスの上部に、.NET Frameworkのバージョンの **\[.NET Framework 3.5\]** リストのを選択します。  
  
         SharePointツールの拡張機能が [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]、このバージョンのの機能が必要です。  
  
    3.  **\[テンプレート\]** のノードの下で、**\[Visual C\#\]** または **\[Visual Basic\]** のノードを展開し、**\[SharePoint\]** のノードを選択し、を **\[2010\]** のノードを選択します。  
  
    4.  **\[SharePoint 2010 プロジェクト\]** テンプレートを選択し、プロジェクトの名前として **\[ModuleTest\]** を入力します。  
  
4.  **\[ソリューション エクスプローラー\]**では、**\[ModuleTest\]** のプロジェクト ノードを選択します。  
  
     **\[プロパティ\]** ウィンドウに、既定値が **False** である新しいカスタム プロパティ **Map Images Folder** が表示されます。  
  
5.  **True**にそのプロパティの値を変更します。  
  
     SharePoint プロジェクトに Images リソース フォルダーが追加されます。  
  
6.  **False**にそのプロパティの値を返します。  
  
     **\[Delete the Images folder?\]** のダイアログ ボックスの **\[○\]** のボタンを選択すると、Imagesリソース フォルダーがSharePointプロジェクトから削除されます。  
  
7.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の実験用のインスタンスを閉じます。  
  
## 参照  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  