---
title: "方法: プロジェクト テンプレートを使用してウィザードを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8eef98d11f98e3db8216c69dcfacf478c676a837
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="how-to-use-wizards-with-project-templates"></a>方法 : プロジェクト テンプレートを組み合わせたウィザードを使用する
Visual Studio には、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスが用意されています。このインターフェイスを実装すると、ユーザーがテンプレートからプロジェクトを作成する際にカスタム コードを実行できるようになります。  
  
 プロジェクトのテンプレートをカスタマイズする、テンプレートに追加のファイルを追加するユーザー入力または許可された他のアクションを収集するカスタム UI を表示するのには、プロジェクト テンプレートのカスタマイズを使用できます。  
  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>ユーザーがクリックするとすぐに開始、プロジェクトの作成中に、さまざまなタイミングでインターフェイス メソッドが呼び出されます**OK**上、**新しいプロジェクト** ダイアログ ボックス。 インターフェイスの各メソッドには、そのメソッドが呼び出される時点を表す名前が付けられます。 たとえば、Visual Studio は<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>プロジェクトを作成、開始時、すぐにことがユーザー入力を収集するためのカスタム コードを記述する適切な位置です。  
  
## <a name="creating-a-project-template-project-with-a-vsix-project"></a>VSIX プロジェクトをプロジェクト テンプレート プロジェクトを作成します。  
 まず、プロジェクト テンプレートにプロジェクトを Visual Studio SDK の一部では、カスタム テンプレートを作成します。 この手順では、c# プロジェクト テンプレート プロジェクトを使用しますも、Visual Basic プロジェクト テンプレート プロジェクトがあります。 VSIX プロジェクトは、プロジェクト テンプレート プロジェクトを含むソリューションに追加します。  
  
1.  C# プロジェクト テンプレート プロジェクトを作成する (Visual Studio で、**ファイル > 新規 > プロジェクト > Visual c# > Extensibility > c# プロジェクト テンプレート**)。 名前を付けます**MyProjectTemplate**です。  
  
    > [!NOTE]
    >  Visual Studio SDK をインストールする要求があります。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
2.  新しい VSIX プロジェクトの追加 (**ファイル > 新規 > プロジェクト > Visual c# > Extensibility > VSIX プロジェクト**) プロジェクト テンプレートと同じソリューションで (で、**ソリューション エクスプ ローラー**を選択、ソリューション ノードを右クリックし、**追加 > 新しいプロジェクト**)。 名前を付けます**MyProjectWizard です。**  
  
3.  VSIX プロジェクトをスタートアップ プロジェクトとして設定します。 **ソリューション エクスプ ローラー**、選択、VSIX プロジェクト ノードを右クリックし、**スタートアップ プロジェクトとして設定**です。  
  
4.  VSIX プロジェクトのアセットとしてテンプレート プロジェクトを追加します。 **ソリューション エクスプ ローラー**、VSIX プロジェクト ノードの下を検索、 **source.extension.vsixmanifest**ファイル。 マニフェスト エディターで開きをダブルクリックします。  
  
5.  マニフェスト エディターで、選択、**資産**ウィンドウの左側にあるタブ。  
  
6.  **資産**] タブで [**新規**です。 **新しいアセットの追加**ウィンドウの種類 フィールドに対して**microsoft.visualstudio.projecttemplate**です。 **ソース**フィールドで、**現在のソリューション内のプロジェクト**です。 **プロジェクト**フィールドで、 **MyProjectTemplate**です。 次に、 **[OK]**をクリックします。  
  
7.  ソリューションをビルドし、デバッグを開始します。 Visual Studio の 2 番目のインスタンスが表示されます。 (これは数分をかかります。)  
  
8.  Visual Studio の 2 番目のインスタンスで、新しいテンプレートを使用して新しいプロジェクトを作成してください。 (**ファイル > 新しい > プロジェクト > Visual c# > MyProject テンプレート**)。 新しいプロジェクトがという名前のクラスを表示する必要があります**Class1**です。 カスタム プロジェクト テンプレートが作成されました! 今すぐデバッグを停止します。  
  
## <a name="creating-a-custom-template-wizard"></a>カスタム テンプレート ウィザードの作成  
 このトピックでは、プロジェクトを作成する前に Windows フォームを開くカスタム ウィザードを作成する方法を紹介します。 フォームでは、プロジェクトの作成時、ソース コードに追加されているカスタム パラメーター値を追加することができます。  
  
1.  アセンブリを作成することを許可する VSIX プロジェクトを設定します。  
  
2.  **ソリューション エクスプ ローラー**、VSIX プロジェクト ノードを選択します。 ソリューション エクスプ ローラーで、以下が表示されます、**プロパティ**ウィンドウです。 そうしないと場合、は、選択**ビュー > プロパティ ウィンドウ**、またはキーを押して**F4**です。 [プロパティ] ウィンドウで、次のフィールドを選択`true`:  
  
    -   **IncludeAssemblyInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInLocalVSIXDeployment**  
  
3.  VSIX プロジェクトを資産として、アセンブリを追加します。 Source.extension.vsixmanifest ファイルを開き、選択、**資産**タブです。**新しいアセットの追加** ウィンドウの**型**選択**microsoft.visualstudio.assembly**の**ソース**選択**A現在のソリューションでプロジェクト**、および**プロジェクト**選択**MyProjectWizard**です。  
  
4.  次の参照を VSIX プロジェクトを追加します。 (で、**ソリューション エクスプ ローラー**、VSIX の下のプロジェクト ノードを選択**参照**、右クリックし、**参照の追加**)。**参照の追加**ダイアログで、 **Framework**  タブで、検索、 **System.Windows フォーム**アセンブリを選択します。 選択できるよう、**拡張**タブ検索、 **EnvDTE**アセンブリを選択します。 見つけることも、 **Microsoft.VisualStudio.TemplateWizardInterface**アセンブリを選択します。 **[OK]**をクリックします。  
  
5.  VSIX プロジェクトに、ウィザード実装のクラスを追加します。 (ソリューション エクスプ ローラーでは、VSIX プロジェクト ノードを右クリックして**追加**、し**新しい項目の**、し**クラス**)。クラスの名前を付けます**WizardImplementation**です。  
  
6.  コードで置き換え、 **WizardImplementationClass.cs**を次のコード ファイル。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.TemplateWizard;  
    using System.Windows.Forms;  
    using EnvDTE;  
  
    namespace MyProjectWizard  
    {  
        public class WizardImplementation:IWizard  
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
  
                    customMessage = UserInputForm.CustomMessage;  
  
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
  
     **UserInputForm**これで参照されているコードは後で実装されます。  
  
     `WizardImplementation` クラスには、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> のすべてのメンバーに対するメソッドの実装が含まれています。 この例では、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> メソッドだけがタスクを実行します。 他のすべてのメソッドは、何もしないか、`true` を返します。  
  
     <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> メソッドは、次の 4 つのパラメーターを受け取ります。  
  
    -   <xref:System.Object> パラメーター。プロジェクトをカスタマイズできるように、ルートの <xref:EnvDTE._DTE> オブジェクトにキャストできます。  
  
    -   <xref:System.Collections.Generic.Dictionary%602> パラメーター。テンプレートで定義済みのすべてのパラメーターのコレクションが含まれます。 テンプレート パラメーターの詳細については、次を参照してください。[テンプレート パラメーター](../ide/template-parameters.md)です。  
  
    -   <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> パラメーター。使用されているテンプレートの種類に関する情報が含まれます。  
  
    -   <xref:System.Object> Visual Studio によって、ウィザードに渡されたパラメーターのセットを含む配列。  
  
     この例では、ユーザー入力フォームから <xref:System.Collections.Generic.Dictionary%602> パラメーターにパラメーター値を追加します。 プロジェクト内の `$custommessage$` パラメーターのすべてのインスタンスは、ユーザーが入力したテキストと置き換えられます。 次のアセンブリをプロジェクトに追加する必要があります:**システム**と**System.Drawing**です。
  
7.  ここで作成、 **UserInputForm**です。 **WizardImplementation.cs**ファイルに終了した後、次のコードを追加、 **WizardImplementation**クラスです。  
  
    ```csharp  
    public partial class UserInputForm : Form  
        {  
            private static string customMessage;  
            private TextBox textBox1;  
            private Button button1;  
  
            public UserInputForm()  
            {  
                this.Size = new System.Drawing.Size(155, 265);   
  
                button1 = new Button();  
                button1.Location = new System.Drawing.Point(90, 25);  
                button1.Size = new System.Drawing.Size(50, 25);  
                button1.Click += button1_Click;  
                this.Controls.Add(button1);  
  
                textBox1 = new TextBox();  
                textBox1.Location = new System.Drawing.Point(10, 25);  
                textBox1.Size = new System.Drawing.Size(70, 20);  
                this.Controls.Add(textBox1);  
            }  
            public static string CustomMessage  
            {  
                get  
                {  
                    return customMessage;  
                }  
                set  
                {  
                    customMessage = value;  
                }     
            }  
            private void button1_Click(object sender, EventArgs e)  
            {  
                customMessage = textBox1.Text;  
                this.Close();
            }  
        }  
    ```  
  
     ユーザー入力フォームには、カスタム パラメーターを入力するための簡単なフォームが用意されています。 このフォームには、`textBox1` という名前のテキスト ボックスおよび `button1` という名前のボタンがあります。 このボタンをクリックすると、テキスト ボックスのテキストが `customMessage` パラメーターに格納されます。  
  
## <a name="connect-the-wizard-to-the-custom-template"></a>カスタム テンプレートにウィザードを接続します。  
 カスタム ウィザードを使用するようにカスタム プロジェクト テンプレートの順番は、ウィザード アセンブリに署名し、新しいプロジェクトの作成時に、ウィザード実装の検索場所を把握できるようにする、カスタム プロジェクト テンプレートをいくつかの行を追加する必要があります。  
  
1.  アセンブリに署名します。 **ソリューション エクスプ ローラー**、選択、VSIX プロジェクトを右クリックし、**プロジェクト プロパティ**です。  
  
2.  **プロジェクトのプロパティ**ウィンドウで、**署名** タブで、**署名** タブで、チェック**アセンブリに署名**です。 **厳密な名前キー ファイルを選択して**フィールドで、 **\<新規 >**です。 **厳密な名前キーの作成** ウィンドウで、**キー ファイル名**フィールドに「 **key.snk**です。 オフにして、**キーファイルをパスワードで保護する**フィールドです。  
  
3.  **ソリューション エクスプ ローラー**、VSIX プロジェクトを選択して、検索、**プロパティ**ウィンドウです。  
  
4.  設定、**ビルド出力を出力ディレクトリのコピー**フィールドを**true**です。 これにより、アセンブリをソリューションが再構築の出力ディレクトリにコピーします。 引き続き、.vsix ファイルに含まれています。 その署名キーを確認するために、アセンブリを参照する必要があります。  
  
5.  ソリューションをリビルドします。  
  
6.  MyProjectWizard プロジェクト ディレクトリにようになりました key.snk ファイルを見つけることができます (**\<ディスクの場所 > \MyProjectTemplate\MyProjectWizard\key.snk**)。 Key.snk ファイルをコピーします。  
  
7.  出力ディレクトリに移動し、アセンブリを検索 (**\<ディスクの場所 > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll**)。 ここで、key.snk ファイルを貼り付けます。 (これは絶対に必要なこれは、次の手順やすくするため)。  
  
8.  コマンド ウィンドウを開き、アセンブリが作成されたディレクトリに変更します。  
  
9. 検索、 **sn.exe**署名ツールです。 たとえば、Windows 10 64 ビット オペレーティング システムで一般的なパスの次ようになります  
  
     **C:\Program Files (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 ツール**  
  
     このツールを見つけられない場合実行してみてください**場所/R です。 sn.exe**コマンド ウィンドウでします。 パスをメモしてをおきます。  
  
10. Key.snk ファイルから公開キーを抽出します。 コマンド ウィンドウで次のように入力します。  
  
     **\<sn.exe の場所 > \sn.exe-p key.snk outfile.key です。**  
  
     ディレクトリ名にスペースがある場合は、引用符で囲まれます sn.exe のパスを囲むように注意してください。  
  
11. 出力ファイルから公開キー トークンを取得します。  
  
     **\<sn.exe の場所 > \sn.exe-t outfile.key です。**  
  
     引用符をもう一度、忘れないでください。 次のような出力に行を表示する必要があります。  
  
     **公開キー トークンは、します。<token>**  
  
     この値をメモしてをおきます。  
  
12. カスタム ウィザードへの参照をプロジェクト テンプレートの .vstemplate ファイルに追加します。 ソリューション エクスプ ローラーで MyProjectTemplate.vstemplate、という名前のファイルを検索し、開きます。 終了した後、 \<TemplateContent > セクションで、次のセクションを追加します。  
  
    ```xml  
    <WizardExtension>  
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>  
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
     ここで**MyProjectWizard** 、アセンブリの名前を指定および**トークン**前の手順でコピーしたトークンです。  
  
13. プロジェクト内のすべてのファイルを保存し、再構築します。  
  
## <a name="adding-the-custom-parameter-to-the-template"></a>テンプレートへのカスタム パラメーターの追加  
 この例では、テンプレートとして使用されるプロジェクトは、カスタム ウィザードのユーザー入力フォームで指定したメッセージを表示します。  
  
1.  ソリューション エクスプ ローラーに移動、 **MyProjectTemplate**プロジェクトから開き**Class1.cs**です。  
  
2.  アプリケーションの `Main` メソッドに次のコード行を追加します。  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     `$custommessage$` パラメーターは、プロジェクトをテンプレートから作成する際にユーザー入力フォームに入力したテキストで置き換えられます。  
  
 テンプレートにエクスポートされた前に、完全なコード ファイルを次に示します。  
  
```csharp  
using System;  
using System.Collections.Generic;  
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;  
$endif$using System.Text;  
  
namespace $safeprojectname$  
{  
    public class Class1  
    {  
          static void Main(string[] args)  
          {  
               Console.WriteLine("$custommessage$");  
          }  
    }  
}  
```  
  
## <a name="using-the-custom-wizard"></a>カスタム ウィザードの使用  
 これで、テンプレートからプロジェクトを作成し、カスタム ウィザードを使用できるようになりました。  
  
1.  ソリューションをリビルドし、デバッグを開始します。 Visual Studio の 2 番目のインスタンスが表示されます。  
  
2.  新しい MyProjectTemplate プロジェクトを作成します。 (**ファイル > 新しい > プロジェクト > Visual c# > MyProjectTemplate**)  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、テンプレート、名前を入力を見つけてクリックして**OK**です。  
  
     ウィザードのユーザー入力フォームが開きます。  
  
4.  カスタム パラメーターの値を入力し、ボタンをクリックします。  
  
     ウィザードのユーザー入力フォームが終了し、プロジェクトがテンプレートから作成されます。  
  
5.  **ソリューション エクスプ ローラー**をソース コード ファイルを右クリックし、をクリックして**コードの表示**です。  
  
     `$custommessage$` は、ウィザードのユーザー入力フォームに入力されたテキストで置き換えられています。  
  
## <a name="see-also"></a>参照  

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
[テンプレートのカスタマイズ](../ide/customizing-project-and-item-templates.md)  
[WizardExtension 要素 (Visual Studio テンプレート)](../extensibility/wizardextension-element-visual-studio-templates.md)  
[Visual Studio のテンプレートで NuGet パッケージ](/nuget/visual-studio-extensibility/visual-studio-templates)
