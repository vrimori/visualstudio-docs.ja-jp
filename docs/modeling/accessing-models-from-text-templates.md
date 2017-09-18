---
title: "テキスト テンプレートからモデルへのアクセス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "テキスト テンプレート, アクセス (モデルに)"
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: 33
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 33
---
# テキスト テンプレートからモデルへのアクセス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テキスト テンプレートを使用するとレポート ファイルソース・コード ファイルをドメイン固有言語モデルに基づく他のテキスト ファイルを作成します。  テキスト テンプレートに関する基本情報については[コード生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md) を参照してください。  テキスト テンプレートが実験モードでのデバッグはDSLDSL を配置したコンピューターで実行される場合。  
  
> [!NOTE]
>  DSL のソリューションを作成するとサンプル テキスト テンプレートの **\*.tt** ファイルはデバッグのプロジェクトに生成されます。  ドメイン クラスの名前を変更するとこれらのテンプレートが機能しなくなります。  いずれにしてもそれらは必要としDSL に一致するように更新する例を示します。基本ディレクティブを示します。  
  
 テキスト テンプレートからモデルにアクセスするには :  
  
-   <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>テンプレート ディレクティブの継承のプロパティを設定します。  これはストアへのアクセスを提供します。  
  
-   アクセスするとDSL に対するディレクティブ プロセッサを指定します。  ここではテキスト テンプレートのコードでドメイン クラスプロパティとリレーションシップを使用できるように DSL のアセンブリを読み込みます。  また指定したモデル ファイルを読み込みます。  
  
 次の例のような `.tt` ファイルはプロジェクトのデバッグに DSL の最小言語テンプレートから [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の新しいソリューションを作成するときに作成されます。  
  
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
  
 このテンプレートについては次の点に注意してください :  
  
-   テンプレートはDSL 定義で定義したドメイン クラスプロパティおよびリレーションシップを使用できます。  
  
-   テンプレートは`requires` のプロパティで指定したモデル ファイルを読み込みます。  
  
-   `this` のプロパティはルート要素が含まれています。  そこからモデル内の他の要素に移動できます。  プロパティの名前は通常DSL のルート ドメインにクラスの名前と同じです。  この例では`this.ExampleModel` です。  
  
-   コードが記述される言語は C\# ですがあらゆる種類のテキストを作成できます。  `template` のディレクティブに `language="VB"` プロパティを追加することにより代わりに [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] のコードを記述できます。  
  
-   テンプレートをデバッグするには`template` のディレクティブに `debug="true"` を追加します。  テンプレートは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の別のインスタンスで例外が発生すると表示されます。  コードの特定の時点でデバッガーを中断するにはステートメントを挿入 `System.Diagnostics.Debugger.Break();`  
  
     詳細については、「[T4 テキスト テンプレートのデバッグ](../modeling/debugging-a-t4-text-template.md)」を参照してください。  
  
## DSL のディレクティブ プロセッサについて  
 テンプレートはDSL 定義で定義したドメイン クラスを使用できます。  これは通常テンプレートの先頭にあるディレクティブで始まります。  前の例では次のようになります。  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 ディレクティブ \(この例で `MyLanguage`\) の名前はDSL の名前から派生します。  これはDSL の一部として生成される  *ディレクティブ プロセッサを*  開始します。  **Dsl\\GeneratedCode\\DirectiveProcessor.cs** のソース・コードを検索できます。  
  
 DSL のディレクティブ プロセッサは2 種類の主要タスクを実行します :  
  
-   これはDSL を参照するテンプレートを効果的にアセンブリとインポート ディレクティブを挿入します。  これはテンプレート コードでドメイン クラスを使用できるようになります。  
  
-   これは`requires` のパラメーターで指定した読み込み読み込んだモデルのルート要素を指定 `this` のプロパティを設定してファイルを表します。  
  
## モデルをテンプレートを実行する前に検証します  
 テンプレートが実行される前にモデルを検証できます。  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 これに注意してください :  
  
1.  `filename` と `validation` のパラメーターは 「区切られています ; 」そのほかの符号または空白があります。  
  
2.  検証のカテゴリの一覧は検証メソッドが実行されるかを判定します。  複数のカテゴリは 「区切ってください。&#124; 」そのほかの符号または空白があります。  
  
 エラーが発生した場合エラー ウィンドウで報告され結果のファイルにエラー メッセージが含まれています。  
  
##  <a name="Multiple"></a> テキスト テンプレートから複数のモデルにアクセスする  
  
> [!NOTE]
>  このメソッドは複数のテンプレートでモデルを読み込むことができますがModelBus 参照はサポートされません。  ModelBus 参照によって連結されるモデルを読み込むには[テキスト テンプレートでの Visual Studio ModelBus の使用](../modeling/using-visual-studio-modelbus-in-a-text-template.md) を参照してください。  
  
 同じテキスト テンプレートから複数のモデルにアクセスする場合は生成されたディレクティブ プロセッサをモデルごとに 1 回呼び出す必要があります。  `requires` のパラメーターで各モデル ファイル名を指定する必要があります。  `provides` のパラメーターのルート ドメインのクラスで使用する名前を指定する必要があります。  ディレクティブの呼び出しにおいて `provides` のパラメーターには異なる値を指定する必要があります。  たとえばLibrary.xyz School.xyz と Work.xyz という 3 種類のモデル ファイルがあるとします。  同じテキスト テンプレートからアクセスするには次のいずれかに似た 3 本のディレクティブの呼び出しを記述する必要があります。  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  このコード例では最小限の言語のソリューション テンプレートに基づく言語用です。  
  
 テキスト テンプレート モデルにアクセスするには次の例のようなコードを記述できます。  
  
```c#  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb#  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## 読み込みが動的にモデル化します。  
 読み込みに使用して実行時に判別する場合はプログラム コードに DSL 固有のディレクティブを使用する代わりにモデル ファイルを動的に読み込むことができます。  
  
 ただしDSL 固有のディレクティブの関数の 1 つがテンプレート コードがDSL で定義されているドメイン クラスを使用できるように DSL の名前空間をインポートします。  ディレクティブを使用していないため読み込む可能性のあるすべてのモデルの **\<assembly\>** と **\<import\>** のディレクティブを追加する必要があります。  これは読み込む可能性があるさまざまなモデルが同じ DSL のすべてのインスタンスは簡単です。  
  
 ファイルを読み込むには最も効果的なメソッドは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus を使用します。  一般的なシナリオではテキスト テンプレートは通常の最初のモデルを読み込むにはDSL 固有のディレクティブを使用します。  モデルはモデルの ModelBus への参照を含む。  参照されたモデルが開き特定の要素にアクセスするにはModelBus を使用できます。  詳細については、「[テキスト テンプレートでの Visual Studio ModelBus の使用](../modeling/using-visual-studio-modelbus-in-a-text-template.md)」を参照してください。  
  
 は通常のシナリオではファイル名のみ[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の現在のプロジェクトでモデル ファイルを開くことがあります。  この場合[方法: プログラム コード内のファイルからモデルを開く](../modeling/how-to-open-a-model-from-file-in-program-code.md) で説明した手法を使用してファイルを開くことができます。  
  
## テンプレートから複数のファイルの生成  
 複数のファイルを生成する場合は。たとえばモデルの各要素に個別のファイルを生成するには複数のような方法があります。  既定では1 種類のファイルはテンプレート ファイルから生成されます。  
  
### 長いファイルの分割  
 このメソッドでは区切り記号で区切られた一つのファイルを生成するテンプレートを使用します。  ファイルを部分に分割します。  2 種類のテンプレートは1 ページを分割する単一のファイルを生成するなどです。  
  
 **LoopTemplate.t4** は単一ファイルを生成します。  \[入力\] ENT0ENT をクリックすると直接操作する必要はないためファイル拡張子が 「 .t4 」であることに注意してください。  このテンプレートはセグメントを区切り記号文字列を指定するパラメーターを受け取ります :  
  
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
  
 `LoopSplitter.tt` は `LoopTemplate.t4` を起動しセグメントに生成されたファイルを分割します。  モデルを読み込まないのでこのテンプレートはモデリングのテンプレートでなくてもかまいませんことに注意してください。  
  
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