---
title: 'チュートリアル: 生成済みディレクティブ プロセッサへのホストの接続'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 5b5346f47d3dcb836a0e8eeef7d9b21bd55ccd07
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896238"
---
# <a name="walkthrough-connect-a-host-to-a-generated-directive-processor"></a>チュートリアル: 生成済みディレクティブ プロセッサにホストを接続する

テキスト テンプレートを処理する、独自のホストを記述することができます。 基本的なカスタム ホストの説明については、[チュートリアル: カスタム テキスト テンプレート ホストの作成](../modeling/walkthrough-creating-a-custom-text-template-host.md)です。 複数の出力ファイルを生成するなどの関数を追加するには、そのホストを拡張できます。

このチュートリアルでは、テキスト テンプレート ディレクティブ プロセッサの呼び出しをサポートするように、そのカスタム ホストを展開します。 ドメイン固有言語を定義するときに生成、*ディレクティブ プロセッサ*ドメイン モデルです。 ディレクティブ プロセッサによって、ユーザー アセンブリを記述し、テンプレートのディレクティブをインポートする必要が少なくなり、モデルにアクセスするためのテンプレートを作成するために簡単にできます。

> [!NOTE]
> このチュートリアル[チュートリアル: カスタム テキスト テンプレート ホストの作成](../modeling/walkthrough-creating-a-custom-text-template-host.md)です。 このチュートリアルを最初に実行します。

このチュートリアルでは、次のタスクについて説明します。

- 使用して[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]ドメイン モデルに基づいているディレクティブ プロセッサを生成します。

- 生成されたディレクティブ プロセッサへのカスタム テキスト テンプレート ホストを接続します。

- 生成されたディレクティブ プロセッサを搭載したカスタム ホストをテストします。

## <a name="prerequisites"></a>必須コンポーネント

DSL を定義するには、以下のコンポーネントをインストールしておく必要があります。


| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580) |
| Visual Studio Visualization and Modeling SDK | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

さらで作成したカスタム テキスト テンプレート変換が必要[チュートリアル: カスタム テキスト テンプレート ホストの作成](../modeling/walkthrough-creating-a-custom-text-template-host.md)です。

## <a name="use-domain-specific-language-tools-to-generate-a-directive-processor"></a>ドメイン固有言語ツールを使用して、ディレクティブ プロセッサを生成するには

このチュートリアルでは、ドメイン固有言語デザイナー ウィザードを使用してソリューション DSLMinimalTest のドメイン固有言語を作成します。

1. 次の特性を持つドメイン固有言語ソリューションを作成します。

   -   名前: DSLMinimalTest

   -   ソリューション テンプレート: 最小言語

   -   ファイル拡張子: min

   -   会社名: Fabrikam

   ドメイン固有言語ソリューションを作成する方法の詳細については、次を参照してください。[方法: ドメイン固有言語ソリューションを作成](../modeling/how-to-create-a-domain-specific-language-solution.md)です。

2. **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

   > [!IMPORTANT]
   > この手順では、ディレクティブ プロセッサを生成し、レジストリでは、キーを追加します。

3. **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。

    Visual Studio の 2 番目のインスタンスを開きます。

4. 実験用のビルドで**ソリューション エクスプ ローラー**、ファイルをダブルクリックして**sample.min**します。

    ファイルがデザイナーで開きます。 モデルが 2 つの要素、ExampleElement1 と ExampleElement2、およびそれらの間のリンクを持つことに注意してください。

5. Visual Studio の 2 番目のインスタンスを閉じます。

6. ソリューションを保存し、ドメイン固有言語デザイナーを閉じます。

## <a name="connect-a-custom-text-template-host-to-a-directive-processor"></a>ディレクティブ プロセッサへのカスタム テキスト テンプレート ホストを接続します。

作成したカスタム テキスト テンプレート ホスト、ディレクティブ プロセッサを接続するディレクティブ プロセッサを生成した後[チュートリアル: カスタム テキスト テンプレート ホストの作成](../modeling/walkthrough-creating-a-custom-text-template-host.md)です。

1.  CustomHost ソリューションを開きます。

2.  **[プロジェクト]** メニューの **[参照の追加]** をクリックします。

     **参照の追加**ダイアログ ボックスが開き、 **.NET**タブが表示されます。

3.  次の参照を追加します。

    -   Microsoft.VisualStudio.Modeling.Sdk.11.0

    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    -   Microsoft.VisualStudio.TextTemplating.11.0

    -   Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    -   Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    -   Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4.  Module1.vb、Program.cs の上部にある次のコード行を追加します。

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5.  プロパティのコードを見つけます`StandardAssemblyReferences`、し、次のコードに置き換えます。

    > [!NOTE]
    > この手順では、生成されたディレクティブ プロセッサ ホストをサポートするに必要なアセンブリへの参照を追加します。

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

6.  関数のコードを見つけます`ResolveDirectiveProcessor`、し、次のコードに置き換えます。

    > [!IMPORTANT]
    > このコードには、接続する生成されたディレクティブ プロセッサの名前にハード コーディングされた参照が含まれています。 行うことができます簡単にこれより一般的なすべてのディレクティブ プロセッサを探す場合、レジストリに一覧表示し一致するものを見つけようとします。 その場合は、ホストは、生成されたディレクティブ プロセッサを行います。

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

7.  **ファイル** メニューのをクリックして**すべて保存**します。

8.  **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

## <a name="test-the-custom-host-with-the-directive-processor"></a>カスタム ディレクティブ プロセッサを搭載したホストをテストします。

最初、カスタム テキスト テンプレート ホストをテストするには、生成されたディレクティブ プロセッサを呼び出すテキスト テンプレートを記述する必要があります。 テキスト テンプレートの名前を渡す、および、ディレクティブが正しく処理されたことを確認します。 カスタム ホストを実行します。

### <a name="create-a-text-template-to-test-the-custom-host"></a>カスタム ホストをテストするテキスト テンプレートを作成します。

1.  テキスト ファイルを作成し、名前`TestTemplateWithDP.tt`します。 メモ帳などの任意のテキスト エディターを使用して、ファイルを作成することができます。

2.  次の内容をテキスト ファイルに追加します。

    > [!NOTE]
    > テキスト テンプレートのプログラミング言語は、カスタム ホストと一致する必要はありません。

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

3.  コードでは、次のように置換します。 \<YOUR パス > 最初の手順で作成した設計に固有の言語から Sample.min ファイルのパスを使用します。

4.  ファイルを保存して閉じます。

### <a name="test-the-custom-host"></a>カスタム ホストをテストします。

1.  コマンド プロンプト ウィンドウを開きます。

2.  カスタム ホストの実行可能ファイルのパスを入力します。ただし、Enter キーはまだ押さないでください。

     たとえば、次のように入力します。

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > アドレスを入力する代わりに CustomHost.exe ファイルを参照できますで**Windows エクスプ ローラー**、コマンド プロンプト ウィンドウにファイルをドラッグします。

3.  空白を入力します。

4.  テキスト テンプレート ファイルのパスを入力し、Enter キーを押します。

     たとえば、次のように入力します。

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > アドレスを入力する代わりに TestTemplateWithDP.txt ファイルを参照できますで**Windows エクスプ ローラー**、コマンド プロンプト ウィンドウにファイルをドラッグします。

     カスタム ホスト アプリケーションが実行され、テキスト テンプレート変換プロセスを開始します。

5.  **Windows エクスプ ローラー**、TestTemplateWithDP.txt ファイルが含まれているフォルダーを参照します。

     フォルダーには、TestTemplateWithDP1.txt ファイルも含まれています。

6.  このファイルを開き、テキスト テンプレート変換の結果を確認します。

     生成されたテキスト出力の結果が表示され、ようになります。

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>関連項目

- [チュートリアル: カスタム テキスト テンプレート ホストの作成](../modeling/walkthrough-creating-a-custom-text-template-host.md)
