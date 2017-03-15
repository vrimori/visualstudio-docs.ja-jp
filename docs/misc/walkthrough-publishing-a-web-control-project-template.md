---
title: "チュートリアル: Web コントロール プロジェクト テンプレートの発行 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "テンプレート、Web コントロール"
  - "Web コントロール テンプレート"
ms.assetid: b56490f8-38bd-4220-a17e-5ebb30d3ac78
caps.latest.revision: 22
caps.handback.revision: 22
manager: "douge"
---
# チュートリアル: Web コントロール プロジェクト テンプレートの発行
他の Web コントロール プロジェクトの基礎として使用する Web コントロール プロジェクト テンプレートを作成できます。 そのテンプレートを VSIX 拡張機能として配布することもできます。  
  
 VSIX 拡張機能を配布するには、その機能を Visual Studio ギャラリーの Web サイトに追加することをお勧めします。開発者が拡張機能マネージャーを使用して、そのギャラリーで新しい拡張機能や更新された拡張機能を参照できるためです。 また、別のサーバーに配置したり、CD などのメディアに書き込んだりして、拡張機能を配布することもできます。  
  
 このチュートリアル \(関連する 2 つのチュートリアルのうちの 1 つ\) では、Web コントロール プロジェクト テンプレートを作成し、配布する方法について説明します。 もう 1 つのチュートリアル \([チュートリアル: Visual Studio 拡張機能を公開します。](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)\) では、Web コントロールを作成し、配布する方法について説明します。  
  
 このチュートリアルには、次のセクションが含まれています。  
  
-   VSIX 拡張機能での Web コントロール プロジェクト テンプレートの作成  
  
-   Visual Studio ギャラリーへのテンプレートの発行  
  
-   Visual Studio ギャラリーからのテンプレートのインストール  
  
-   インストールしたテンプレートのテスト  
  
-   テンプレートへのデバッグ操作ウィザードの追加  
  
## 必須コンポーネント  
 このチュートリアルを完了するには、Web コントロールを理解し、プロジェクトの作成方法、プロジェクト プロパティの設定方法、および Visual Studio 実験用インスタンスの使用方法を理解する必要があります。 Visual Studio と Visual Studio SDK の両方をコンピューターにインストールする必要があります。 このチュートリアルを開始する前に、[チュートリアル: Visual Studio 拡張機能を公開します。](../extensibility/walkthrough-publishing-a-visual-studio-extension.md) を完了する必要があります。  
  
## VSIX 拡張機能での Web コントロール プロジェクト テンプレートの作成  
 Web コントロール プロジェクト テンプレートを作成するには、まず Web コントロール プロジェクトを作成します。 このチュートリアルでは、「[チュートリアル: Visual Studio 拡張機能を公開します。](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)」で作成した ColorTextControl Web コントロール プロジェクトから開始します。  
  
 プロジェクト テンプレートを Visual Studio ギャラリーに発行する前に、**VSIX としてテンプレートをエクスポート** ウィザードを使用して、VSIX 拡張機能としてテンプレートをエクスポートし、**拡張機能マネージャー**でテンプレートを識別する際に役立つようにテンプレートのアイコンを作成し、さらにテンプレートの機能がわかるようにイメージも作成します。  
  
#### Web コントロール プロジェクトを配布するための準備をするには  
  
1.  Visual Studio で、MyWebControls プロジェクトを開きます。  
  
2.  **拡張機能マネージャー**を使用して、[Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkId=194329)の Web サイトから **\[テンプレートのエクスポート ウィザード\]** をダウンロードします。  
  
     ウィザードのインストール後、プロジェクトを開くと、**\[VSIX としてテンプレートをエクスポート\]** が **\[ファイル\]** メニューに表示されます。  
  
3.  **\[ファイル\]** メニューの **\[VSIX としてテンプレートをエクスポート\]** をクリックします。  
  
     ![&#91;ファイル&#93; メニューの VSIX 形式でプロジェクトをエクスポート](../misc/media/pcwc_exportasvsix.png "PCWC\_ExportAsVsix")  
  
4.  **\[テンプレートの種類の選択\]** ページで、**\[プロジェクト テンプレート\]** を選択し、MyWebControls.csproj を選択します。**\[次へ\]** をクリックします。  
  
     ![プロジェクト テンプレートの選択](../misc/media/pcwc_choosetemplate.png "PCWC\_ChooseTemplate")  
  
5.  **\[テンプレート オプションの選択\]** ページで、**\[テンプレート名\]** を `Extensibility Color Text Web Toolbox Control` に、**\[テンプレートの説明\]** を `Color text web control project that produces a VSIX extension.` に設定します。  
  
6.  **\[アイコン イメージ\]** ボックスの横にある **\[参照\]** をクリックします。**\[ファイル名\]** ボックスに、「`*.*`」と入力します。 Color.bmp を見つけ、**\[開く\]** をクリックします。  
  
7.  **\[プレビュー イメージ\]** ボックスの横にある **\[参照\]** をクリックします。**\[ファイル名\]** ボックスに、「`*.*`」と入力します。 ScreenShot.bmp を見つけ、**\[開く\]** をクリックします。**\[次へ\]** をクリックします。  
  
     ![テンプレート オプションの選択](../misc/media/pcwc_selecttemplateoptions2.png "PCWC\_SelectTemplateOptions2")  
  
8.  **\[VSIX オプションの選択\]** ページで、**\[製品名\]** を `Extensibility Color Text Web Control Template` に変更します。  
  
9. 必要に応じて、**\[会社名\]**、**\[バージョン\]**、**\[ライセンス\]**、および **\[概要ガイドの URL\]** を変更できます。  
  
10. **\[テンプレートを自動的に Visual Studio にインポート\]** オプションをオフにします。**\[完了\]** をクリックします。  
  
     ![&#91;テンプレートを自動的に Visual Studio にインポート&#93; チェック ボックスをオフにする](../misc/media/pcwc_.png "PCWC\_")  
  
     Windows エクスプローラーで、..\\マイ ドキュメント\\Visual Studio *\<バージョン\>*\\My Exported Templates\\ フォルダーに、Extensibility Color Text Web Control Template.vsix が表示されます。  
  
## Visual Studio ギャラリーへのテンプレートの発行  
 これで、プロジェクト テンプレートを Visual Studio ギャラリーに発行する準備ができました。  
  
#### Visual Studio ギャラリーにテンプレートを発行するには  
  
1.  Web ブラウザーで、[Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkId=194329) の Web サイトを開きます。  
  
2.  右上隅の **\[サインイン\]** をクリックします。  
  
3.  Microsoft アカウントを使用してサインインします。 Microsoft アカウントがない場合は、ここで新しいアカウントを作成できます。  
  
4.  **\[アップロード\]** をクリックします。  
  
5.  **\[手順 1: 拡張機能の種類\]** で、**\[プロジェクトまたはアイテム テンプレート\]** を選択し、**\[次へ\]** をクリックします。  
  
6.  **\[手順 2: アップロード\]** で、**\[参照\]** をクリックします。 \\My Exported Templates\\ フォルダーで、Extensibility Color Text Web Control Template.vsix を選択します。**\[次へ\]** をクリックします。  
  
7.  **\[手順 3: 基本情報\]** では、**\[VSIX としてテンプレートをエクスポート ウィザード\]** からの情報が表示されます。  
  
8.  **カテゴリ** を `ASP.NET` に、**タグ** を `toolbox, web control, templates` に設定します。  
  
9. コントリビューション規約に目を通して同意し、表示されているテキストをボックスに入力します。  
  
10. **\[コントリビューションの作成\]** をクリックし、**\[発行\]** をクリックします。  
  
11. Visual Studio ギャラリーで Extensibility Color Text Web Control Template を検索します。 テンプレートの一覧が表示されます。  
  
     ![新しい Web コントロール テンプレートの一覧表示](../misc/media/pcwc_templatelisting.png "PCWC\_TemplateListing")  
  
## Visual Studio ギャラリーからのテンプレートのインストール  
 Web コントロール プロジェクト テンプレートが発行されたので、それを Visual Studio にインストールし、テストします。  
  
#### Visual Studio に Web コントロール プロジェクト テンプレートをインストールするには  
  
1.  Visual Studio の **\[ツール\]** メニューで、**\[拡張機能マネージャー\]** をクリックします。  
  
2.  **\[オンライン ギャラリー\]** をクリックし、Extensibility Color Text Web Control Template を検索します。 テンプレートの一覧が表示されます。  
  
3.  **\[ダウンロード\]** をクリックします。 拡張機能をダウンロードした後、**\[インストール\]** をクリックします。  
  
## インストールしたテンプレートのテスト  
 これで、Extensibility Color Text Web Control プロジェクト テンプレートを使用して、カスタム Web コントロールを作成できます。 各コントロールを手動で作成する必要はありません。 このセクションでは、このテンプレートを使用して、BlueColorTextControl Web コントロールを作成する方法を示します。  
  
#### テンプレートに基づいて Web コントロールを作成するには  
  
1.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
2.  左のウィンドウで、**\[オンライン テンプレート\]** をクリックし、**\[テンプレート\]** を展開し、**\[ASP.NET\]** をクリックします。 中央のウィンドウで、**\[Extensibility Color Text Web Control Template\]** をクリックします。  
  
     ![機能拡張カラー テキスト Web テンプレートの選択](../Image/PCWC_NewProjectTemplate.png "PCWC\_NewProjectTemplate")  
  
3.  **\[名前\]** を `MoreWebControls` に設定します。**\[OK\]** をクリックします。  
  
4.  **ソリューション エクスプローラー**で、ColorTextControl.cs の名前を BlueColorTextControl.cs に変更します。  
  
5.  エディターで BlueColorTextControl.cs をダブルクリックして開きます。  
  
6.  `ToolboxData` 属性で、出現する両方の `ColorTextControl` を `BlueColorTextControl` に置き換えます。  
  
     これらの値では、デザイン時にコントロールを **\[ツールボックス\]** から Web ページにドラッグするとそのコントロール用に生成される開始タグと終了タグを指定します。  値は、コントロール クラスの名前と一致する必要があります。これは、**\[ツールボックス\]** に表示されるコントロールの名前でもあります。  
  
     これで、コントロール クラスのソース コードの先頭部分は次のコードのようになります。  
  
    ```  
    namespace MoreWebControls { [DefaultProperty("Text")] [ToolboxData("<{0}:BlueColorTextControl runat=server> </{0}:BlueColorTextControl>")] [ProvideToolboxControl("MoreWebControls", false)] public class BlueColorTextControl : WebControl {  
  
    ```  
  
7.  `get` メソッドで、`color:green` を `color:blue` に変更します。  
  
    ```  
    get { String s = (String)ViewState["Text"]; return "<span style='color:blue'>" + s + "</span>"; }  
    ```  
  
     これはテキストを span タグにラップして、テキストを青色にします。  
  
8.  MoreWebControls プロジェクトをビルドします。  
  
## 新しい Web コントロールのテスト  
 ここで、新しい Web コントロールが **\[ツールボックス\]** で利用可能かどうかをテストできます。 ただし、MoreWebControls プロジェクトを開いて、F5 キーを押しても、コントロールをテストするための Visual Studio の実験用インスタンスは開始しません。 このようになるのは、プロジェクトが Extensibility Color Text Web Control Template に基づいており、このテンプレートではデバッグ操作をまだ設定できないためです。 \(次のセクションでは、デバッグ操作を設定するウィザードをテンプレートに追加する方法を示しています。\) ここでは、コントロールをテストするには、次の手順に従います。  
  
#### 新しい Web コントロールをテストするには  
  
1.  Visual Studio の実験用インスタンスを開くには、実験用インスタンスを開始します。  
  
    1.  [!INCLUDE[win7](../debugger/includes/win7_md.md)] で、**\[スタート\]** メニューを使用します \(**\[スタート\]\/\[すべてのプログラム\]\/\[Microsoft Visual Studio \<バージョン\> SDK\]\/\[ツール\]\/\[Start Experimental Instance of Microsoft Visual Studio \<バージョン\>\]**\)。  
  
    2.  [!INCLUDE[win81](../debugger/includes/win81_md.md)] の **\[スタート\]** 画面で、「**Start Experimental Instance of Microsoft Visual Studio \<version\>**」と入力します。  
  
2.  Web アプリケーション プロジェクトを作成します。  
  
3.  プロジェクトで、default.aspx を開きます。**\[ソース\]** ビューが表示されることを確認します。  
  
4.  **\[ツールボックス\]** の **\[MoreWebControls\]** カテゴリに、**BlueColorTextControl** が表示されます。  
  
     ![MoreWebControls に表示された BlueColorTextControl](../Image/PCWC_Toolbox2.png "PCWC\_Toolbox2")  
  
5.  Web ページの `body` タグ内のどこかに BlueColorTextControl をドラッグします。  
  
6.  `ColorTextControl` タグで、`Text` 属性を追加し、その値を `Think Blue!` にします。 その結果生成されるタグは、次のようになります。  
  
    ```  
    <cc1:BlueColorTextControl ID="BlueColorTextControl1" Text="Think Blue!" runat="server" />  
  
    ```  
  
7.  F5 キーを押して、ASP.NET 開発サーバーを起動します。  
  
     BlueColorTextControl の表示は次の図のようになります。  
  
     ![BlueColorTextControl で読み込まれた Think Blue](../misc/media/pcwc_thinkblue.png "PCWC\_ThinkBlue")  
  
8.  ASP.NET 開発サーバーを終了します。  
  
9. Visual Studio の実験用インスタンスを終了します。  
  
## テンプレートへのデバッグ操作ウィザードの追加  
 前のセクションで説明したように、MoreWebControls プロジェクトが開いているときに F5 キーを押しても、Visual Studio の実験用インスタンスは開かれません。 その代わりに、"出力の種類がクラス ライブラリのプロジェクトを直接起動することはできません。" というメッセージが表示されます。 このことは、実験用インスタンスの位置がプロジェクトで認識されない場合に発生します。 ただし、テンプレートで、ターゲット コンピューターでの実験用インスタンスの場所を特定し、適切なデバッグ操作を設定できるようにすることができます。 これにより、コンピューター上の、そのテンプレートに基づくすべてのプロジェクトが、F5 キーに対して想定どおりに応答するようになります。  
  
 Visual Studio SDK に含まれるすべての機能拡張プロジェクト テンプレートには、インストール時に動作し、ターゲット コンピューター上の実験用インスタンスの場所を特定し、デバッグ操作を設定するウィザードが含まれています。 これを行うための独自のウィザードを作成して、配布するすべてのテンプレートに組み込むことができます。  
  
 Extensibility Color Text Web Control Template にデバッグ操作ウィザードを追加するには、テンプレートの最初のバージョンをいったん削除し、ウィザードを追加してから再作成する必要があります。  
  
#### テンプレートの最初のバージョンを削除するには  
  
1.  Visual Studio ギャラリーの Web サイトで、左上隅にある **\[マイ コントリビューション\]** をクリックします。**\[Extensibility Color Text Web Control Template\]** の一覧が表示されます。  
  
2.  Visual Studio ギャラリーからプロジェクト テンプレートを完全に削除するには、**\[削除\]** をクリックします。  
  
3.  Visual Studio の **\[ツール\]** メニューで、**\[拡張機能マネージャー\]** をクリックします。  
  
4.  **\[Extensibility Color Text Web Control Template\]** を選択し、**\[アンインストール\]** をクリックします。  
  
5.  **拡張機能マネージャー**を閉じます。  
  
6.  MoreWebControls ソリューションを閉じます。  
  
7.  Visual Studio を閉じます。  
  
8.  MoreWebControls ソリューション フォルダーを削除します。  
  
9. アンインストール プロセスを完了するには、Visual Studio を再起動します。  
  
 デバッグ操作ウィザードには `Microsoft.VisualStudio.TemplateWizard.IWizard` のパブリックな実装が必要であり、厳密なアセンブリ名を使用して署名する必要があります。  
  
#### デバッグ操作ウィザードを作成するには  
  
1.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**Visual C\#**、**Windows**、**クラス ライブラリ** プロジェクトを作成し、`MyWizard` という名前を付けます。  
  
2.  この新しいプロジェクトで、class1.cs を MyWizard.cs という名前に変更します。  
  
3.  MyWizard.cs の内容を次のコードに置き換えます。  
  
    ```  
    using System; using System.Collections.Generic; using System.Linq; using System.Text; using Microsoft.VisualStudio.TemplateWizard; using System.Globalization; using EnvDTE; namespace MyWizard { public class MyWizard : IWizard { public void BeforeOpeningFile(ProjectItem projectItem) { } public void ProjectFinishedGenerating(Project project) { foreach (Configuration config in project.ConfigurationManager) { //Set up the debug options to run "devenv /rootsuffix Exp"; config.Properties.Item("StartAction").Value = 1; //Get the full path to devenv.exe through DTE.FullName config.Properties.Item("StartProgram").Value = project.DTE.FullName; config.Properties.Item("StartArguments").Value = "/rootsuffix Exp"; } } public void ProjectItemFinishedGenerating(ProjectItem projectItem) { } public void RunFinished() { } public void RunStarted(object automationObject, Dictionary<string, string> replacementsDictionary, WizardRunKind runKind, object[] customParams) { } public bool ShouldAddProjectItem(string filePath) { return true; } } }  
  
    ```  
  
4.  プロジェクトに次の参照を追加します。 複数の選択肢がある場合は、[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] へのパスを持つ参照を選択します。  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
5.  MyWizard プロジェクトを右クリックし、**\[プロパティ\]** をクリックします。**\[署名\]** タブの **\[アセンブリの署名\]** オプションを選択します。  
  
6.  **\[厳密な名前のキー ファイルを選択してください\]** ボックスの一覧で **\[\<新規作成...\>\]** を選択します。**\[厳密な名前キーの作成\]** ダイアログ ボックスが表示されます。  
  
7.  **\[キー ファイル\]** を `key.snk` に設定し、**\[キー ファイルをパスワードで保護する\]** オプションをオフにします。  
  
     ![キー ファイルの指定](../misc/media/pcwc_strongname.png "PCWC\_StrongName")  
  
8.  **\[OK\]** をクリックして key.snk をプロジェクトに追加します。  
  
9. MyWizard プロジェクトをリリース ビルドとしてビルドします。 これでウィザードを使用する準備ができました。  
  
10. MyWizard ソリューションを閉じます。  
  
#### ウィザードを組み込み、テンプレートを再作成するには  
  
1.  前のセクション「VSIX 拡張機能での Web コントロール プロジェクト テンプレートの作成」の手順に従いますが、次の追加と変更を行います。  
  
    -   **\[VSIX としてテンプレートをエクスポート\]** ウィザードをもう一度ダウンロードする必要はありません。  
  
    -   **\[VSIX としてテンプレートをエクスポート\]** ウィザードの **\[VSIX オプションの選択\]** ページの **\[ウィザード\]** ボックスで、前の手順で作成した \\bin\\Release\\MyWizard.dll ファイルを探して選択します。  
  
         ![ウィザード アセンブリの指定](../misc/media/pcwc_wizardassembly.png "PCWC\_WizardAssembly")  
  
    -   既存の VSIX 拡張機能出力ファイルを上書きするメッセージが表示されたら、**\[はい\]** をクリックします。  
  
2.  「新しい Web コントロールのテスト」セクションに到達したら、F5 キーを押します。 Visual Studio の実験用インスタンスが開始します。  
  
## 次の手順  
 このチュートリアルでは、**\[VSIX としてテンプレートをエクスポート\]** ウィザードを使用して、プロジェクト テンプレートを作成し、配布する方法を示しました。**\[新しいプロジェクト\]** ダイアログ ボックスに表示されるアイコンを選択するなど、プロジェクト テンプレートをより詳細に制御する必要がある場合は、プロジェクト テンプレートを明示的に作成して VSIX 拡張機能にラップする必要があります。 詳細については、Visual Studio Blog の Web サイトの「[Creating and Sharing Project & Item Templates \(プロジェクトおよびアイテム テンプレートの作成と共有\)](http://go.microsoft.com/fwlink/?LinkId=194551)」を参照してください。  
  
## 参照  
 [Visual Studio 拡張機能を配布](../extensibility/shipping-visual-studio-extensions.md)