---
title: "テキスト テンプレートからモデルにアクセスする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, accessing models
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3162350a9afbe7972c4e593049141f533517bdc3
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="accessing-models-from-text-templates"></a>テキスト テンプレートからモデルへのアクセス
テキスト テンプレートを使用すると、レポート ファイル、ソース コード ファイル、およびその他のドメイン固有言語モデルに基づいたテキスト ファイルを作成することができます。 テキスト テンプレートの基本については、次を参照してください。[コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)です。 テキスト テンプレートは、DSL をデバッグするときは、実験用のモードで動作し、DSL が配置されているコンピューターではでも機能します。  
  
> [!NOTE]
>  DSL ソリューション、サンプル テキスト テンプレートを作成するとき **\*.tt**デバッグ プロジェクトでファイルが生成されます。 ドメイン クラスの名前を変更すると、これらのテンプレートが動作しなくなります。 いずれにしても、必要な基本的なディレクティブを含めるし、DSL の一致するように更新できる例を示します。  
  
 テキスト テンプレートから、モデルにアクセスします。  
  
-   Template ディレクティブの継承プロパティを設定する<xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>です。 これは、ストアにアクセスを提供します。  
  
-   アクセスする dsl には、ディレクティブ プロセッサを指定します。 テキスト テンプレートのコードでそのドメイン クラス、プロパティ、およびリレーションシップを使用できるように、DSL のアセンブリを読み込みます。 また、指定したモデル ファイルを読み込みます。  
  
 A`.tt`新規に作成すると、デバッグ プロジェクトに次の例のようなファイルが作成[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]DSL 最小限言語テンプレートからのソリューションです。  
  
```  
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ output extension=".txt" #>  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
  
This text will be output directly.  
  
This is the name of the model: <#= this.ModelRoot.Name #>  
  
Here is a list of elements in the model:  
<#  
  // When you change the DSL Definition, some of the code below may not work.  
  foreach (ExampleElement element in this.ExampleModel.Elements)  
  {#>  
<#= element.Name #>  
<#      
  }  
#>  
  
```  
  
 このテンプレートには、次の点に注意してください。  
  
-   テンプレートには、ドメイン クラス、プロパティ、および DSL 定義で定義されているリレーションシップを使用できます。  
  
-   テンプレートで指定したモデル ファイルの読み込み、`requires`プロパティです。  
  
-   プロパティに`this`ルート要素が含まれています。 そこから、コードは、モデルの他の要素に移動できます。 プロパティの名前は、通常、DSL のルート ドメイン クラスと同じです。 この例では、 `this.ExampleModel`です。  
  
-   コード フラグメントを記述する言語が必要な場合は、c# を使用して、任意の種類のテキストを生成できます。 コードを記述することができますまた[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]プロパティを追加することによって`language="VB"`を`template`ディレクティブです。  
  
-   テンプレートをデバッグするには、追加`debug="true"`を`template`ディレクティブです。 別のインスタンスで、テンプレートが開きます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]場合は、例外が発生します。 特定の時点のコードにデバッガーを中断する場合は、ステートメントを挿入します`System.Diagnostics.Debugger.Break();`  
  
     詳細については、次を参照してください。 [T4 テキスト テンプレートのデバッグ](../modeling/debugging-a-t4-text-template.md)です。  
  
## <a name="about-the-dsl-directive-processor"></a>DSL ディレクティブ プロセッサについて  
 テンプレートには、DSL 定義で定義されているドメイン クラスを使用できます。 これについては、通常、テンプレートの先頭近くに表示されるディレクティブでになります。 前の例では、次です。  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 ディレクティブの名前 ( `MyLanguage`、この例では) は、DSL の名前から派生します。 呼び出す、*ディレクティブ プロセッサ*DSL の一部として作成されます。 場合は、そのソース コードを見つけることができます**Dsl\GeneratedCode\DirectiveProcessor.cs**です。  
  
 DSL ディレクティブ プロセッサでは、次の 2 つの主要なタスクを実行します。  
  
-   実質的に、DSL を参照するテンプレートにアセンブリおよびインポート ディレクティブを挿入します。 これにより、テンプレート コードで、ドメイン クラスを使用できます。  
  
-   指定したファイルが読み込まれます、`requires`パラメーター セットのプロパティと`this`読み込み済みのモデルのルート要素を参照します。  
  
## <a name="validating-the-model-before-running-the-template"></a>テンプレートを実行する前に、モデルの検証  
 検証に使用するテンプレートが実行される前にモデルが発生することができます。  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 以下の点に注意してください。  
  
1.  `filename`と`validation`パラメーターはセミコロン「;」-h-1 他の区切り記号またはスペースとします。  
  
2.  検証のカテゴリの一覧は、どの検証メソッドは実行を決定します。 複数のカテゴリを区切る必要があります"&#124;"があってはなりません他の区切り記号またはスペースとします。  
  
 エラーが見つかった場合は、エラー ウィンドウに報告され、エラー メッセージを結果ファイルが含まれます。  
  
##  <a name="Multiple"></a>テキスト テンプレートから複数のモデルにアクセスします。  
  
> [!NOTE]
>  このメソッドは、同じテンプレート内の複数のモデルを読み取ることができますが、ModelBus 参照をサポートしません。 ModelBus 参照によって指定されたモデルを参照してください[テキスト テンプレートで Visual Studio ModelBus を使用して](../modeling/using-visual-studio-modelbus-in-a-text-template.md)です。  
  
 同じテキスト テンプレートから複数のモデルにアクセスする場合は、各モデルの生成されたディレクティブ プロセッサに 1 回を呼び出す必要があります。 各モデルのファイル名を指定する必要があります、`requires`パラメーター。 ルート ドメインのクラスを使用する名前を指定する必要があります、`provides`パラメーター。 異なる値を指定する必要があります、`provides`内の各ディレクティブの呼び出しのパラメーターです。 たとえば、Library.xyz、School.xyz、および Work.xyz と呼ばれる 3 つのモデル ファイルがあることを想定しています。 同じテキスト テンプレートからそれらにアクセスするには、次のように 3 つのディレクティブの呼び出しを書き込む必要があります。  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  このコード例では、最小限の言語のソリューション テンプレートに基づいている言語です。  
  
 テキスト テンプレート内のモデルにアクセスするに次の例では、コードのようなコードを記述できます。  
  
```csharp  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## <a name="loading-models-dynamically"></a>モデルを動的に読み込む  
 どのモデルを読み込む実行時に確認するには、モデル ファイルを DSL 固有のディレクティブを使用する代わりに、プログラム コードで動的に読み込むことができます。  
  
 ただし、DSL 固有ディレクティブの関数の 1 つは、DSL の名前空間をインポートするテンプレート コードがその DSL で定義されているドメイン クラスを使用できるように。 追加する必要があります、ディレクティブを使用していないため**\<アセンブリ >**と**\<インポート >**ディレクティブをすべてのモデルを読み込むことがあります。 これは、さまざまなモデルを読み込むことがありますが同じ DSL のすべてのインスタンスである場合は簡単です。  
  
 使用して、ファイルを読み込むには、最も効果的な方法は、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus です。 一般的なシナリオで、テキスト テンプレートは、通常の方法で、最初のモデルを読み込む、DSL 固有ディレクティブを使用します。 そのモデルには、別のモデルに ModelBus 参照が含まれます。 ModelBus を使用して、参照先のモデルを開くし、特定の要素にアクセスすることができます。 詳細については、次を参照してください。[テキスト テンプレートで Visual Studio ModelBus を使用して](../modeling/using-visual-studio-modelbus-in-a-text-template.md)です。  
  
 シナリオでは、通常小さく、可能性がある、ファイル名のみがあるモデル ファイルを開く場合があります、現在のおよび[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト。 この例で説明した手法を使用して、ファイルを開くことができます[する方法: プログラム コード内のファイルからモデルを開く](../modeling/how-to-open-a-model-from-file-in-program-code.md)です。  
  
## <a name="generating-multiple-files-from-a-template"></a>テンプレートから複数のファイルを生成します。  
 いくつかのファイル - を生成する場合など、モデルでは、各要素に個別のファイルを生成するがあるいくつかの可能なアプローチです。 既定では、各テンプレート ファイルから 1 つのファイルが生成されます。  
  
### <a name="splitting-a-long-file"></a>長いファイルの分割  
 このメソッドでは、テンプレートを使用する、区切り記号で区切られた 1 つのファイルを生成します。 各部分にファイルを分割します。 1 つのファイルおよびを分割して、その他を生成する 1 つ、2 つのテンプレートがあります。  
  
 **LoopTemplate.t4**長いの 1 つのファイルが生成されます。 ファイルの拡張子が「.t4 と展開されます」に注意してください、処理は必要ないをクリックすると直接ため**すべてのテンプレートの変換**です。 このテンプレートは、セグメントを区切る区切り記号文字列を指定するパラメーターを受け取ります。  
  
```  
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ parameter name="delimiter" type="System.String" #>  
<#@ output extension=".txt" #>  
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>  
<#  
  // Create a file segment for each element:  
  foreach (ExampleElement element in this.ExampleModel.Elements)   
  {   
    // First item is the delimiter:  
#>  
<#= string.Format(delimiter, element.Id) #>  
  
   Element: <#= element.Name #>  
<#  
   // Here you generate more content derived from the element.  
  }  
#>  
  
```  
  
 `LoopSplitter.tt`呼び出す`LoopTemplate.t4`、し、そのセグメントに生成されたファイルを分割します。 このテンプレートができないにモデル化のテンプレートでは、モデルが読み取らないために注意してください。  
  
```  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>  
<#@ import namespace="System.Runtime.Remoting.Messaging" #>  
<#@ import namespace="System.IO" #>  
  
<#  
  // Get the local path:  
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");  
  string dir = Path.GetDirectoryName(itemTemplatePath);  
  
  // Get the template for generating each file:  
  string loopTemplate = File.ReadAllText(itemTemplatePath);  
  
  Engine engine = new Engine();  
  
  // Pass parameter to new template:  
  string delimiterGuid = Guid.NewGuid().ToString();  
  string delimiter = "::::" + delimiterGuid + ":::";  
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");   
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);  
  
  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);  
  
  foreach (string nameAndFile in separateFiles)   
  {   
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;  
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);  
     if (parts.Length < 2) continue;  
#>  
 Generate: [<#= dir #>] [<#= parts[0] #>]  
<#  
     // Generate a file from this item:  
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);    
  }  
#>  
  
```