---
title: "チュートリアル: 生成されたディレクティブ プロセッサをホストに接続する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 264953ec2044aae7069af72d74a5abbfdcacce51
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>チュートリアル: 生成済みディレクティブ プロセッサへのホストの接続
テキスト テンプレートを処理する、独自のホストを記述することができます。 基本的なカスタム ホストはではデモンストレーション[チュートリアル: カスタム テキスト テンプレート ホストの作成](../modeling/walkthrough-creating-a-custom-text-template-host.md)です。 複数の出力ファイルを生成するなどの機能を追加するには、そのホストを拡張できます。  
  
 このチュートリアルでは、ディレクティブ プロセッサを呼び出すテキスト テンプレートをサポートするように、そのカスタム ホストを展開します。 ドメイン固有言語を定義するときに生成、*ディレクティブ プロセッサ*ドメイン モデル。 ディレクティブ プロセッサでは、ユーザー アセンブリを記述して、テンプレート内のディレクティブをインポートする必要性が低く、モデルにアクセスするテンプレートを記述するやすくなります。  
  
> [!WARNING]
>  このチュートリアル[チュートリアル: カスタム テキスト テンプレート ホストの作成](../modeling/walkthrough-creating-a-custom-text-template-host.md)です。 このチュートリアルを最初に実行します。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   使用して[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]ドメイン モデルに基づいているディレクティブ プロセッサを生成します。  
  
-   生成されたディレクティブ プロセッサをカスタム テキスト テンプレート ホストに接続します。  
  
-   カスタム生成されたディレクティブ プロセッサを搭載したホストをテストします。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 DSL を定義するには、以下のコンポーネントをインストールしておく必要があります。  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Visual Studio Visualization and Modeling SDK||  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
 さらで作成したカスタム テキスト テンプレート変換する必要があります[チュートリアル: カスタム テキスト テンプレート ホストの作成](../modeling/walkthrough-creating-a-custom-text-template-host.md)です。  
  
## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>ドメイン固有言語ツールを使用して、ディレクティブ プロセッサを生成するには  
 このチュートリアルでは、ドメイン固有言語ソリューション DSLMinimalTest を作成するのにドメイン固有言語のデザイナー ウィザードを使用します。  
  
#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>ドメイン モデルに基づいているディレクティブ プロセッサを生成するドメイン固有言語ツールを使用するには  
  
1.  次の特徴が含まれるドメイン固有言語ソリューションを作成します。  
  
    -   名前: DSLMinimalTest  
  
    -   ソリューション テンプレート: 最小言語  
  
    -   ファイル拡張子: 最小値  
  
    -   会社名: Fabrikam  
  
     ドメイン固有言語ソリューションを作成の詳細については、次を参照してください。[する方法: ドメイン固有言語ソリューションを作成する](../modeling/how-to-create-a-domain-specific-language-solution.md)です。  
  
2.  **[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。  
  
    > [!IMPORTANT]
    >  この手順では、ディレクティブ プロセッサを生成し、そのキーをレジストリに追加します。  
  
3.  **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。  
  
     2 番目のインスタンスの[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]が開きます。  
  
4.  実験用のビルドで**ソリューション エクスプ ローラー**、ファイルをダブルクリックして**sample.min**です。  
  
     このファイルは、デザイナーで開きます。 モデルに 2 つの要素、ExampleElement1 と ExampleElement2、およびそれらの間のリンクに注意してください。  
  
5.  2 つ目のインスタンスを閉じる[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
6.  ソリューションを保存し、ドメイン固有言語デザイナーを閉じます。  
  
## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>ディレクティブ プロセッサをカスタム テキスト テンプレート ホストに接続します。  
 ディレクティブ プロセッサとで作成したカスタム テキスト テンプレート ホストに接続するディレクティブ プロセッサを生成した後[チュートリアル: カスタム テキスト テンプレート ホストの作成](../modeling/walkthrough-creating-a-custom-text-template-host.md)です。  
  
#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>生成されたディレクティブ プロセッサへのカスタム テキスト テンプレート ホストに接続するには  
  
1.  CustomHost ソリューションを開きます。  
  
2.  **[プロジェクト]** メニューの **[参照の追加]** をクリックします。  
  
     **参照の追加** ダイアログ ボックスが開き、 **.NET**  タブが表示されます。  
  
3.  次の参照を追加します。  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Interfaces.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.VSHost.11.0  
  
4.  Program.cs または Module1.vb の上部には、次のコード行を追加します。  
  
    ```csharp  
    using Microsoft.Win32;  
    ```  
  
    ```vb  
    Imports Microsoft.Win32  
    ```  
  
5.  プロパティのコードを見つけます`StandardAssemblyReferences`、次のコードに置き換えます。  
  
    > [!NOTE]
    >  この手順では、生成されたディレクティブ プロセッサをサポートするホストに必要なアセンブリへの参照を追加します。  
  
    ```csharp  
    //the host can provide standard assembly references  
    //the engine will use these references when compiling and  
    //executing the generated transformation class  
    //--------------------------------------------------------------  
    public IList<string> StandardAssemblyReferences  
    {  
        get  
        {  
            return new string[]  
            {  
                //if this host searches standard paths and the GAC  
                //we can specify the assembly name like this:  
                //"System"  
                //since this host only resolves assemblies from the   
                //fully qualified path and name of the assembly  
                //this is a quick way to get the code to give us the  
                //fully qualified path and name of the System assembly  
                //---------------------------------------------------------  
                typeof(System.Uri).Assembly.Location,  
                            typeof(System.Uri).Assembly.Location,  
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,  
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,  
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,  
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location  
  
            };  
        }  
    }  
    ```  
  
6.  関数のコードを見つける`ResolveDirectiveProcessor`、次のコードに置き換えます。  
  
    > [!IMPORTANT]
    >  このコードには、接続する、生成されたディレクティブ プロセッサの名前へのハードコード参照が含まれています。 簡単に行ったこれより一般的なレジストリに登録し一致するものを検索しようとしています。 すべてのディレクティブ プロセッサを探す場合。 その場合は、ホストは、生成されたディレクティブ プロセッサを搭載した機能です。  
  
    ```csharp  
    //the engine calls this method based on the directives the user has   
            //specified it in the text template  
            //this method can be called 0, 1, or more times  
            //---------------------------------------------------------------------  
            public Type ResolveDirectiveProcessor(string processorName)  
            {  
                //check the processor name, and if it is the name of the processor the   
                //host wants to support, return the type of the processor  
                //---------------------------------------------------------------------  
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)  
                {  
                    try  
                    {  
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";  
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))  
                        {  
                            if (specificKey != null)  
                            {  
                                List<string> names = new List<String>(specificKey.GetValueNames());  
                                string classValue = specificKey.GetValue("Class") as string;  
                                if (!string.IsNullOrEmpty(classValue))  
                                {  
                                    string loadValue = string.Empty;  
                                    System.Reflection.Assembly processorAssembly = null;  
                                    if (names.Contains("Assembly"))  
                                    {  
                                        loadValue = specificKey.GetValue("Assembly") as string;  
                                        if (!string.IsNullOrEmpty(loadValue))  
                                        {  
                                            //the assembly must be installed in the GAC  
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);  
                                        }  
                                    }  
                                    else if (names.Contains("CodeBase"))  
                                    {  
                                        loadValue = specificKey.GetValue("CodeBase") as string;  
                                        if (!string.IsNullOrEmpty(loadValue))  
                                        {  
                                            //loading local assembly  
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);  
                                        }  
                                    }  
                                    if (processorAssembly == null)  
                                    {  
                                        throw new Exception("Directive Processor not found");  
                                    }  
                                    Type processorType = processorAssembly.GetType(classValue);  
                                    if (processorType == null)  
                                    {  
                                        throw new Exception("Directive Processor not found");  
                                    }  
                                    return processorType;  
                                }  
                            }  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        //if the directive processor can not be found, throw an error  
                        throw new Exception("Directive Processor not found");  
                    }  
                }  
  
                //if the directive processor is not one this host wants to support  
                throw new Exception("Directive Processor not supported");  
            }  
    ```  
  
7.  **ファイル** メニューのをクリックして**すべて保存**です。  
  
8.  **[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。  
  
## <a name="testing-the-custom-host-with-the-directive-processor"></a>カスタム ディレクティブ プロセッサを搭載したホストのテスト  
 最初にカスタム テキスト テンプレート ホストをテストするを生成されたディレクティブ プロセッサを呼び出すテキスト テンプレートを記述する必要があります。 カスタム ホストを実行する、テキスト テンプレートの名前を渡すし、ディレクティブが正しく処理されることを確認します。  
  
#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>テキスト テンプレートを作成してカスタム ホストをテストするには  
  
1.  テキスト ファイルを作成し、名前を付けます`TestTemplateWithDP.tt`です。 メモ帳などの任意のテキスト エディターを使用して、ファイルを作成することができます。  
  
2.  次の内容をテキスト ファイルに追加します。  
  
    > [!NOTE]
    >  テキスト テンプレートのプログラミング言語は、カスタム ホストのと一致する必要はありません。  
  
    ```csharp  
    Text Template Host Test  
  
    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
    <# //this is the call to the examplemodel directive in the generated directive processor #>  
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>  
    <# //uncomment this line to test that the host allows the engine to set the extension #>  
    <# //@ output extension=".htm" #>  
  
    <# //uncomment this line if you want to see the generated transformation class #>  
    <# //System.Diagnostics.Debugger.Break(); #>  
    <# //this code uses the results of the examplemodel directive #>  
    <#  
        foreach ( ExampleElement box in this.ExampleModel.Elements )   
        {   
            WriteLine("Box: {0}", box.Name);  
  
            foreach (ExampleElement linkedTo in box.Targets)  
            {  
                WriteLine("Linked to: {0}", linkedTo.Name);  
            }  
  
            foreach (ExampleElement linkedFrom in box.Sources)  
            {  
                WriteLine("Linked from: {0}", linkedFrom.Name);  
            }  
  
            WriteLine("");  
        }   
    #>  
    ```  
  
    ```vb  
    Text Template Host Test  
  
    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
  
    <# 'this is the call to the examplemodel directive in the generated directive processor #>  
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>  
  
    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>  
    <# '@ output extension=".htm" #>  
  
    <# 'Uncomment this line if you want to see the generated transformation class. #>  
    <# 'System.Diagnostics.Debugger.Break() #>  
  
    <# 'this code uses the results of the examplemodel directive #>  
  
    <#      
       For Each box as ExampleElement In Me.ExampleModel.Elements   
  
           WriteLine("Box: {0}", box.Name)  
  
            For Each LinkedTo as ExampleElement In box.Targets  
                WriteLine("Linked to: {0}", LinkedTo.Name)  
            Next  
  
            For Each LinkedFrom as ExampleElement In box.Sources  
                WriteLine("Linked from: {0}", LinkedFrom.Name)  
            Next  
  
            WriteLine("")  
  
       Next   
    #>  
    ```  
  
3.  コードでは、次のように置換します。\<のパス > 最初の手順で作成した設計に固有の言語から、Sample.min ファイルのパスを使用します。  
  
4.  ファイルを保存して閉じます。  
  
#### <a name="to-test-the-custom-host"></a>カスタム ホストをテストするには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  カスタム ホストの実行可能ファイルのパスを入力します。ただし、Enter キーはまだ押さないでください。  
  
     たとえば、次のように入力します。  
  
     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`  
  
    > [!NOTE]
    >  アドレスを入力するには、代わりに CustomHost.exe ファイルを参照することができますに**Windows エクスプ ローラー**、コマンド プロンプト ウィンドウにファイルをドラッグします。  
  
3.  空白を入力します。  
  
4.  テキスト テンプレート ファイルのパスを入力し、Enter キーを押します。  
  
     たとえば、次のように入力します。  
  
     `<YOUR PATH>TestTemplateWithDP.txt`  
  
    > [!NOTE]
    >  アドレスを入力するには、代わりに TestTemplateWithDP.txt ファイルを参照することができますに**Windows エクスプ ローラー**、コマンド プロンプト ウィンドウにファイルをドラッグします。  
  
     カスタム ホスト アプリケーションを実行し、テキスト テンプレート変換プロセスを開始します。  
  
5.  **Windows エクスプ ローラー**、TestTemplateWithDP.txt ファイルが含まれているフォルダーを参照します。  
  
     フォルダーには、TestTemplateWithDP1.txt ファイルも含まれています。  
  
6.  このファイルを開き、テキスト テンプレート変換の結果を確認します。  
  
     生成されたテキスト出力の結果が表示され、次のようになります。  
  
    ```  
    Text Template Host Test  
  
    Box: ExampleElement1  
    Linked to: ExampleElement2  
  
    Box: ExampleElement2  
    Linked from: ExampleElement1  
    ```  
  
## <a name="see-also"></a>参照  
 [チュートリアル: カスタム テキスト テンプレート ホストの作成](../modeling/walkthrough-creating-a-custom-text-template-host.md)
