---
title: '方法: プロジェクト テンプレートにウィザードを使用して |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 17632f18985820730cd5036d2d53f7364afde5f7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547322"
---
# <a name="how-to-use-wizards-with-project-templates"></a>方法 : プロジェクト テンプレートを組み合わせたウィザードを使用する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio には、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスが用意されています。このインターフェイスを実装すると、ユーザーがテンプレートからプロジェクトを作成する際にカスタム コードを実行できるようになります。  
  
 プロジェクトのテンプレートをカスタマイズする、テンプレートに追加のファイルを追加するユーザー入力または許可された他のアクションを収集するカスタム UI を表示するのには、プロジェクト テンプレートのカスタマイズを使用できます。  
  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>ユーザーがクリックすると同時に開始、プロジェクトの作成中に、さまざまな時点でインターフェイス メソッドが呼び出されます**OK**上、**新しいプロジェクト** ダイアログ ボックス。 インターフェイスの各メソッドには、そのメソッドが呼び出される時点を表す名前が付けられます。 たとえば、Visual Studio が呼び出す<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>プロジェクトを作成するときに開始、すぐにことがユーザー入力を収集するカスタム コードを記述する適切な位置。  
  
## <a name="creating-a-project-template-project-with-a-vsix-project"></a>VSIX プロジェクトのプロジェクト テンプレート プロジェクトを作成します。  
 プロジェクト テンプレート プロジェクトを Visual Studio SDK の一部であるカスタム テンプレートの作成を開始するとします。 この手順では、c# プロジェクト テンプレート プロジェクトを使用しましたも Visual Basic プロジェクト テンプレート プロジェクトがあります。 プロジェクト テンプレート プロジェクトを含むソリューションに、VSIX プロジェクトを追加します。  
  
1.  C# プロジェクト テンプレート プロジェクトを作成 (Visual Studio で、**ファイル/新しい/プロジェクト/Visual c#/機能拡張/c# プロジェクト テンプレート**)。 名前を付けます**MyProjectTemplate**します。  
  
    > [!NOTE]
    >  Visual Studio SDK をインストールするためのよく寄せられる可能性があります。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
2.  新しい VSIX プロジェクトの追加 (**ファイル/新しい/プロジェクト/Visual c#/機能拡張/VSIX プロジェクト**) プロジェクト テンプレートと同じソリューションで (で、**ソリューション エクスプ ローラー**、ソリューション ノードを選択右クリックし、**追加/新規プロジェクト**)。 名前を付けます**MyProjectWizard します。**  
  
3.  VSIX プロジェクトをスタートアップ プロジェクトとして設定します。 **ソリューション エクスプ ローラー**、選択、ソリューション ノードを右クリックし、**スタートアップ プロジェクトとして設定**します。  
  
4.  VSIX プロジェクトの資産としてテンプレート プロジェクトを追加します。 **ソリューション エクスプ ローラー**、VSIX プロジェクトのノードの下にあります、 **source.extension.vsixmanifest**ファイル。 マニフェスト エディターで開きをダブルクリックします。  
  
5.  マニフェスト エディターで、**資産**ウィンドウの左側にあるタブ。  
  
6.  **資産**] タブで [**新規**します。 **新しい資産の追加**ウィンドウの種類 フィールドに対して**Microsoft.VisualStudio.ProjectTemplate**します。 **ソース**フィールドで、**現在のソリューションでプロジェクトを**します。 **プロジェクト**フィールドで、 **MyProjectTemplate**します。 次に、 **[OK]** をクリックします。  
  
7.  ソリューションをビルドし、デバッグを開始します。 Visual Studio の 2 番目のインスタンスが表示されます。 (いくつか分をかかります。)  
  
8.  Visual Studio の 2 番目のインスタンスでは、新しいテンプレートを使用して新しいプロジェクトを作成してみてください。 (**ファイル/new/プロジェクト/Visual c#/MyProject テンプレート**)。 新しいプロジェクトがという名前のクラスを表示する必要があります**Class1**します。 カスタム プロジェクト テンプレートが作成されました! デバッグを停止します。  
  
## <a name="creating-a-custom-template-wizard"></a>カスタム テンプレート ウィザードの作成  
 このトピックでは、プロジェクトを作成する前に Windows フォームを開くカスタム ウィザードを作成する方法を紹介します。 フォームでは、プロジェクトの作成中にソース コードに追加されているカスタム パラメーター値を追加することができます。  
  
1.  アセンブリを作成することができる VSIX プロジェクトを設定します。  
  
2.  **ソリューション エクスプ ローラー**、VSIX プロジェクト ノードを選択します。 ソリューション エクスプ ローラーで、以下が表示、**プロパティ**ウィンドウ。 そうでない場合は、選択**ビュー/プロパティ ウィンドウ**、またはキーを押します**F4**します。 [プロパティ] ウィンドウで、次のフィールドを選択します`true`:。  
  
    -   **IncludeAssemblyInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInLocalVSIXDeployment**  
  
3.  VSIX プロジェクトにアセットとしてのアセンブリを追加します。 Source.extension.vsixmanifest ファイルを開き、選択、**資産**タブ。**新しい資産の追加** ウィンドウの**型**選択**microsoft.visualstudio.assembly**の**ソース**選択**A現在のソリューションでプロジェクト**、および**プロジェクト**選択**MyTemplateWizard**します。  
  
4.  VSIX プロジェクトに次の参照を追加します。 (で、**ソリューション エクスプ ローラー**、[VSIX プロジェクト ノードを選択**参照**、右クリックし、**参照の追加**)。**参照の追加**ダイアログで、 **Framework** ] タブで、検索、 **System.Windows フォーム**アセンブリを選択します。 ここで選択、**拡張機能** タブの検索、 **EnvDTE**アセンブリを選択します。 また、 **Microsoft.VisualStudio.TemplateWizardInterface**アセンブリを選択します。 **[OK]** をクリックします。  
  
5.  VSIX プロジェクトに、ウィザード実装するためのクラスを追加します。 (ソリューション エクスプ ローラーでは、VSIX プロジェクト ノードを右クリックして**追加**、し**新しい項目の**、し**クラス**)。クラスの名前**WizardImplementation**します。  
  
6.  コードに置き換えます、 **WizardImplementationClass.cs**を次のコード ファイル。  
  
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
  
     **されている UserInputForm**これで参照されているコードは後で実装されます。  
  
     `WizardImplementation` クラスには、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> のすべてのメンバーに対するメソッドの実装が含まれています。 この例では、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> メソッドだけがタスクを実行します。 他のすべてのメソッドは、何もしないか、`true` を返します。  
  
     <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> メソッドは、次の 4 つのパラメーターを受け取ります。  
  
    -   <xref:System.Object> パラメーター。プロジェクトをカスタマイズできるように、ルートの <xref:EnvDTE._DTE> オブジェクトにキャストできます。  
  
    -   <xref:System.Collections.Generic.Dictionary%602> パラメーター。テンプレートで定義済みのすべてのパラメーターのコレクションが含まれます。 テンプレート パラメーターの詳細については、次を参照してください。[テンプレート パラメーター](../ide/template-parameters.md)します。  
  
    -   <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> パラメーター。使用されているテンプレートの種類に関する情報が含まれます。  
  
    -   <xref:System.Object>パラメーターのセットを含む配列が Visual Studio によってウィザードに渡されます。  
  
     この例では、ユーザー入力フォームから <xref:System.Collections.Generic.Dictionary%602> パラメーターにパラメーター値を追加します。 プロジェクト内の `$custommessage$` パラメーターのすべてのインスタンスは、ユーザーが入力したテキストと置き換えられます。 以下のアセンブリをプロジェクトに追加する必要があります。  
  
7.  ここで作成、**されている UserInputForm**します。 **WizardImplementation.cs**ファイルを終了した後、次のコードを追加、 **WizardImplementation**クラス。  
  
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
            }  
        }  
    ```  
  
     ユーザー入力フォームには、カスタム パラメーターを入力するための簡単なフォームが用意されています。 このフォームには、`textBox1` という名前のテキスト ボックスおよび `button1` という名前のボタンがあります。 このボタンをクリックすると、テキスト ボックスのテキストが `customMessage` パラメーターに格納されます。  
  
## <a name="connect-the-wizard-to-the-custom-template"></a>カスタム テンプレートにウィザードを接続します。  
 カスタム プロジェクト テンプレート、カスタム ウィザードを使用するためには、ウィザード アセンブリに署名し、新しいプロジェクトが作成されるときに、ウィザード実装を検索する場所を知ることができるようにする、カスタム プロジェクト テンプレートにいくつかの行を追加する必要があります。  
  
1.  アセンブリに署名します。 **ソリューション エクスプ ローラー**、選択、VSIX プロジェクトを右クリックし、**プロジェクトのプロパティ**します。  
  
2.  **プロジェクトのプロパティ**ウィンドウで、**署名** タブで、**署名** タブで、チェック**アセンブリに署名**します。 **厳密な名前キー ファイルを選択して**フィールドで、 **\<新規 >** します。 **厳密な名前キーの作成**ウィンドウで、**キー ファイル名**フィールドに「 **key.snk**します。 オフにして、**キーファイルをパスワードで保護する**フィールド。  
  
3.  **ソリューション エクスプ ローラー**、VSIX プロジェクトを選択し、検索、**プロパティ**ウィンドウ。  
  
4.  設定、**ビルド出力を出力ディレクトリのコピー**フィールドを**true**します。 これにより、ソリューションが再構築されるときの出力ディレクトリにコピーするアセンブリ。 これは、.vsix ファイルも含まれています。 その署名キーを確認するには、アセンブリを表示する必要があります。  
  
5.  ソリューションをリビルドします。  
  
6.  MyProjectWizard プロジェクト ディレクトリに key.snk ファイルを検索できます (**\<ディスクの場所 > \MyProjectTemplate\MyProjectWizard\key.snk**)。 Key.snk ファイルをコピーします。  
  
7.  出力ディレクトリに移動し、アセンブリを検索 (**\<ディスクの場所 > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll**)。 ここで、key.snk ファイルを貼り付けます。 (これは、どうしても必要はありませんは簡単に、次の手順)。  
  
8.  コマンド ウィンドウを開き、アセンブリが作成されたディレクトリに変更します。  
  
9. 検索、 **sn.exe**署名ツール。 たとえば、Windows 10 64 ビットのオペレーティング システムで一般的なパス、次のようになります  
  
     **C:\Program Files (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools**  
  
     ツールが見つからない場合は実行してみてください **/R します。 sn.exe**コマンド ウィンドウにします。 パスをメモしてをおきます。  
  
10. Key.snk ファイルから公開キーを抽出します。 コマンド ウィンドウで次のように入力します。  
  
     **\<sn.exe の場所 > \sn.exe - p key.snk outfile.key します。**  
  
     ディレクトリ名にスペースがある場合は、引用符で sn.exe のパスを囲むようにご注意ください。  
  
11. 出力ファイルから公開キー トークンを取得します。  
  
     **\<sn.exe の場所 > \sn.exe - t outfile.key します。**  
  
     引用符をもう一度、忘れないでください。 このような出力に行が表示されます。  
  
     **公開キー トークンは、します。 <token>**  
  
     この値をメモしてをおきます。  
  
12. プロジェクト テンプレートの .vstemplate ファイルには、カスタム ウィザードへの参照を追加します。 ソリューション エクスプ ローラーで検索 MyProjectTemplate.vstemplate、という名前のファイルを開きます。 終了した後、 \<TemplateContent > セクションで、次のセクションを追加します。  
  
    ```xml  
    <WizardExtension>  
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>  
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
     場所**MyProjectWizard** 、アセンブリの名前を指定し、**トークン**は、前の手順でコピーしたトークンです。  
  
13. プロジェクト内のすべてのファイルを保存し、リビルドします。  
  
## <a name="adding-the-custom-parameter-to-the-template"></a>カスタム パラメーターをテンプレートに追加します。  
 この例では、テンプレートとして使用されるプロジェクトには、カスタム ウィザードのユーザー入力フォームで指定されたメッセージが表示されます。  
  
1.  ソリューション エクスプ ローラーに移動、 **MyProjectTemplate**プロジェクト開き**Class1.cs**します。  
  
2.  アプリケーションの `Main` メソッドに次のコード行を追加します。  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     `$custommessage$` パラメーターは、プロジェクトをテンプレートから作成する際にユーザー入力フォームに入力したテキストで置き換えられます。  
  
 ここでテンプレートにエクスポートされる前に、完全なコード ファイルを示します。  
  
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
  
2.  新しい MyProjectTemplate プロジェクトを作成します。 (**ファイル/new/プロジェクト/Visual c#/MyProjectTemplate**)  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、テンプレートを指定の名前を入力 をクリックして**OK**します。  
  
     ウィザードのユーザー入力フォームが開きます。  
  
4.  カスタム パラメーターの値を入力し、ボタンをクリックします。  
  
     ウィザードのユーザー入力フォームが終了し、プロジェクトがテンプレートから作成されます。  
  
5.  **ソリューション エクスプ ローラー**ソース コード ファイルを右クリックし、クリックして、**コードの表示**します。  
  
     `$custommessage$` は、ウィザードのユーザー入力フォームに入力されたテキストで置き換えられています。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
 [テンプレートのカスタマイズ](../ide/customizing-project-and-item-templates.md)   
 [WizardExtension 要素 (Visual Studio テンプレート)](../extensibility/wizardextension-element-visual-studio-templates.md)