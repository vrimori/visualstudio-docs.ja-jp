---
title: 'チュートリアル: プロジェクト テンプレートを使用したサイト列プロジェクト項目の作成、パート 2 |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7616dd184bae2cabb433879ceadae79dbeb23b93
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "42626017"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>チュートリアル: プロジェクト テンプレート、第 2 部でのサイト列プロジェクト項目を作成します。
  SharePoint プロジェクト項目のカスタム種類を定義し、Visual Studio でその種類をプロジェクト テンプレートと関連付けてから、テンプレート用のウィザードを用意することもできます。 ウィザードを使用すると、ユーザーがテンプレートを使用してプロジェクト項目を含む新しいプロジェクトを作成するときに、ユーザーから情報を収集できます。 収集した情報を使用して、プロジェクト項目を初期化できます。  
  
 このチュートリアルでは、」に示した Site Column プロジェクト テンプレートにウィザードを追加[チュートリアル: プロジェクト テンプレート、第 1 部でサイト列プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)します。 ウィザードが (その基本型とグループ) など、サイト内の列に関する情報を収集およびにこの情報を追加します。 ユーザーが Site Column プロジェクトを作成するとき、 *Elements.xml*で新しいプロジェクト ファイル。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   プロジェクト テンプレートに関連付けるカスタム SharePoint プロジェクト項目の種類に対するウィザードを作成します。  
  
-   Visual Studio の SharePoint プロジェクト用の組み込みウィザードと似たカスタム ウィザードの UI を定義します。  
  
-   2 つ作成*SharePoint コマンド*ウィザードの実行中にローカル SharePoint サイトへの呼び出しに使用します。 SharePoint コマンドは、SharePoint サーバー オブジェクト モデルの API を呼び出すために Visual Studio 拡張機能で使用できるメソッドです。 詳細については、次を参照してください。 [SharePoint オブジェクト モデルの呼び出し](../sharepoint/calling-into-the-sharepoint-object-models.md)します。  
  
-   置き換え可能パラメーターを使用して、ウィザードで収集したデータで SharePoint プロジェクト ファイルを初期化します。  
  
-   新しい各 Site Column プロジェクト インスタンスで新しい .snk ファイルを作成します。 このファイルを使用してプロジェクトの出力に署名し、SharePoint ソリューション アセンブリをグローバル アセンブリ キャッシュに配置できるようにします。  
  
-   ウィザードをデバッグおよびテストします。  
  
> [!NOTE]  
> 一連のサンプル ワークフローは、次を参照してください。 [SharePoint workflow のサンプル](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行する必要がありますまず SiteColumnProjectItem ソリューション実行して作成した[チュートリアル: プロジェクト テンプレート、第 1 部でサイト列プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)します。  
  
 また、このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   サポート対象エディションの Windows、SharePoint、Visual Studio。
  
-   Visual Studio SDK。 このチュートリアルでは、 **VSIX プロジェクト**sdk プロジェクト アイテムを配置するための VSIX パッケージを作成するテンプレート。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールを拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)します。  
  
 次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   Visual Studio のプロジェクトおよび項目テンプレート用のウィザード。 詳細については、次を参照してください。[方法: プロジェクト テンプレートにウィザードの使用](../extensibility/how-to-use-wizards-with-project-templates.md)と<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>インターフェイス。  
  
-   SharePoint のサイト内の列。 詳細については、次を参照してください。[列](http://go.microsoft.com/fwlink/?LinkId=183547)します。  
  
## <a name="understand-the-wizard-components"></a>ウィザードのコンポーネントを理解します。
 このチュートリアルで説明されているウィザードには、いくつかのコンポーネントが含まれています。 次の表は、これらのコンポーネントについての説明です。  
  
|コンポーネント|説明|  
|---------------|-----------------|  
|ウィザード実装|これは `SiteColumnProjectWizard` という名前のクラスであり、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスを実装します。 このインターフェイスは、ウィザードの起動および終了時と、ウィザードの実行中の特定のタイミングで Visual Studio によって呼び出されるメソッドを定義します。|  
|ウィザード UI|これは、`WizardWindow` という名前の WPF ベースのウィンドウです。 このウィンドウには、`Page1` および `Page2` という名前の 2 つのユーザー コントロールが含まれます。 これらのユーザー コントロールは、ウィザードの 2 つのページを表します。<br /><br /> このチュートリアルでは、ウィザード実装の <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> メソッドによって、ウィザード UI が表示されます。|  
|ウィザード データ モデル|これは、`SiteColumnWizardModel` という名前の中間クラスであり、ウィザード UI とウィザード実装の間のレイヤーを提供します。 このサンプルでは、このクラスを使用して、ウィザード実装とウィザード UI を互いに抽象化できるようにします。このクラスは、すべてのウィザードで必須コンポーネントとなるわけではありません。<br /><br /> このチュートリアルでは、ウィザード UI が表示されるときに、ウィザード実装によって、ウィザード ウィンドウに `SiteColumnWizardModel` オブジェクトが渡されます。 ウィザード UI は、このオブジェクトのメソッドを使用して UI にコントロールの値を保存し、入力されたサイト URL が有効であることの確認などのタスクを実行します。 ユーザーがウィザードを終了すると、ウィザード実装は `SiteColumnWizardModel` オブジェクトを使用して、UI の最終的な状態を判断します。|  
|プロジェクト署名マネージャー|これは、`ProjectSigningManager` という名前のヘルパー クラスであり、新しい各プロジェクト インスタンスで新しい key.snk ファイルを作成するためにウィザード実装によって使用されます。|  
|SharePoint コマンド|これらは、ウィザードの実行中にローカル SharePoint サイトへの呼び出しを行うためにウィザード データ モデルによって使用されるメソッドです。 SharePoint コマンドは .NET Framework 3.5 をターゲットとする必要があるため、これらのコマンドは他のウィザード コードとは異なるアセンブリに実装されます。|  
  
## <a name="create-the-projects"></a>プロジェクトを作成します。
 このチュートリアルを完了するにはいくつかのプロジェクトで作成した SiteColumnProjectItem ソリューションに追加する必要があります[チュートリアル: プロジェクト テンプレート、第 1 部でサイト列プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):  
  
-   WPF プロジェクト。 このプロジェクトで、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスを実装し、ウィザードの UI を定義します。  
  
-   SharePoint コマンドを定義するクラス ライブラリ プロジェクト。 このプロジェクトは .NET Framework 3.5 を対象にする必要があります。  
  
 この 2 つのプロジェクトを作成することから始めます。  
  
#### <a name="to-create-the-wpf-project"></a>WPF プロジェクトを作成するには
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で、SiteColumnProjectItem ソリューションを開きます。  
  
2.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **SiteColumnProjectItem**ソリューション ノードを選択**追加**を選び、 **の新しいプロジェクト**.  
  
3.  上部にある、**新しいプロジェクトの追加** ダイアログ ボックスで、ことを確認します **.NET Framework 4.5** .NET Framework のバージョンの一覧でを選択します。  
  
4.  展開、 **Visual c#** ノードまたは**Visual Basic**ノードを選択し、 **Windows**ノード。  
  
5.  プロジェクト テンプレートの一覧で選択**WPF ユーザー コントロール ライブラリ**、プロジェクトに名前を**ProjectTemplateWizard**、選択し、 **OK**ボタン。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **ProjectTemplateWizard**プロジェクトがソリューションに既定の UserControl1.xaml ファイルを開きます。  
  
6.  UserControl1.xaml ファイルをプロジェクトから削除します。  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>SharePoint コマンド プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**、SiteColumnProjectItem ソリューション ノードのショートカット メニューを開き、**追加**を選び、**新しいプロジェクト**します。  
  
2.  上部にある、**新しいプロジェクトの追加** ダイアログ ボックスで、選択 **.NET Framework 3.5**で .NET Framework のバージョンの一覧。  
  
3.  展開、 **Visual c#** ノードまたは**Visual Basic**ノードを選択し、 **Windows**ノード。  
  
4.  選択、**クラス ライブラリ**プロジェクト テンプレート、プロジェクトの名前**SharePointCommands**、選択し、 **OK**ボタン。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **SharePointCommands**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
## <a name="configure-the-projects"></a>プロジェクトを構成します。
 ウィザードを作成する前に、いくつかのコード ファイルとアセンブリ参照をプロジェクトに追加する必要があります。  
  
#### <a name="to-configure-the-wizard-project"></a>ウィザード プロジェクトを構成するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ProjectTemplateWizard**プロジェクト ノードを選び、**プロパティ**します。  
  
2.  **プロジェクト デザイナー**、選択、**アプリケーション**Visual c# プロジェクトのタブまたは**コンパイル**Visual Basic プロジェクトのタブ。  
  
3.  ターゲット フレームワークが .NET Framework 4.5 Client Profile ではなく .NET Framework 4.5 に設定されていることを確認します。  
  
     詳細については、「[方法: .NET Framework のバージョンをターゲットにする](../ide/how-to-target-a-version-of-the-dotnet-framework.md)」を参照してください。  
  
4.  ショートカット メニューを開き、 **ProjectTemplateWizard**プロジェクトで、選択**追加**を選び、**新しい項目の**します。  
  
5.  選択、**ウィンドウ (WPF)** 項目でアイテムの名前を付けます**WizardWindow**、選択し、**追加**ボタンをクリックします。  
  
6.  2 つ追加**ユーザー コントロール (WPF)** 項目をプロジェクトには、という名前を付けます**Page1**と**Page2**します。  
  
7.  次の名前で 4 つのコード ファイルをプロジェクトに追加します。  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   CommandIds  
  
8.  ショートカット メニューを開き、 **ProjectTemplateWizard**プロジェクト ノードを選び、**参照の追加**します。  
  
9. 展開、**アセンブリ**ノードで、選択、**拡張**ノード、し、次のアセンブリの横にあるチェック ボックスを選択。  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. 選択、 **OK**アセンブリをプロジェクトに追加するボタンをクリックします。  
  
11. **ソリューション エクスプ ローラー**下で、**参照**のフォルダー、 **ProjectTemplateWizard**プロジェクトで、選択**EnvDTE**します。  
  
12. **プロパティ** ウィンドウの値を変更、 **Embed Interop Types**プロパティを**False**します。  
  
13. Visual Basic プロジェクトを開発している場合は、プロジェクトにインポート ProjectTemplateWizard 名前空間を使用して、**プロジェクト デザイナー**します。  
  
     詳細については、次を参照してください。[方法: インポートされた名前空間を追加または&#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)します。  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>SharePointcommands プロジェクトを構成するには
  
1.  **ソリューション エクスプ ローラー**、選択、 **SharePointCommands**プロジェクト ノード。  
  
2.  メニュー バーで、**プロジェクト**、**既存項目の追加**します。  
  
3.  **既存項目の追加**] ダイアログ ボックスで、ProjectTemplateWizard プロジェクトのコード ファイルを含むフォルダーを参照し、[、 **CommandIds**コード ファイル。  
  
4.  横にある矢印を選択、**追加**ボタンをクリックし、選択し、**リンクとして追加**表示されたメニュー オプション。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] コード ファイルを追加、 **SharePointCommands**プロジェクトにリンクとして。 コード ファイルにある、 **ProjectTemplateWizard**ファイル内のコードは、プロジェクトではコンパイルも、 **SharePointCommands**プロジェクト。  
  
5.  **SharePointCommands**プロジェクトに、Commands という別のコード ファイルを追加します。  
  
6.  SharePointCommands プロジェクトを選択し、次に、メニュー バーで、次のように選択します。**プロジェクト** > **参照の追加**します。  
  
7.  展開、**アセンブリ**ノードで、選択、**拡張**ノード、し、次のアセンブリの横にあるチェック ボックスを選択。  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  選択、 **OK**アセンブリをプロジェクトに追加するボタンをクリックします。  
  
## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>ウィザード モデル、署名マネージャー、および SharePoint コマンド Id を作成します。
 ProjectTemplateWizard プロジェクトにコードを追加して、サンプルの次のコンポーネントを実装します。  
  
-   SharePoint コマンド ID。 これらは、ウィザードによって使用される SharePoint コマンドを識別する文字列です。 このチュートリアルで後で、コマンドを実装する SharePointCommands プロジェクトにコードを追加します。  
  
-   ウィザード データ モデル。  
  
-   プロジェクト署名マネージャー。  
  
 これらのコンポーネントの詳細については、次を参照してください。[ウィザードのコンポーネントについて](#wizardcomponents)します。  
  
#### <a name="to-define-the-sharepoint-command-ids"></a>SharePoint コマンド ID を定義するには
  
1.  ProjectTemplateWizard プロジェクトで、CommandIds コード ファイルを開き、このファイルの内容全体を次のコードに置き換えます。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]  
  
#### <a name="to-create-the-wizard-model"></a>ウィザード モデルを作成するには  
  
1.  SiteColumnWizardModel コード ファイルを開き、このファイルの内容全体を次のコードに置き換えます。  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]  
  
#### <a name="to-create-the-project-signing-manager"></a>プロジェクト署名マネージャーを作成するには  
  
1.  ProjectSigningManager コード ファイルを開き、このファイルの内容全体を次のコードに置き換えます。  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]  
  
## <a name="create-the-wizard-ui"></a>ウィザードの UI を作成します。
 ウィザード ウィンドウの UI と、ウィザード ページの UI を提供する 2 つのユーザー コントロールを定義する XAML を追加し、ウィンドウとユーザー コントロールの動作を定義するコードを追加します。 作成するウィザードは、Visual Studio の SharePoint プロジェクト用の組み込みウィザードに似ています。  
  
> [!NOTE]  
>  以降の手順では、プロジェクトに XAML またはコードを追加した後で、いくつかのコンパイル エラーが発生します。 これらのエラーは、この後の手順でコードを追加すると解消されます。  
  
#### <a name="to-create-the-wizard-window-ui"></a>ウィザード ウィンドウの UI を作成するには
  
1.  ProjectTemplateWizard プロジェクトで、WizardWindow.xaml ファイルのショートカット メニューを開きし、**開く**デザイナーでウィンドウを開きます。  
  
2.  デザイナーの XAML ビューで、現在の XAML を次の XAML に置き換えます。 この XAML は、見出しを含む UI、ウィザード ページが含まれる <xref:System.Windows.Controls.Grid>、およびウィンドウの下部に示されるナビゲーション ボタンを定義します。  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  この XAML で作成したウィンドウがから派生、<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>基本クラス。 カスタムの WPF ダイアログ ボックスを Visual Studio に追加する場合は、ダイアログ ボックスをこのクラスから派生し、スタイルを他の Visual Studio ダイアログ ボックスと一貫させ、発生する可能性のあるモーダル ダイアログの問題を回避することをお勧めします。 詳細については、次を参照してください。[モーダル ダイアログ ボックスの管理の作成と](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes)します。  
  
3.  Visual Basic プロジェクトを開発する場合は、削除、`ProjectTemplateWizard`から名前空間、`WizardWindow`内のクラス名、`x:Class`の属性、`Window`要素。 この要素は XAML の 1 行目にあります。 完了したら、最初の行は次の例のようになります。  
  
    ```xml  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  WizardWindow.xaml ファイルの分離コード ファイルを開きます。  
  
5.  このファイルの内容を、ファイルの先頭の `using` 宣言を除いて、次のコードに置き換えます。  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]  
  
#### <a name="to-create-the-first-wizard-page-ui"></a>1 つ目のウィザード ページの UI を作成するには
  
1.  ProjectTemplateWizard プロジェクトで、Page1.xaml ファイルのショートカット メニューを開きし、**開く**をデザイナーで、ユーザー コントロールを開きます。  
  
2.  デザイナーの XAML ビューで、現在の XAML を次の XAML に置き換えます。 この XAML で定義している UI には、ユーザーがデバッグに使用するローカル サイトの URL を入力できるテキスト ボックスが含まれます。 この UI には、ユーザーがプロジェクトをサンドボックス化するかどうかを指定できるオプション ボタンも含まれます。  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]  
  
3.  Visual Basic プロジェクトを開発している場合は、`ProjectTemplateWizard` 要素の `Page1` 属性の `x:Class` クラス名から `UserControl` 名前空間を削除します。 これは XAML の 1 行目にあります。 変更後の 1 行目は次のようになります。  
  
    ```xml  
    <UserControl x:Class="Page1"  
    ```  
  
4.  Page1.xaml ファイルの内容を、ファイルの先頭にある `using` 宣言を除いて、次のコードに置き換えます。  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]  
  
#### <a name="to-create-the-second-wizard-page-ui"></a>2 つ目のウィザード ページの UI を作成するには
  
1.  ProjectTemplateWizard プロジェクトで、Page2.xaml ファイルのショートカット メニューを開きし、**開く**します。  
  
     ユーザー コントロールがデザイナーで開きます。  
  
2.  XAML ビューで、現在の XAML を次の XAML に置き換えます。 この XAML は、サイト内の列の基本型を選択するためのドロップダウン リスト、ギャラリーでサイト内の列を表示する組み込みまたはカスタムのグループを指定するためのコンボ ボックス、およびサイト内の列の名前を指定するためのボックスが含まれる UI を定義します。  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]  
  
3.  Visual Basic プロジェクトを開発している場合は、`ProjectTemplateWizard` 要素の `Page2` 属性の `x:Class` クラス名から `UserControl` 名前空間を削除します。 これは XAML の 1 行目にあります。 変更後の 1 行目は次のようになります。  
  
    ```xml  
    <UserControl x:Class="Page2"  
    ```  
  
4.  Page2.xaml ファイルの分離コード ファイルの内容を、ファイルの先頭にある `using` 宣言を除いて、次のコードに置き換えます。  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]  
  
## <a name="implement-the-wizard"></a>ウィザードを実装します。
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスを実装することで、ウィザードの主要機能を定義します。 このインターフェイスは、ウィザードの起動および終了時と、ウィザードの実行中の特定のタイミングで Visual Studio によって呼び出されるメソッドを定義します。  
  
#### <a name="to-implement-the-wizard"></a>ウィザードを実装するには  
  
1.  ProjectTemplateWizard プロジェクトで、SiteColumnProjectWizard コード ファイルを開きます。  
  
2.  このファイルの内容全体を次のコードで置き換えます。  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]  
  
## <a name="create-the-sharepoint-commands"></a>SharePoint コマンドを作成します。
 SharePoint サーバー オブジェクト モデルを呼び出す 2 つのカスタム コマンドを作成します。 一方のコマンドは、ウィザードでユーザーが入力するサイトの URL が有効かどうかを判断します。 もう一方のコマンドは、指定した SharePoint サイトからすべてのフィールドの型を取得して、ユーザーが新しいサイト内の列の基本として使用するフィールドの型を選択できるようにします。  
  
#### <a name="to-define-the-sharepoint-commands"></a>SharePoint コマンドを定義するには  
  
1.  **SharePointCommands**プロジェクトで、コマンドのコード ファイルを開きます。  
  
2.  このファイルの内容全体を次のコードで置き換えます。  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]  
  
## <a name="checkpoint"></a>チェックポイント  
 この段階で、ウィザードに必要なすべてのコードがプロジェクトに揃ったことになります。 エラーが発生することなくプロジェクトをコンパイルできるかどうか、プロジェクトをビルドして確認してください。  
  
#### <a name="to-build-your-project"></a>プロジェクトをビルドするには  
  
1.  メニュー バーで、**[ビルド]** > **[ソリューションのビルド]** の順にクリックします。  
  
## <a name="removing-the-keysnk-file-from-the-project-template"></a>プロジェクト テンプレートから key.snk ファイルを削除します。
 [チュートリアル: プロジェクト テンプレート、第 1 部でサイト列プロジェクト項目を作成する](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)、作成したプロジェクト テンプレートには、各 Site Column プロジェクト インスタンスに署名するために使用される key.snk ファイルが含まれています。 ウィザードでプロジェクトごとに新しい key.snk ファイルが生成されるようになったため、この key.snk ファイルはもう必要ありません。 プロジェクト テンプレートから key.snk ファイルを削除し、このファイルへの参照を削除します。  
  
#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>プロジェクト テンプレートから key.snk ファイルを削除するには  
  
1.  **ソリューション エクスプ ローラー**下で、 **SiteColumnProjectTemplate**ノード、ショートカット メニューを開き、 **key.snk**ファイルを選び、 **の削除**.  
  
2.  確認ダイアログ ボックスが表示されますが、選択、 **OK**ボタンをクリックします。  
  
3.  で、 **SiteColumnProjectTemplate**ノード、SiteColumnProjectTemplate.vstemplate ファイルを開くし、そこから次の要素を削除します。  
  
    ```xml  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  ファイルを保存して閉じます。  
  
5.  下、 **SiteColumnProjectTemplate**ノードで、ProjectTemplate.csproj または ProjectTemplate.vbproj ファイルを開くし、次を削除して`PropertyGroup`からの要素。  
  
    ```xml  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ``` 
  
6.  次の `None` 要素を削除します。  
  
    ```xml  
    <None Include="key.snk" />  
    ```  
  
7.  ファイルを保存して閉じます。  
  
## <a name="associating-the-wizard-with-the-project-template"></a>プロジェクト テンプレートと、ウィザードの関連付け
 これで、ウィザードを実装している、ウィザードを関連付ける必要があります、 **Site Column**プロジェクト テンプレート。 これを行うために必要となる手順は次の 3 つです。  
  
1.  ウィザード アセンブリに厳密な名前で署名します。  
  
2.  ウィザード アセンブリの公開キー トークンを取得します。  
  
3.  ウィザード アセンブリへの参照を追加の .vstemplate ファイルで、 **Site Column**プロジェクト テンプレート。  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>ウィザード アセンブリに厳密な名前で署名するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ProjectTemplateWizard**プロジェクトを選び、**プロパティ**します。  
  
2.  **署名**] タブで、[、**アセンブリに署名**チェック ボックスをオンします。  
  
3.  **厳密な名前キー ファイルを選択して**一覧で、選択**\<新規作成 >** します。  
  
4.  **厳密な名前キーの作成** ダイアログ ボックスで、チェック ボックスをオフに、新しいキー ファイルの名前を入力、**キーファイルをパスワードで保護する**チェック ボックスをオンにして、 **ok**ボタン。  
  
5.  ショートカット メニューを開き、 **ProjectTemplateWizard**プロジェクトを選び、**ビルド**ProjectTemplateWizard.dll ファイルを作成します。  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>ウィザード アセンブリの公開キー トークンを取得するには  
  
1.  **[スタート] メニュー**、選択**すべてのプログラム**、選択**Microsoft Visual Studio**、選択**Visual Studio Tools**を選択し、**開発者コマンド プロンプト**します。  
  
     Visual Studio コマンド プロンプト ウィンドウが開きます。  
  
2.  次のコマンドを実行して交換*PathToWizardAssembly*開発用コンピューター上で ProjectTemplateWizard プロジェクト用にビルドされた ProjectTemplateWizard.dll アセンブリへの完全パスで。  
  
    ```cmd  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     ProjectTemplateWizard.dll アセンブリに対する公開キー トークンが Visual Studio コマンド プロンプト ウィンドウに記述されます。  
  
3.  Visual Studio コマンド プロンプト ウィンドウは開いたままにします。 次の手順の間に、公開キー トークンが必要になります。  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>.vstemplate ファイルにウィザード アセンブリへの参照を追加するには  
  
1.  **ソリューション エクスプ ローラー**、展開、 **SiteColumnProjectTemplate**プロジェクト ノード、SiteColumnProjectTemplate.vstemplate ファイルを開きます。  
  
2.  ファイルの末尾の近くで、次の `WizardExtension` 要素を `</TemplateContent>` タグと `</VSTemplate>` タグの間に追加します。 置換、*トークン*の値、`PublicKeyToken`前の手順で取得した公開キー トークンの属性。  
  
    ```xml  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     詳細については、`WizardExtension`要素を参照してください[WizardExtension 要素&#40;Visual Studio テンプレート&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates)します。  
  
3.  ファイルを保存して閉じます。  
  
## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>プロジェクト テンプレートの Elements.xml ファイルに置き換え可能パラメーターを追加します。
 いくつかの置き換え可能パラメーターを追加、 *Elements.xml* SiteColumnProjectTemplate プロジェクトでのファイル。 これらのパラメーターは、前に定義した `RunStarted` クラスの `SiteColumnProjectWizard` メソッドで初期化されます。 Visual Studio によって自動的にこれらのパラメーターで置き換えられますユーザーが Site Column プロジェクトを作成するとき、 *Elements.xml*ウィザードでユーザーが指定した値を持つ新しいプロジェクトのファイル。  
  
 置き換え可能パラメーターはトークンであり、先頭と末尾にはドル記号 ($) が付いています。 独自の置き換え可能パラメーターを定義するだけでなく、SharePoint プロジェクト システムによって定義されて初期化される組み込みパラメーターを使用することもできます。 詳細については、次を参照してください。[置き換え可能パラメーター](../sharepoint/replaceable-parameters.md)します。  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>置き換え可能パラメーターを Elements.xml ファイルに追加するには
  
1.  SiteColumnProjectTemplate プロジェクトでの内容を置き換える、 *Elements.xml*を次の XML ファイル。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
             Name="$fieldname$"   
             DisplayName="$fieldname$"   
             Type="$selectedfieldtype$"   
             Group="$selectedgrouptype$">  
      </Field>  
    </Elements>  
    ```  
  
     新しい XML では、`Name`、`DisplayName`、`Type`、`Group` の各属性の値がカスタムの置き換え可能パラメーターに変更されます。  
  
2.  ファイルを保存して閉じます。  
  
## <a name="add-the-wizard-to-the-vsix-package"></a>VSIX パッケージをウィザードに追加します。
 Site Column プロジェクト テンプレートが含まれる VSIX パッケージと共にウィザードを配置するには、ウィザード プロジェクトと SharePoint コマンド プロジェクトへの参照を VSIX プロジェクトの source.extension.vsixmanifest ファイルに追加します。  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>VSIX パッケージにウィザードを追加するには  
  
1.  **ソリューション エクスプ ローラー**の**SiteColumnProjectItem**プロジェクトで、ショートカット メニューを開き、 **source.extension.vsixmanifest**ファイルを選び、 **オープン**します。  
  
     Visual Studio によってマニフェスト エディターでファイルが開きます。  
  
2.  **資産** タブ、エディターの選択、**新規**ボタンをクリックします。  
  
     **新しい資産の追加** ダイアログ ボックスが表示されます。  
  
3.  **型**一覧で、選択 **[microsoft.visualstudio.assembly]** します。  
  
4.  **ソース**一覧で、選択**現在のソリューションでプロジェクトを**します。  
  
5.  **プロジェクト**一覧で、選択**ProjectTemplateWizard**、選択し、 **OK**ボタン。  
  
6.  **資産** タブ、エディターの選択、**新規**もう一度ボタンをクリックします。  
  
     **新しい資産の追加** ダイアログ ボックスが表示されます。  
  
7.  **型**一覧で、入力**SharePoint.Commands.v4**します。  
  
8.  **ソース**一覧で、選択**現在のソリューションでプロジェクトを**します。  
  
9. **プロジェクト**一覧で、選択、 **SharePointCommands**プロジェクトを選び、 **OK**ボタンをクリックします。  
  
10. メニュー バーで、**ビルド** > **ソリューションのビルド**、ソリューションがエラーなしでビルドされるかどうかを確認します。  
  
## <a name="test-the-wizard"></a>ウィザードをテストします。
 これで、ウィザードをテストする準備ができました。 まず、Visual Studio の実験用インスタンスで SiteColumnProjectItem ソリューションのデバッグを開始します。 次に、Visual Studio の実験用インスタンスで、Site Column プロジェクトのウィザードをテストします。 最後に、プロジェクトをビルドして実行し、サイト内の列が正常に機能することを確認します。  
  
#### <a name="to-start-debugging-the-solution"></a>ソリューションのデバッグを開始するには  
  
1.  管理者の資格情報で Visual Studio を再起動し、SiteColumnProjectItem ソリューションを開きます。  
  
2.  ProjectTemplateWizard プロジェクトで、SiteColumnProjectWizard コード ファイルを開き、`RunStarted` メソッド内のコードの 1 行目にブレークポイントを追加します。  
  
3.  メニュー バーで、**デバッグ** > **例外**します。  
  
4.  **例外** ダイアログ ボックスに、必ず、**スローされるとき**と**user-unhandled**のチェック ボックスを**Common Language Runtime Exceptions**クリアされますが、クリックして、 **OK**ボタンをクリックします。  
  
5.  選択してデバッグを開始、 **F5**キーか、メニュー バーで**デバッグ** > **デバッグの開始**します。  
  
     Visual Studio によって、拡張機能が %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 にインストールされ、Visual Studio の実験用インスタンスが開始されます。 このインスタンスの Visual Studio でプロジェクト項目をテストします。  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Visual Studio でウィザードをテストするには  
  
1.  メニュー バーで、Visual Studio の実験用インスタンスで次のように選択します。**ファイル** > **新規** > **プロジェクト**します。  
  
2.  展開、 **Visual c#** ノードまたは**Visual Basic** (言語に応じて、プロジェクト テンプレートがサポートする)、ノードを展開、 **SharePoint**ノードを選択し、**2010**ノード。  
  
3.  プロジェクト テンプレートの一覧で選択**Site Column**、プロジェクトに名前を**SiteColumnWizardTest**、選択し、 **[ok]** ボタンをクリックします。  
  
4.  Visual Studio のもう一方のインスタンスで、先ほど `RunStarted` メソッドに設定したブレークポイントで、コードが停止していることを確認します。  
  
5.  選択して、プロジェクトのデバッグを続行、 **F5**キーか、メニュー バーで**デバッグ** > **続行**します。  
  
6.  **SharePoint カスタマイズ ウィザード**、デバッグに使用するサイトの URL を入力し、、**次**ボタンをクリックします。  
  
7.  2 ページ目で、 **SharePoint カスタマイズ ウィザード**、次の選択を行います。  
  
    -   **型**一覧で、選択**ブール**します。  
  
    -   **グループ**一覧で、選択**Custom Yes/No Columns**します。  
  
    -   **名前**ボックスに、入力**My Yes/No Column**、選択し、**完了**ボタンをクリックします。  
  
     **ソリューション エクスプ ローラー**、新しいプロジェクトが表示され、プロジェクト項目の名前が含まれて**Field1**、Visual Studio プロジェクトの表示と*Elements.xml*ファイルがエディターでします。  
  
8.  いることを確認*Elements.xml*ウィザードで指定した値が含まれています。  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>SharePoint でサイト内の列をテストするには  
  
1.  Visual Studio の実験用インスタンスの選択、 **F5**キー。  
  
     サイト内の列がパッケージ化され、SharePoint に配置されるサイト、**サイトの URL**プロジェクトのプロパティを指定します。 Web ブラウザーには、このサイトの既定のページが表示されます。  
  
    > [!NOTE]  
    >  場合、**スクリプト デバッグが無効**選択 ダイアログ ボックスが表示されたら、**はい**クリックしてプロジェクトのデバッグを続行します。  
  
2.  **サイトの操作**] メニューの [選択**サイト設定**します。  
  
3.  サイトの設定] ページで、[**ギャラリー**、選択、**サイト列**リンク。  
  
4.  サイト内の列の一覧であることを確認、 **Custom Yes/No Columns**グループにはという列が含まれています**My Yes/No Column**、web ブラウザーを閉じます。  
  
## <a name="clean-up-the-development-computer"></a>開発用コンピューターをクリーンアップします。
 プロジェクト項目のテストが終わったら、プロジェクト テンプレートを Visual Studio の実験用インスタンスから削除します。  
  
#### <a name="to-clean-up-the-development-computer"></a>開発コンピューターをクリーンアップするには  
  
1.  メニュー バーで、Visual Studio の実験用インスタンスで次のように選択します。**ツール** > **拡張機能と更新**します。  
  
     **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で選択**Site Column**、選択し、**アンインストール**ボタンをクリックします。  
  
3.  ダイアログ ボックスが表示されますが、選択、**はい**ボタンをクリックして、拡張機能をアンインストールすることを確認します、**今すぐ再起動**アンインストールを完了するボタン。  
  
4.  Visual Studio の実験用インスタンスと、CustomActionProjectItem ソリューションが開いているインスタンスの両方を閉じます。  
  
     デプロイする方法については[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、拡張機能を参照してください[Visual Studio 拡張機能の配布](/visualstudio/extensibility/shipping-visual-studio-extensions)します。  
  
## <a name="see-also"></a>関連項目
 [チュートリアル: プロジェクト テンプレート、第 1 部でのサイト列プロジェクト項目を作成します。](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [カスタム SharePoint プロジェクト項目の種類を定義します。](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [SharePoint プロジェクト項目の項目テンプレートとプロジェクト テンプレートを作成します。](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Visual Studio テンプレート スキーマ参照](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [方法: プロジェクト テンプレートでウィザードを使用する](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
