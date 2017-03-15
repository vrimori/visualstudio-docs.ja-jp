---
title: "方法 : プロジェクト テンプレートを組み合わせたウィザードを使用する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IWizard インターフェイス"
  - "プロジェクト テンプレート [Visual Studio], ウィザード"
  - "テンプレート [Visual Studio], ウィザード"
  - "Visual Studio のテンプレート, ウィザード"
  - "ウィザード [Visual Studio], プロジェクト テンプレート"
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 方法 : プロジェクト テンプレートを組み合わせたウィザードを使用する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio には、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスが用意されています。このインターフェイスを実装すると、ユーザーがテンプレートからプロジェクトを作成する際にカスタム コードを実行できるようになります。  
  
 プロジェクト テンプレートのカスタマイズを使用すると、次の操作を実行できます。  
  
-   ユーザー入力を収集してテンプレートをパラメーター化するカスタム UI を表示できます。  
  
-   テンプレートで使用するパラメーター値を追加できます。  
  
-   テンプレートに他のファイルを追加できます。  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] オートメーション オブジェクト モデルによって許可されたアクションを実際にプロジェクトで実行できます。  
  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイス メソッドは、プロジェクトの作成中にさまざまな時点で呼び出されます。プロジェクトの作成は、ユーザーが **\[新しいプロジェクト\]** ダイアログ ボックスの **\[OK\]** をクリックすると同時に開始されます。  インターフェイスの各メソッドには、そのメソッドが呼び出される時点を表す名前が付けられます。  たとえば、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、プロジェクトの作成の開始直後に <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> を呼び出します。この時点が、ユーザー入力を収集するためのカスタム コードの記述に適した場所になります。  
  
 カスタム ウィザード用に記述するコードのほとんどでは、<xref:EnvDTE.DTE> オブジェクトを使用します。このオブジェクトは、プロジェクトをカスタマイズするための、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] オートメーション オブジェクト モデルの主要なオブジェクトです。  オートメーション オブジェクト モデルの詳細については、「[Extending the Visual Studio Environment](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)」および「[Automation and Extensibility Reference](../Topic/Automation%20and%20Extensibility%20Reference.md)」を参照してください。  
  
## カスタム テンプレート ウィザードの作成  
 このトピックでは、プロジェクトを作成する前に Windows フォームを開くカスタム ウィザードを作成する方法を紹介します。  このフォームを使用すると、ユーザーは、プロジェクトの作成時にソース コードに後から追加されるカスタム パラメーター値を追加できます。  主な手順を次に示し、各手順の詳細について説明します。  
  
#### カスタム テンプレート ウィザードを作成するには  
  
1.  <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスを実装するアセンブリを作成します。  
  
2.  アセンブリをグローバル アセンブリ キャッシュにインストールします。  
  
3.  プロジェクトを作成し、**テンプレートのエクスポート** ウィザードを使用して、そのプロジェクトからテンプレートを作成します。  
  
4.  テンプレートを変更します。ここでは、.vstemplate ファイルに `WizardExtension` 要素を追加し、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> を実装するアセンブリにテンプレートをリンクします。  
  
5.  カスタム ウィザードを使用し、新しいプロジェクトを作成します。  
  
## IWizard の実装  
 このプロセスでは、最初に、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> を実装するアセンブリを作成します。  このアセンブリは、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> メソッドを使用し、ユーザーがカスタム パラメーター値を追加できる Windows フォームを表示します。このパラメーター値は、プロジェクトの作成時に使用されます。  
  
> [!NOTE]
>  この例では、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> の実装に [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] を使用していますが、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] を使用することもできます。  
  
#### IWizard を実装するには  
  
1.  新しいクラス ライブラリ プロジェクトを作成します。  
  
2.  <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスを実装するクラスを作成します。  完全に実装された <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスの [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] の例については、後述のコードを参照してください。  
  
 この例には、2 つのコード ファイルが含まれています。1 つは、`IWizardImplementation` という、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスを実装するクラスで、もう 1 つは、`UserInputForm` という、ユーザー入力用の Windows フォームです。  
  
### IWizardImplementation クラス  
 `IWizardImplementation` クラスには、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> のすべてのメンバーに対するメソッドの実装が含まれています。  この例では、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> メソッドだけがタスクを実行します。  他のすべてのメソッドは、何もしないか、`true` を返します。  
  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> メソッドは、次の 4 つのパラメーターを受け取ります。  
  
-   <xref:System.Object> パラメーター。プロジェクトをカスタマイズできるように、ルートの <xref:EnvDTE._DTE> オブジェクトにキャストできます。  
  
-   <xref:System.Collections.Generic.Dictionary%602> パラメーター。テンプレートで定義済みのすべてのパラメーターのコレクションが含まれます。  テンプレート パラメーターの詳細については、「[テンプレート名](../ide/template-parameters.md)」を参照してください。  
  
-   <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> パラメーター。使用されているテンプレートの種類に関する情報が含まれます。  
  
-   <xref:System.Object> 配列。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によってウィザードに渡される一連のパラメーターが格納されます。  
  
 この例では、ユーザー入力フォームから <xref:System.Collections.Generic.Dictionary%602> パラメーターにパラメーター値を追加します。  プロジェクト内の `$custommessage$` パラメーターのすべてのインスタンスは、ユーザーが入力したテキストと置き換えられます。  以下のアセンブリをプロジェクトに追加する必要があります。  
  
1.  EnvDTE.dll  
  
2.  Microsoft.VisualStudio.TemplateWizardInterface.dll  
  
3.  System.Windows.Forms.dll  
  
> [!IMPORTANT]
>  この例で使用されている UserInputForm は、次のセクションで定義されています。  
  
```c#  
using System;  
using System.Collections.Generic;  
using Microsoft.VisualStudio.TemplateWizard;  
using System.Windows.Forms;  
using EnvDTE;  
  
namespace CustomWizard  
{  
    public class IWizardImplementation:IWizard  
    {  
        private UserInputForm inputForm;  
        private string customMessage;  
  
        // This method is called before opening any item that   
        // has the OpenInEditor attribute.  
        public void BeforeOpeningFile(ProjectItem projectItem)  
        {  
        }  
  
        public void ProjectFinishedGenerating(Project project)  
        {  
        }  
  
        // This method is only called for item templates,  
        // not for project templates.  
        public void ProjectItemFinishedGenerating(ProjectItem   
            projectItem)  
        {  
        }  
  
        // This method is called after the project is created.  
        public void RunFinished()  
        {  
        }  
  
        public void RunStarted(object automationObject,  
            Dictionary<string, string> replacementsDictionary,  
            WizardRunKind runKind, object[] customParams)  
        {  
            try  
            {  
                // Display a form to the user. The form collects   
                // input for the custom message.  
                inputForm = new UserInputForm();  
                inputForm.ShowDialog();  
  
                customMessage = inputForm.get_CustomMessage();  
  
                // Add custom parameters.  
                replacementsDictionary.Add("$custommessage$",   
                    customMessage);  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.ToString());  
            }  
        }  
  
        // This method is only called for item templates,  
        // not for project templates.  
        public bool ShouldAddProjectItem(string filePath)  
        {  
            return true;  
        }          
    }  
}  
```  
  
### ユーザー入力フォーム  
 ユーザー入力フォームには、カスタム パラメーターを入力するための簡単なフォームが用意されています。  このフォームには、`textBox1` という名前のテキスト ボックスおよび `button1` という名前のボタンがあります。  このボタンをクリックすると、テキスト ボックスのテキストが `customMessage` パラメーターに格納されます。  
  
##### Windows フォームをソリューションに追加するには  
  
1.  ウィザード実装が含まれるファイルに次のコードを追加します。  
  
```c#  
public partial class UserInputForm : Form  
{  
    private string customMessage;  
    private TextBox textBox1;  
  
    public UserInputForm()  
    {   
        textBox1 = new TextBox();  
        this.Controls.Add(textBox1);  
    }  
  
    public string get_CustomMessage()  
    {  
        return customMessage;  
    }  
  
    private void textBox1_TextChanged(object sender, EventArgs e)  
    {  
        customMessage = textBox1.Text;  
        this.Dispose();  
    }  
}  
```  
  
## グローバル アセンブリ キャッシュへのアセンブリのインストール  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> を実装するアセンブリは、厳密な名前で署名して、グローバル アセンブリ キャッシュにインストールする必要があります。  
  
#### アセンブリをグローバル アセンブリ キャッシュにインストールするには  
  
1.  アセンブリに厳密な名前で署名します。  詳細については、「[方法 : 厳密な名前でアセンブリに署名する](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md)」または「[How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/f468a7d3-234c-4353-924d-8e0ae5896564)」を参照してください。  
  
2.  厳密な名前付きアセンブリをグローバル アセンブリ キャッシュにインストールします。  詳細については、「[方法 : グローバル アセンブリ キャッシュにアセンブリをインストールする](../Topic/How%20to:%20Install%20an%20Assembly%20into%20the%20Global%20Assembly%20Cache.md)」を参照してください。  
  
## テンプレートとして使用するプロジェクトの作成  
 この例でテンプレートとして使用されるプロジェクトは、カスタム ウィザードのユーザー入力フォームで指定されたメッセージを表示するコンソール アプリケーションです。  
  
#### サンプル プロジェクトを作成するには  
  
1.  [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] コンソール アプリケーションを新しく作成します。  
  
2.  アプリケーションの `Main` メソッドに次のコード行を追加します。  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     `$custommessage$` パラメーターは、プロジェクトをテンプレートから作成する際にユーザー入力フォームに入力したテキストで置き換えられます。  
  
3.  **\[ファイル\]** メニューの **\[テンプレートのエクスポート\]** をクリックします。  
  
4.  **テンプレートのエクスポート** ウィザードで、**\[プロジェクト テンプレート\]** をクリックし、適切なプロジェクトを選択して、**\[次へ\]** をクリックします。  
  
5.  **テンプレートのエクスポート** ウィザードで、テンプレートの説明情報を入力します。**\[テンプレートを自動的に Visual Studio にインポート\]** チェック ボックスをオンにし、**\[完了\]** をクリックします。  
  
     これで、テンプレートは **\[新しいプロジェクト\]** ダイアログ ボックスに表示されるようになりますが、カスタム ウィザードは使用しません。  
  
 テンプレートにエクスポートされる前のコード ファイル全体の例を次に示します。  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
namespace TemplateProject  
{  
    class WriteMessage  
    {  
        static void Main(string[] args)  
        {  
            Console.WriteLine("$custommessage$");  
        }  
    }  
}  
```  
  
## テンプレートの変更  
 テンプレートが作成され、**\[新しいプロジェクト\]** ダイアログ ボックスに表示されたら、前の手順で作成したアセンブリを使用するように、そのテンプレートを変更する必要があります。  
  
#### カスタム ウィザードをテンプレートに追加するには  
  
1.  テンプレートを含む .zip ファイルを探します。  
  
    1.  **\[ツール\]** メニューの **\[オプション\]** をクリックします。  
  
    2.  **\[プロジェクトおよびソリューション\]** をクリックします。  
  
    3.  **\[Visual Studio ユーザー プロジェクト テンプレートの場所\]** ボックスを確認します。  
  
     既定の場所は、My Documents\\Visual Studio *Version*\\Templates\\ProjectTemplates です。  
  
2.  .zip ファイルを展開します。  
  
3.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で .vstemplate ファイルを開きます。  
  
4.  `TemplateContent` 要素の後に、カスタム ウィザード アセンブリの厳密な名前の付いた [WizardExtension 要素 \(Visual Studio テンプレート\)](../extensibility/wizardextension-element-visual-studio-templates.md) 要素を追加します。  アセンブリの厳密な名前を検索する方法の詳細については、「[方法 : グローバル アセンブリ キャッシュの内容を表示する](../Topic/How%20to:%20View%20the%20Contents%20of%20the%20Global%20Assembly%20Cache.md)」および「[方法 : 厳密な名前のアセンブリを参照する](../Topic/How%20to:%20Reference%20a%20Strong-Named%20Assembly.md)」を参照してください。  
  
     `WizardExtension` 要素の例を次に示します。  
  
    ```  
    <WizardExtension>  
        <Assembly>CustomWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=fa3902f409bb6a3b</Assembly>  
        <FullClassName>CustomWizard.IWizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
## カスタム ウィザードの使用  
 これで、テンプレートからプロジェクトを作成し、カスタム ウィザードを使用できるようになりました。  
  
#### カスタム ウィザードを使用するには  
  
1.  **\[ファイル\]** メニューの **\[新しいプロジェクト\]** をクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスで、テンプレートを指定し、名前を入力して、**\[OK\]** をクリックします。  
  
     ウィザードのユーザー入力フォームが開きます。  
  
3.  カスタム パラメーターの値を入力し、ボタンをクリックします。  
  
     ウィザードのユーザー入力フォームが終了し、プロジェクトがテンプレートから作成されます。  
  
4.  **ソリューション エクスプローラー**で、ソース コード ファイルを右クリックし、**\[コードの表示\]** をクリックします。  
  
     `$custommessage$` は、ウィザードのユーザー入力フォームに入力されたテキストで置き換えられています。  
  
## 参照  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
 [テンプレートのカスタマイズ](../ide/customizing-project-and-item-templates.md)   
 [WizardExtension 要素 \(Visual Studio テンプレート\)](../extensibility/wizardextension-element-visual-studio-templates.md)