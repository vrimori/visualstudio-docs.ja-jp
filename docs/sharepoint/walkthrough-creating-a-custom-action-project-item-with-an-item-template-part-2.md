---
title: "Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "project items [SharePoint development in Visual Studio], creating template wizards"
  - "SharePoint project items, creating template wizards"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 2d8165d3-4af9-4a5e-bdba-8b2a06b1dc8d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2
  SharePoint プロジェクト項目のカスタム種類を定義し、Visual Studio でその種類を項目テンプレートと関連付けてから、テンプレート用のウィザードを用意することもできます。  ユーザーが独自のテンプレートを使用してプロジェクト項目の新しいインスタンスをプロジェクトに追加するときに、ウィザードを使用してユーザーから情報を収集できます。  収集した情報を使用して、プロジェクト項目を初期化できます。  
  
 このチュートリアルでは、「[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)」で示されているカスタム動作プロジェクト項目にウィザードを追加します。  userがSharePointプロジェクトにカスタム動作プロジェクト項目を追加すると、ウィザードは、エンド ユーザーが選択したときにカスタム動作についての情報 \(移動するための場所とURLなど\) に収集し、新しいプロジェクト項目のElements.xmlファイルにこの情報を追加します。  
  
 このチュートリアルでは、次のタスクを実行します。  
  
-   項目テンプレートに関連付けるカスタム SharePoint プロジェクト項目の種類に対するウィザードの作成。  
  
-   Visual Studio の SharePoint プロジェクト項目用の組み込みウィザードと似たカスタム ウィザードの UI の定義。  
  
-   置き換え可能パラメーターを使用して、ウィザードで収集したデータで SharePoint プロジェクト ファイルを初期化します。  
  
-   ウィザードをデバッグおよびテストします。  
  
> [!NOTE]  
>  次の場所から、このチュートリアルの完了のプロジェクト、コードとそのほかのファイルを含むサンプルをダウンロードできます: [SharePointのプロジェクト ファイルは、機能拡張のチュートリアルにTools](http://go.microsoft.com/fwlink/?LinkId=191369)。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、先に「[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)」を完了して CustomActionProjectItem ソリューションを作成しておく必要があります。  
  
 また、このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   Windows SharePoint、およびサポートされるVisual Studioのエディション。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   Visual Studio SDK。  このチュートリアルでは、SDK の **VSIX プロジェクト** テンプレートを使用して、プロジェクト項目を配置するための VSIX パッケージを作成します。  詳細については、「[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
 次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   Visual Studio のプロジェクトおよび項目テンプレート用のウィザード。  詳細については、「[方法 : プロジェクト テンプレートを組み合わせたウィザードを使用する](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)」および <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスを参照してください。  
  
-   SharePoint のカスタム動作。  詳細については、「[Custom Action \(カスタム動作\)](http://go.microsoft.com/fwlink/?LinkId=177800)」を参照してください。  
  
## ウィザード プロジェクトの作成  
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)で作成したこのチュートリアルを完了するには、CustomActionProjectItemソリューションにプロジェクトを追加する必要があります。  このプロジェクトで、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスを実装し、ウィザードの UI を定義します。  
  
#### ウィザード プロジェクトを作成するには  
  
1.  Visual Studioでは、CustomActionProjectItemソリューションを開きます。  
  
2.  **\[ソリューション エクスプローラー\]**で、ソリューション ノードのショートカット メニューを開き、**\[追加\]**を選択し、を **\[新しいプロジェクト\]**を選択します。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトで**ソリューション エクスプローラー**にソリューション ノードが表示されるのは、[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/ja-jp/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)の **\[常にソリューションを表示\]** チェック ボックスがオンになっている場合だけです。  
  
3.  **\[新しいプロジェクト\]** のダイアログ ボックスで、**\[Visual C\#\]** または **\[Visual Basic\]** のノードを展開し、**\[ウィンドウ\]** のノードを選択します。  
  
4.  **\[新しいプロジェクト\]** のダイアログ ボックスの上部に、**\[.NET Framework 4.5\]** が.NET Frameworkのバージョンの一覧で、が選択されていることを確認します。  
  
5.  **\[WPF ユーザー コントロール ライブラリ\]** のプロジェクト テンプレートを選択し、プロジェクト **\[ItemTemplateWizard\]**を付けておくと、**\[OK\]** のボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のソリューションに **ItemTemplateWizard** プロジェクトが追加されます。  
  
6.  プロジェクトから UserControl1 アイテムを削除します。  
  
## ウィザード プロジェクトの構成  
 ウィザードを作成する前に、プロジェクトにWindows Presentation Foundation \(WPF\)のウィンドウ、コード ファイルおよびアセンブリ参照を追加する必要があります。  
  
#### ウィザード プロジェクトを構成するには  
  
1.  **\[ソリューション エクスプローラー\]**では、**\[ItemTemplateWizard\]** のプロジェクト ノードからショートカット メニューを開き、**\[プロパティ\]**を選択します。  
  
2.  **\[プロジェクト デザイナー\]**で、ターゲット フレームワークを.NET Framework 4.5に設定されていることを確認します。  
  
     Visual C\#プロジェクトの場合は、**\[アプリケーション\]** のタブにこの値を設定できます。  Visual Basicプロジェクトの場合、**\[コンパイル\]** のタブにこの値を設定できます。  詳細については、「[方法: .NET Framework のバージョンをターゲットにする](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)」を参照してください。  
  
3.  **\[ItemTemplateWizard\]** のプロジェクトでは、**\[ウィンドウ \(WPF\)\]** の項目をプロジェクトに追加し、項目 **WizardWindow**を表示します。  
  
4.  CustomActionWizard String 2とという二つのコード ファイルを追加します。  
  
5.  **\[ItemTemplateWizard\]** のプロジェクトのショートカット メニューを開き、**\[参照の追加\]**を選択します。  
  
6.  **\[Reference Manager \- ItemTemplateWizard\]** のダイアログ ボックスで、**\[アセンブリ\]** のノードの下で、**\[拡張機能\]** のノードを選択します。  
  
7.  チェック ボックスは、次のアセンブリの横にあるを選択し、**\[OK\]** のボタンを選択する:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  ItemTemplateWizardプロジェクトの **\[参照\]** フォルダーの **\[ソリューション エクスプローラー\]**では、**\[EnvDTE\]** の参照を選択します。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトでは、**\[参照設定\]** フォルダーが表示されるのは、[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/ja-jp/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) で **\[常にソリューションを表示\]** チェック ボックスがオンになっている場合のみです。  
  
9. **\[プロパティ\]** のペインで、**\[false\]**に **\[相互運用型の埋め込み\]** のプロパティの値を変更します。  
  
## カスタム動作の既定の場所と ID 文字列の定義  
 すべてのカスタム動作には場所と ID があり、Elements.xml ファイルの `CustomAction` 要素の `GroupID` 属性と `Location` 属性で指定されています。  この手順では、ItemTemplateWizard プロジェクトでこれらの属性に有効な文字列のいくつかを定義します。  このチュートリアルを完了すると、これらの文字列は、カスタム動作プロジェクト項目のElements.xmlファイルにuser、このウィザードの場所とIDを指定するときに書き込まれます。  
  
 簡潔にするため、このサンプルでは使用可能な既定の場所と ID のサブセットのみをサポートしています。  完全な一覧については、「[Default Custom Action Locations and IDs \(カスタム動作の既定の場所と ID\)](http://go.microsoft.com/fwlink/?LinkId=181964)」を参照してください。  
  
#### 既定の場所と ID の文字列を定義するには  
  
1.  開きます。  
  
2.  **\[ItemTemplateWizard\]** のプロジェクトでは、次のコードにStringコード ファイルのコードに置き換えます。  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/strings.vb#6)]  
  
## ウィザードの UI の作成  
 ウィザードの UI を定義する XAML を追加し、ウィザードの一部のコントロールを ID 文字列にバインドするためのコードを追加します。  作成するウィザードは、Visual Studio の SharePoint プロジェクト用の組み込みウィザードに似ています。  
  
#### ウィザードの UI を作成するには  
  
1.  **\[ItemTemplateWizard\]** のプロジェクトでは、**\[WizardWindow.xaml\]** ファイルのショートカット メニューを開き、ウィンドウをデザイナーで開くに **\[開く\]** を選択します。  
  
2.  XAMLビューで、次のXAMLに現在のXAMLに置き換えます。  この XAML は、見出しを含む UI、カスタム動作の振る舞いを指定するためのコントロール、およびウィンドウの下部に示されるナビゲーション ボタンを定義します。  
  
    > [!NOTE]  
    >  このコードを追加すると、いくつかのコンパイル エラーが発生します。  これらのエラーは、この後の手順でコードを追加すると解消されます。  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  このXAMLで作成するウィンドウは <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> の基本クラスから派生します。  Visual StudioにカスタムのWPFダイアログ ボックスを追加すると、Visual Studioの他のダイアログ ボックスで一貫したスタイル設定を使用すると、モーダル ダイアログ ボックスとして別の方法で発生する可能性のある問題を回避するには、このクラスからダイアログ ボックスを取得することをお勧めします。  詳細については、「[作成して、モーダル ダイアログ ボックスを管理します。](../extensibility/creating-and-managing-modal-dialog-boxes.md)」を参照してください。  
  
3.  Visual Basicプロジェクトを開発している場合は、`Window` の要素の `x:Class` の属性の `WizardWindow` の `ItemTemplateWizard` のクラス名から名前空間を削除します。  この要素は、の最初の行にあります。  されると、最初の行は次のようになります。:  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  WizardWindow.xamlファイルの分離コード ファイルで、次のコードでは、現在のコードに置き換えます。  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/wizardwindow.xaml.cs#7)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/wizardwindow.xaml.vb#7)]  
  
## ウィザードの実装  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスを実装することで、ウィザードの機能を定義します。  
  
#### ウィザードを実装するには  
  
1.  **\[ItemTemplateWizard\]** のプロジェクトでは、**\[CustomActionWizard\]** コード ファイルを開き、次のコードでこのファイルの現在のコードに置き換えます。:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/customactionwizard.vb#8)]  
  
## チェックポイント  
 この段階で、ウィザードに必要なすべてのコードがプロジェクトに揃ったことになります。  エラーが発生することなくプロジェクトをコンパイルできるかどうか、プロジェクトをビルドして確認してください。  
  
#### プロジェクトをビルドするには  
  
1.  メニュー バーで、**\[ビルド\]**、**\[ソリューションのビルド\]**を選択します。  
  
## ウィザードと項目テンプレートの関連付け  
 ウィザードの実装が済んだので、**\[ユーザー設定のアクション\]** の項目テンプレートで3種類の主要な手順を実行すると、アプリケーションを関連付ける必要があります:  
  
1.  ウィザード アセンブリに厳密な名前で署名します。  
  
2.  ウィザード アセンブリの公開キー トークンを取得します。  
  
3.  **カスタム動作**項目テンプレートの .vstemplate ファイルに、ウィザード アセンブリへの参照を追加します。  
  
#### ウィザード アセンブリに厳密な名前で署名するには  
  
1.  **\[ソリューション エクスプローラー\]**では、**\[ItemTemplateWizard\]** のプロジェクト ノードからショートカット メニューを開き、**\[プロパティ\]**を選択します。  
  
2.  **\[署名\]** タブの **\[アセンブリの署名\]** チェック ボックスをオンにします。  
  
3.  **\[厳密な名前のキー ファイルを選択してください\]** の一覧で、を選択 **\<New...\>**します。  
  
4.  **\[厳密な名前キーの作成\]** のダイアログ ボックスに名前を入力し、**\[キーファイルをパスワードで保護する\]** のチェック ボックスをオフにし、を **\[OK\]** のボタンをクリックします。  
  
5.  メニュー バーで、**\[ビルド\]**、**\[ソリューションのビルド\]**を選択します。  
  
#### ウィザード アセンブリの公開キー トークンを取得するには  
  
1.  Visual Studioのコマンド プロンプト ウィンドウで、開発用コンピューターにItemTemplateWizardプロジェクトのビルドされたItemTemplateWizard.dllアセンブリに完全パスで *PathToWizardAssembly* を置き換える次のコマンドを実行します。  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     ItemTemplateWizard.dll アセンブリに対する公開キー トークンが Visual Studio コマンド プロンプト ウィンドウに記述されます。  
  
2.  Visual Studio コマンド プロンプト ウィンドウは開いたままにします。  公開キー トークンが次の手順を実行する必要があります。  
  
#### .vstemplate ファイルにウィザード アセンブリへの参照を追加するには  
  
1.  **\[ソリューション エクスプローラー\]**では、**\[ItemTemplate\]** のプロジェクト ノードを展開し、ItemTemplate.vstemplateファイルを開きます。  
  
2.  ファイルの末尾の近くで、次の `WizardExtension` 要素を `</TemplateContent>` タグと `</VSTemplate>` タグの間に追加します。  前の手順で取得した公開キー トークンで `PublicKeyToken` の属性の *YourToken* の値に置き換えます。  
  
    ```  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     `WizardExtension` 要素の詳細については、「[WizardExtension 要素 &#40;Visual Studio テンプレート&#41;](../extensibility/wizardextension-element-visual-studio-templates.md)」を参照してください。  
  
3.  ファイルを保存して閉じます。  
  
## 項目テンプレートの Elements.xml ファイルへの置き換え可能パラメーターの追加  
 複数の置き換え可能パラメーターを、ItemTemplate プロジェクトの Elements.xml ファイルに追加します。  これらのパラメーターは、前に定義した `CustomActionWizard` クラスの `PopulateReplacementDictionary` メソッドで初期化されます。  ユーザーがカスタム動作プロジェクト項目をプロジェクトに追加すると、Visual Studio によって自動的に、新しいプロジェクト項目の Elements.xml ファイル内のこれらのパラメーターが、ウィザードでユーザーが指定した値に置き換えられます。  
  
 置き換え可能パラメーターはドル記号 \($\) が付いて開始と終了のトークンです。  独自の置き換え可能パラメーターの定義に加えて、SharePointプロジェクト システムが定義し、初期化、組み込みパラメーターを使用できます。  詳細については、「[置き換え可能パラメーター](../sharepoint/replaceable-parameters.md)」を参照してください。  
  
#### 置き換え可能パラメーターを Elements.xml ファイルに追加するには  
  
1.  ItemTemplateプロジェクトでは、次のXMLにElements.xmlファイルの内容を置き換えます。  
  
    ```  
  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="$IdValue$"  
                    GroupId="$GroupIdValue$"  
                    Location="$LocationValue$"  
                    Sequence="1000"  
                    Title="$TitleValue$"  
                    Description="$DescriptionValue$" >  
        <UrlAction Url="$UrlValue$"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     新しい XML では、`Id`、`GroupId`、`Location`、`Description`、`Url` の各属性の値が置き換え可能パラメーターに変更されます。  
  
2.  ファイルを保存して閉じます。  
  
## VSIX パッケージへのウィザードの追加  
 VSIXプロジェクトのsource.extension.vsixmanifestファイルで、プロジェクト項目を含むVSIXパッケージで配置したように、ウィザード プロジェクトへの参照を追加します。  
  
#### VSIX パッケージにウィザードを追加するには  
  
1.  **\[ソリューション エクスプローラー\]**では、CustomActionProjectItemプロジェクトの **\[source.extension.vsixmanifest\]** ファイルからショートカット メニューを開き、マニフェスト エディターでファイルを開くには **\[開く\]** を選択します。  
  
2.  マニフェスト エディターで、**\[資産\]** タブをクリックし、を **\[新規作成\]** のボタンをクリックします。  
  
     **\[新しい資産の追加\]** のダイアログ ボックスが表示されます。  
  
3.  **\[種類\]** の一覧で、**\[Microsoft.VisualStudio.Assembly\]**を選択します。  
  
4.  **\[ソース\]** の一覧で、**\[現在のソリューション内のプロジェクト\]**を選択します。  
  
5.  **\[プロジェクト\]** の一覧で、**\[ItemTemplateWizard\]**を選択し、**\[OK\]** のボタンをクリックします。  
  
6.  メニュー バーで、**\[ビルド\]**、**\[ソリューションのビルド\]**を選択し、次に、ソリューションのエラーなしでコンパイルしてください。  
  
## ウィザードのテスト  
 これで、ウィザードをテストする準備ができました。  まず、Visual Studioの実験用インスタンスでCustomActionProjectItemソリューションのデバッグを開始します。  次に、Visual Studioの実験用インスタンスで、SharePointプロジェクトのカスタム動作プロジェクト項目のウィザードをテストします。  最後に、SharePoint プロジェクトをビルドして実行し、カスタム動作が正常に機能することを確認します。  
  
#### ソリューションをデバッグする  
  
1.  管理資格情報を使用してVisual Studioを再起動し、CustomActionProjectItemソリューションを開きます。  
  
2.  ItemTemplateWizardプロジェクトで、CustomActionWizardコード ファイルを開き、`RunStarted` のメソッドのコードの先頭行にブレークポイントを追加します。  
  
3.  メニュー バーで、**\[デバッグ\]**、**\[例外\]**を選択します。  
  
4.  **\[例外\]** のダイアログ ボックスで、**\[Common Language Runtime Exceptions\]** の **\[スローされるとき\]** と **\[ユーザーにハンドルされていないとき\]** のチェック ボックスがオフになっていることを確認し、次に **\[OK\]** のボタンを選択します。  
  
5.  F5キーのは、**\[デバッグ\]**を選択するメニュー バーのをクリックしてデバッグを開始した **\[デバッグの開始\]**。  
  
     Visual Studioは、%UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Custom Action Project Item\\1.0に拡張機能をインストール、Visual Studioの実験用インスタンスを起動します。  Visual Studioでプロジェクト項目をテストします。この場合  
  
#### Visual Studio でウィザードをテストするには  
  
1.  Visual Studioの実験用インスタンスで、メニュー バーで、**\[ファイル\]**、**\[新規作成\]**、**\[プロジェクト\]**を選択します。  
  
2.  **\[Visual C\#\]** または **\[Visual Basic\]** のノードを次の項目テンプレートがサポートする言語に応じて\) **\[SharePoint\]** 展開し、ノードを展開し、を **\[2010\]** のノードを選択します。  
  
3.  プロジェクト テンプレートの一覧で、**\[SharePoint 2010 プロジェクト\]**を選択し、プロジェクト **CustomActionWizardTest**を付けておくと、**\[OK\]** のボタンをクリックします。  
  
4.  **\[SharePoint カスタマイズ ウィザード\]**では、デバッグ用に使用する入力し、次に **\[完了\]** のボタンを選択します。サイトのURL。  
  
5.  **\[ソリューション エクスプローラー\]**で、プロジェクトのノードのショートカット メニューを開き、**\[追加\]**を選択し、を **\[新しい項目\]**を選択します。  
  
6.  **\[Add New Item \- CustomItemWizardTest\]** のダイアログ ボックスで、**\[SharePoint\]** のノードを展開し、**\[2010\]** のノードを展開します。  
  
7.  プロジェクト項目の一覧で、**\[ユーザー設定のアクション\]** の項目を選択し、**\[追加\]** のボタンをクリックします。  
  
8.  Visual Studio のもう一方のインスタンスで、先ほど `RunStarted` メソッドに設定したブレークポイントで、コードが停止していることを確認します。  
  
9. または、**\[デバッグ\]**を選択するメニュー バーで **\[続行\]**F5キーをクリックして、プロジェクトのデバッグを続行します。  
  
     SharePoint カスタマイズ ウィザードが表示されます。  
  
10. **\[場所\]**の下に、**\[List Edit\]** のオプション ボタンを選択します。  
  
11. **\[グループ ID\]** の一覧で、**\[通信\]**を選択します。  
  
12. **\[タイトル\]** ボックスに、**\[SharePoint Developer Center\]**を入力します。  
  
13. **\[説明\]** ボックスに、**SharePoint Developer Center Webサイトを開きます**を入力します。  
  
14. **\[URL\]** ボックスに、**http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx**を入力し、を **\[完了\]** のボタンをクリックします。  
  
     isual Studioでは、プロジェクトへの **\[CustomAction1\]** という追加され、エディターのElements.xmlファイルを項目を開きます。  Elements.xml にウィザードで指定した値が含まれることを確認します。  
  
#### SharePoint のカスタム動作をテストするには  
  
1.  Visual Studioの実験用インスタンスで、F5キーのキーを選択したり、メニュー バーで、**\[デバッグ\]**、**\[デバッグの開始\]**を選択します。  
  
     プロジェクトの **\[サイト URL\]** のプロパティで指定されたカスタム動作はSharePointサイトにパッケージ化および配置され、WebBrowserには、このサイトの既定のページが表示されます。  
  
    > [!NOTE]  
    >  **\[スクリプト デバッグが無効\]** ダイアログ ボックスが表示されたら、**\[○\]** のボタンをクリックします。  
  
2.  SharePointサイトのリストの領域では、**\[タスク\]** のリンクを選択します。  
  
     **\[–にすべてのタスクおよびタスク\]** のページが表示されます。  
  
3.  次に、リボン **\[リスト ​​ツール\]** のタブで、**\[一覧\]** のタブを、**\[設定\]** のグループで、をクリックします **\[リストの設定\]**を選択します。  
  
     **\[リストの設定\]** のページが表示されます。  
  
4.  ページの先頭付近に **\[通信\]** 見出しの下で、ブラウザーがWebサイトhttp:\/\/msdn.microsoft.com\/sharepoint\/default.aspxを開き、ブラウザーを閉じます選択することを **\[SharePoint Developer Center\]** のリンクを確認します。  
  
## 開発コンピューターのクリーンアップ  
 プロジェクト項目のテストが終わったら、プロジェクト項目テンプレートを Visual Studio の実験用インスタンスから削除します。  
  
#### 開発コンピューターをクリーンアップするには  
  
1.  Visual Studioの実験用インスタンスで、メニュー バーで、**\[ツール\]**、**\[拡張機能と更新プログラム\]**を選択します。  
  
     **\[拡張機能と更新プログラム\]** のダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で、**\[Custom Action Project Item\]** の拡張機能を選択し、**\[アンインストール\]** のボタンをクリックします。  
  
3.  表示されたダイアログ ボックスで、拡張機能をアンインストールする選択し、アンインストールを実行するに **\[今すぐ再起動\]** のボタンを選択します。ことを確認するために **\[○\]** のボタンをクリックします。  
  
4.  Visual Studioの実験用インスタンスとインスタンス \(CustomActionProjectItemソリューションが開いている\) Visual Studioの両方のインスタンスのインスタンスを閉じます。  
  
## 参照  
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [方法 : プロジェクト テンプレートを組み合わせたウィザードを使用する](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)   
 [カスタム アクションの既定の場所および ID](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
  