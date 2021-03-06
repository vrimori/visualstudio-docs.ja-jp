---
title: テキスト テンプレートからモデルへのアクセス
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, accessing models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 513ab6f1a953a2992b744aa3680cd453f677f5bb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966804"
---
# <a name="accessing-models-from-text-templates"></a>テキスト テンプレートからモデルへのアクセス
テキスト テンプレートを使用すると、レポート ファイル、ソース コード ファイル、およびその他のドメイン固有言語モデルを基にテキスト ファイルを作成できます。 テキスト テンプレートの基本については、次を参照してください。[コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)します。 テキスト テンプレートは、DSL をデバッグするときは、実験モードで動作し、DSL が配置されているコンピューターにも機能します。

> [!NOTE]
>  DSL ソリューション、サンプル テキスト テンプレートを作成するときに **\*.tt**デバッグ プロジェクトでファイルが生成されます。 ドメイン クラスの名前を変更すると、これらのテンプレートが機能しなくなります。 それにもかかわらずが、必要な基本的なディレクティブを含めるし、DSL を一致するように更新できる例を示します。

 テキスト テンプレートからモデルにアクセスします。

- Template ディレクティブの継承プロパティを設定<xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>します。 これは、ストアにアクセスを提供します。

- アクセスする DSL のディレクティブ プロセッサを指定します。 テキスト テンプレートのコードでは、ドメイン クラス、プロパティ、およびリレーションシップを使用できるように、DSL のアセンブリを読み込みます。 また、指定したモデル ファイルを読み込みます。

  A`.tt`最小言語の DSL テンプレートから新しい Visual Studio ソリューションを作成するときに、デバッグ プロジェクトに次の例のようなファイルが作成されます。

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

 このテンプレートについては、次の点に注意してください。

- テンプレートには、ドメイン クラス、プロパティ、および、DSL 定義で定義されているリレーションシップを使用できます。

- テンプレートで指定したモデル ファイルを読み込み、`requires`プロパティ。

- プロパティに`this`ルート要素が含まれています。 そこから、コードは、モデルの他の要素に移動できます。 プロパティの名前は、通常、DSL のルート ドメイン クラスと同じです。 この例では、 `this.ExampleModel`です。

- コード フラグメントを記述する言語が必要な場合は、c# を使用して、あらゆる種類のテキストを生成できます。 コードを記述できますまた[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]プロパティを追加することで`language="VB"`を`template`ディレクティブ。

- テンプレートをデバッグするには、追加`debug="true"`を`template`ディレクティブ。 テンプレートは、例外が発生した場合、Visual Studio の別のインスタンスで開かれます。 コードの特定の時点でデバッガーを中断する場合は、insert ステートメント `System.Diagnostics.Debugger.Break();`

   詳細については、次を参照してください。 [T4 テキスト テンプレートのデバッグ](../modeling/debugging-a-t4-text-template.md)します。

## <a name="about-the-dsl-directive-processor"></a>DSL のディレクティブ プロセッサについて
 テンプレートには、DSL 定義で定義されているドメイン クラスを使用できます。 これはの詳細については、通常は、テンプレートの先頭近くに表示される、ディレクティブになります。 前の例では、次は。

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 ディレクティブの名前 ( `MyLanguage`、この例では) は、DSL の名前から派生します。 呼び出す、*ディレクティブ プロセッサ*DSL の一部として生成されます。 ソース コードを検索する**Dsl\GeneratedCode\DirectiveProcessor.cs**します。

 DSL のディレクティブ プロセッサは、2 つの主要なタスクを実行します。

-   アセンブリおよびインポート ディレクティブは、DSL を参照するテンプレートに効果的に挿入します。 これにより、テンプレート コードで、ドメイン クラスを使用できます。

-   指定したファイルを読み込む、`requires`パラメーター セットのプロパティと`this`読み込み済みのモデルのルート要素を参照します。

## <a name="validating-the-model-before-running-the-template"></a>テンプレートを実行する前に、モデルの検証
 このテンプレートを実行する前に検証するモデルが発生することができます。

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 以下の点に注意してください。

1. `filename`と`validation`パラメーターで区切られます「;」必要があるその他の区切り記号またはスペースがあるとします。

2. どの検証メソッドが実行される検証カテゴリの一覧を決定します。 複数のカテゴリを区切る必要があります"&#124;"必要があるその他の区切り記号またはスペースがあるとします。

   エラーが見つかった場合は、[エラー] ウィンドウで報告し、結果ファイルは、エラー メッセージが格納されます。

## <a name="Multiple"></a> テキスト テンプレートから複数のモデルへのアクセス

> [!NOTE]
>  このメソッドは、同じテンプレートに複数のモデルを読み取ることができますが、ModelBus references をサポートしていません。 ModelBus 参照によって指定されたモデルを読み取り、次を参照してください。[テキスト テンプレートで Visual Studio ModelBus を使用して](../modeling/using-visual-studio-modelbus-in-a-text-template.md)します。

 同じテキスト テンプレートから複数のモデルにアクセスする場合は、各モデルの生成されたディレクティブ プロセッサに 1 回を呼び出す必要があります。 各モデルでのファイル名を指定する必要があります、`requires`パラメーター。 内のルート ドメイン クラスを使用する名前を指定する必要があります、`provides`パラメーター。 別の値を指定する必要があります、`provides`内の各ディレクティブの呼び出しのパラメーター。 たとえば、Library.xyz、School.xyz、および Work.xyz と呼ばれる 3 つのモデル ファイルがあることを想定しています。 同じテキスト テンプレートからそれらにアクセスするには、次のように 3 つのディレクティブの呼び出しを記述する必要があります。

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
>  このコード例では、最小言語ソリューション テンプレートに基づいている言語です。

 テキスト テンプレートでのモデルにアクセスするには、次の例では、コードのようなコードを記述できます。

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
 実行時に読み込む場合は、どのモデルを確認するには、モデル ファイルを DSL に固有のディレクティブを使用する代わりに、プログラム コードで動的に読み込むことができます。

 ただし、DSL に固有のディレクティブの関数の 1 つは、DSL の名前空間をインポートするテンプレート コードがその DSL で定義されているドメイン クラスを使用できるようにします。 追加する必要があります、ディレクティブを使用していないため、 **\<アセンブリ >** と**\<インポート >** ディレクティブをすべてのモデルを読み込むことがあります。 さまざまなモデルを読み込むことがありますが、同じ DSL のすべてのインスタンスである場合は簡単です。

 ファイルを読み込むには、最も効果的な方法は、Visual Studio ModelBus を使用してします。 一般的なシナリオで、テキスト テンプレートは、通常の方法で最初のモデルを読み込む、DSL に固有のディレクティブを使用します。 そのモデルには、別のモデルへの ModelBus 参照が含まれます。 ModelBus を使用して、参照されているモデルを開き、特定の要素にアクセスすることができます。 詳細については、次を参照してください。[テキスト テンプレートで Visual Studio ModelBus を使用して](../modeling/using-visual-studio-modelbus-in-a-text-template.md)します。

 あまり一般的なシナリオでは、ファイル名のみがあるモデル ファイルを開く可能性があり、これで、現在の Visual Studio プロジェクトではない可能性があります。 この場合で説明した手法を使用してファイルを開く[方法。プログラム コード内のファイルからモデルを開く](../modeling/how-to-open-a-model-from-file-in-program-code.md)します。

## <a name="generating-multiple-files-from-a-template"></a>テンプレートから複数のファイルを生成します。
 いくつかのファイル - を生成する場合など、モデルでは、各要素に対して個別のファイルを生成するがあるいくつかの可能なアプローチです。 既定では、1 つのファイルは、各テンプレート ファイルから生成されます。

### <a name="splitting-a-long-file"></a>長いファイルの分割
 このメソッドでは、テンプレートを使用する区切り記号で区切られた、1 つのファイルを生成します。 その部分にファイルを分割します。 2 つのテンプレートが 1 つのファイルと、分割を生成する 1 つがあります。

 **LoopTemplate.t4**長の 1 つのファイルが生成されます。 クリックすると直接に処理しないため、そのファイルの拡張子が「.t4 と展開されます」に注意してください**すべてのテンプレートの変換**します。 このテンプレートは、セグメントを区切る区切り記号文字列を指定するパラメーターを受け取ります。

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

 `LoopSplitter.tt` 呼び出す`LoopTemplate.t4`、結果として得られるファイルにはセグメントに分割します。 モデルは読み取られませんので、このテンプレートにモデル化のテンプレートがないことに注意してください。

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