---
title: "T4 テキスト テンプレートを使用したデザイン時コード生成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "テキスト テンプレート プロジェクト項目"
  - "テキスト テンプレート, データ ソース モデル"
  - "テキスト テンプレート, 生成 (アプリケーションのコードを)"
  - "テキスト テンプレート, はじめに"
  - "テキスト テンプレート, コード生成のガイドライン"
  - "TextTemplatingFileGenerator カスタム ツール"
  - "すべてのテンプレートの変換"
ms.assetid: 2774b83d-1adb-4c66-a607-746e019b80c0
caps.latest.revision: 38
caps.handback.revision: 38
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 テキスト テンプレートを使用したデザイン時コード生成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

デザイン時 T4 テキスト テンプレートを使用して、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトのプログラム コードや他のファイルを生成できます。  テンプレートを作成するときは、*モデル*のデータに応じて生成されるコードが変わるようにするのが一般的です。  モデルとは、アプリケーションの要件に関する重要な情報が含まれたファイルまたはデータベースのことです。  
  
 たとえば、ワークフローをテーブルまたは図として定義したモデルがあるとします。  このモデルから、ワークフローを実行するソフトウェアを生成できます。  ユーザーの要件が変わったときに、新しいワークフローについてユーザーと共に検討しやすくなります。  ワークフローからコードを再生成すると、コードを手動で更新するよりも信頼性が高まります。  
  
> [!NOTE]
>  *モデル*は、アプリケーションの特定の側面を記述したデータ ソースです。  モデルはどのような形式でもかまいません。あらゆる種類のファイルまたはデータベースを使用できます。  UML モデルやドメイン固有言語モデルなどの特定の形式である必要はありません。  標準的なモデルの形式は、テーブルまたは XML ファイルです。  
  
 コード生成は決して新しい概念ではありません。  **.resx** ソリューションにある [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ファイルでリソースを定義すると、一連のクラスおよびメソッドが自動的に生成されます。  リソースの編集は、クラスやメソッドを直接編集するよりも、リソース ファイルで行った方がはるかに簡単で確実です。  同様に、テキスト テンプレートを使用すると、独自に設計したソースからコードを生成することができます。  
  
 テキスト テンプレートには、生成するテキストと、テキストの可変部分を生成するプログラム コードの組み合わせが含まれます。  プログラム コードにより、生成されるテキストの一部を繰り返したり、条件に従って省略したりできるようになります。  生成されるテキスト自体を、アプリケーションの一部となるプログラム コードにすることもできます。  
  
## デザイン時 T4 テキスト テンプレートを作成する  
  
#### Visual Studio でデザイン時 T4 テンプレートを作成するには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトを作成するか、既存のプロジェクトを開きます。  
  
     たとえば、**\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
2.  テキスト テンプレート ファイルをプロジェクトに追加し、ファイル名の拡張子を .tt にします。  
  
     そのために、**ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、**\[追加\]**、**\[新しい項目\]** の順にクリックします。  **\[新しい項目の追加\]** ダイアログ ボックスで、中央のペインの **\[テキスト テンプレート\]** を選択します。  
  
     ファイルの **\[カスタム ツール\]** プロパティが **TextTemplatingFileGenerator** となっていることに注目してください。  
  
3.  ファイルを開きます。  既に次のディレクティブが指定されています。  
  
    ```  
    <#@ template hostspecific="false" language="C#" #>  
    <#@ output extension=".txt" #>  
    ```  
  
     [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] プロジェクトにテンプレートを追加した場合、言語属性は "`VB`" になります。  
  
4.  ファイルの最後にテキストを追加します。  次に例を示します。  
  
    ```  
    Hello, world!  
    ```  
  
5.  ファイルを保存します。  
  
     テンプレートを実行してよいか確認する **\[セキュリティ警告\]** メッセージ ボックスが表示されます。  **\[OK\]** をクリックします。  
  
6.  **ソリューション エクスプローラー**で、テンプレート ファイル ノードを展開すると、拡張子が .txt のファイルが見つかります。  このファイルには、テンプレートから生成されたテキストが格納されています。  
  
    > [!NOTE]
    >  Visual Basic プロジェクトの場合は、**\[すべてのファイルを表示\]** をクリックしないと、出力ファイルが表示されません。  
  
### コードの再生成  
 次のいずれかの場合に、テンプレートが実行され、従属ファイルが生成されます。  
  
-   テンプレートを編集した後、フォーカスを別の [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ウィンドウに切り替えたとき。  
  
-   テンプレートを保存したとき。  
  
-   **\[ビルド\]** メニューの **\[すべてのテンプレートの変換\]** をクリックしたとき。  この場合、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューション内のすべてのテンプレートが変換されます。  
  
-   **ソリューション エクスプローラー**で、ファイルのショートカット メニューの **\[カスタム ツールの実行\]** をクリックしたとき。  この方法は、複数のテンプレートを選択して変換する場合に使用します。  
  
 読み取り先のデータ ファイルが変更されたときにテンプレートが実行されるよう、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトを設定することもできます。  詳細については、「[コードを自動的に再生成する](#Regenerating)」を参照してください。  
  
## 可変テキストを生成する  
 テキスト テンプレートから生成されるファイルのコンテンツは、プログラム コードを使用して変化させることができます。  
  
#### プログラム コードを使用してテキストを生成するには  
  
1.  `.tt` ファイルの内容を次のように変更します。  
  
    ```c#  
    <#@ template hostspecific="false" language="C#" #>  
    <#@ output extension=".txt" #>  
    <#int top = 10;  
  
    for (int i = 0; i<=top; i++)   
    { #>  
       The square of <#= i #> is <#= i*i #>  
    <# } #>  
    ```  
  
    ```vb#  
    <#@ template hostspecific="false" language="VB" #>  
    <#@ output extension=".txt" #>  
    <#Dim top As Integer = 10  
  
    For i As Integer = 0 To top  
    #>  
        The square of <#= i #> is <#= i*i #>  
    <#  
    Next  
    #>  
  
    ```  
  
2.  .tt ファイルを保存し、生成された .txt ファイルを再度確認します。  0 から 10 の数値を 2 乗した値が一覧表示されます。  
  
 複数のステートメントは `<#...#>` で囲まれており、単一の式は `<#=...#>` で囲まれていることに注意してください。  詳細については、「[T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)」を参照してください。  
  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] で生成コードを記述する場合は、`template` ディレクティブに `language="VB"` を含める必要があります。  `"C#"` が既定値です。  
  
## デザイン時 T4 テキスト テンプレートをデバッグする  
 テキスト テンプレートをデバッグするには、以下を実行します。  
  
-   `debug="true"` ディレクティブに `template` を挿入します。  例:  
  
     `<#@ template debug="true" hostspecific="false" language="C#" #>`  
  
-   通常のコードと同じように、テンプレートにブレークポイントを設定します。  
  
-   ソリューション エクスプローラーで、テキスト テンプレート ファイルのショートカット メニューを開き **\[T4 テンプレートのデバッグ\]** をクリックします。  
  
 テンプレートが実行され、ブレークポイントで停止します。  通常の方法で、変数を調べコードのステップ実行ができます。  
  
> [!TIP]
>  `debug="true"` は、生成されたコードに行番号ディレクティブを多数挿入して、生成されたコードをテキスト テンプレートに正確に対応付けます。  これを省いた場合、ブレークポイントが間違った状態で実行を停止する可能性があります。  
>   
>  ただし、デバッグしていないときでも、template ディレクティブにこれを残しておくことができます。  こうしても実行速度がほんのわずか低下するだけです。  
  
## ソリューションのコードまたはリソースを生成する  
 生成するプログラム ファイルは、モデルに応じて変化させることができます。  モデルは入力です。たとえば、データベース、構成ファイル、UML モデル、DSL モデルなど、各種のソースがそれに該当します。  プログラム ファイルは、同じモデルから複数生成するのが一般的です。  そのためには、生成するプログラム ファイルごとにテンプレート ファイルを作成し、すべてのテンプレートで同じモデルを読み取るようにします。  
  
#### プログラム コードまたはリソースを生成するには  
  
1.  適切な種類のファイル \(.cs、.vb、.resx、.xml など\) を生成するように output ディレクティブを変更します。  
  
2.  必要なソリューション コードを生成するためのコードを挿入します。  たとえば、クラス内に整数型のフィールド宣言を 3 つ生成するには、次のようにします。  
  
    ```c#  
  
                      <#@ template debug="false" hostspecific="false" language="C#" #>  
    <#@ output extension=".cs" #>  
    <# var properties = new string [] {"P1", "P2", "P3"}; #>  
    // This is generated code:  
    class MyGeneratedClass {  
    <# // This code runs in the text template:  
      foreach (string propertyName in properties)   { #>  
      // Generated code:  
      private int <#= propertyName #> = 0;  
    <# } #>  
    }  
    ```  
  
    ```vb#  
    <#@ template debug="false" hostspecific="false" language="VB" #>  
    <#@ output extension=".cs" #>  
    <# Dim properties = {"P1", "P2", "P3"} #>  
    class MyGeneratedClass {  
    <#   
       For Each propertyName As String In properties  
    #>  
      private int <#= propertyName #> = 0;  
    <#  
       Next  
    #>  
    }  
  
    ```  
  
3.  ファイルを保存し、生成されたファイルを調べると、次のコードが含まれていることがわかります。  
  
    ```  
    class MyGeneratedClass {  
      private int P1 = 0;   
      private int P2 = 0;  
      private int P3 = 0;  
    }  
    ```  
  
### 生成コードと生成されたテキスト  
 プログラム コードを生成する際に最も重要なことは、テンプレート内で実行されるコード生成機構 \(コードを生成するためのコード\) と、結果として生成されるコード \(ソリューションの一部になるコード\) とを混同しないことです。  2 つの言語が必ずしも一致している必要はありません。  
  
 前の例は、2 つのバージョンで構成されています。  1 つ目のバージョンは C\# のコードで生成されます。  2 つ目のバージョンは、Visual Basic のコードで生成されます。  ただし、両方のコードで生成されるテキストは同じであり、C\# クラスです。  
  
 同様に、[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] テンプレートは、どのような言語のコードでも生成できます。  生成されるテキストは、プログラム コードが含まれる固有の言語である必要はありません。  
  
### テキスト テンプレートの構成  
 ここでは、テンプレート コードを次の 2 つの部分に分けています。  
  
-   構成またはデータ収集の部分。この部分では変数に値を設定しますが、テキスト ブロックは含まれません。  前の例では、`properties` の初期化の部分が該当します。  
  
     この部分はインストア モデルを構築し、通常はモデル ファイルを読み取るため、"モデル" セクションとも呼ばれます。  
  
-   テキスト生成部分 \(この例では、`foreach(...){...}`\)。この部分では変数の値を使用します。  
  
 必ずしもこのように分ける必要はありませんが、このように記述すると、テキストを含む部分の複雑さが軽減され、テンプレートが読みやすくなります。  
  
## ファイルなど各種ソースを読み取る  
 モデル ファイルまたはモデル データベースにアクセスするために、テンプレート コードで System.XML などのアセンブリを使用できます。  これらのアセンブリにアクセスするためには、次のようなディレクティブを挿入する必要があります。  
  
```  
<#@ assembly name="System.Xml.dll" #>  
<#@ import namespace="System.Xml" #>  
<#@ import namespace="System.IO" #>  
```  
  
 `assembly` ディレクティブでアセンブリを指定することによって、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトの \[参照設定\] セクションに表示されるアセンブリと同じように、指定されたアセンブリにテンプレート コードからアクセスすることができます。  System.dll への参照を含める必要はありません。System.dll は自動的に参照されます。  `import` ディレクティブの効果は、完全修飾名を使用せずに型を指定できるようになることです。通常のプログラム ファイルで `using` ディレクティブを使用した場合と同様です。  
  
 たとえば、**System.IO** のインポート後に、次のようなコードを記述できます。  
  
```c#  
  
          <# var properties = File.ReadLines("C:\\propertyList.txt");#>  
...  
<# foreach (string propertyName in properties) { #>  
...  
```  
  
```vb#  
<# For Each propertyName As String In   
             File.ReadLines("C:\\propertyList.txt")  
#>  
  
```  
  
### 相対パス名を指定してファイルを開く  
 テキスト テンプレートを基準とする場所からファイルを読み込むには、`this.Host.ResolvePath()` を使用します。  this.Host を使用するには、次のように `hostspecific="true"` で `template` を設定する必要があります。  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
  
```  
  
 これで、次のようなコードを記述できるようになります。  
  
```c#  
<# string fileName = this.Host.ResolvePath("filename.txt");  
  string [] properties = File.ReadLines(filename);  
#>  
...  
<#  foreach (string propertyName in properties { #>  
...  
  
```  
  
```vb#  
<# Dim fileName = Me.Host.ResolvePath("propertyList.txt")  
   Dim properties = File.ReadLines(filename)  
#>  
...  
<#   For Each propertyName As String In properties  
...  
#>  
  
```  
  
 `this.Host.TemplateFile` を使用して、現在のテンプレート ファイルの名前を示すこともできます。  
  
 `this.Host` \(VB の場合は `Me.Host`\) の型は、`Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost` です。  
  
### [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] からデータを取得する  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で提供されるサービスを使用するには、`hostSpecific` 属性を設定し、`EnvDTE` アセンブリを読み込みます。  その後、IServiceProvider.GetCOMService\(\) を使用して、DTE などのサービスにアクセスできます。  次に例を示します。  
  
```scr  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#  
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));  
#>  
  
Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>  
  
```  
  
> [!TIP]
>  テキスト テンプレートは独自のアプリ ドメインで実行され、サービスはマーシャリングによってアクセスされます。  この状況では、GetCOMService\(\) は GetService\(\) よりも信頼性が高くなります。  
  
##  <a name="Regenerating"></a> コードを自動的に再生成する  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューションには、1 つの入力モデルを使用して複数のファイルを生成するのが一般的です。  各ファイルはそれぞれ対応するテンプレートから生成されますが、すべてのテンプレートは同じモデルを参照します。  
  
 ソース モデルが変更された場合は、ソリューションのすべてのテンプレートを再度実行する必要があります。  これを手動で行うには、**\[ビルド\]** メニューの **\[すべてのテンプレートの変換\]** をクリックします。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK がインストールされている場合は、ビルドを実行するたびにすべてのテンプレートが自動的に変換されるように設定できます。  そのためには、プロジェクト ファイル \(.csproj または .vbproj\) をテキスト エディターで編集し、ファイルの末尾付近の、他の `<import>` ステートメントよりも後に次のコード行を追加します。  
  
```  
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v11.0\TextTemplating\Microsoft.TextTemplating.targets" />  
<PropertyGroup>  
   <TransformOnBuild>true</TransformOnBuild>  
   <!-- Other properties can be inserted here -->  
</PropertyGroup>  
```  
  
 詳細については、「[ビルド処理でのコード生成](../modeling/code-generation-in-a-build-process.md)」を参照してください。  
  
## エラー レポート  
 エラー メッセージおよび警告メッセージを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のエラー ウィンドウに表示するには、次のメソッドを使用します。  
  
```  
Error("An error message");  
Warning("A warning message");  
```  
  
##  <a name="Converting"></a> 既存のファイルをテンプレートに変換する  
 テンプレートには、見た目は生成されるファイルとよく似ていて、そこに、プログラム コードが挿入されているという特徴があります。  このことを利用すると、テンプレートを効率的に作成することができます。  最初に通常のファイル \([!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ファイルなど\) をプロトタイプとして作成し、その後、結果のファイルにバリエーションを持たせるための生成コードを徐々に適用していく方法です。  
  
#### 既存のファイルをデザイン時テンプレートに変換するには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、`.cs`、`.vb` など、生成する種類のファイルを `.resx` プロジェクトに追加します。  
  
2.  この新しいファイルをテストして、ファイルが機能することを確認します。  
  
3.  ソリューション エクスプローラーで、ファイル名拡張子を **.tt** に変更します。  
  
4.  **.tt** ファイルの次のプロパティを確認します。  
  
    |||  
    |-|-|  
    |**カスタム ツール \=**|**TextTemplatingFileGenerator**|  
    |**ビルド アクション \=**|**なし**|  
  
5.  ファイルの先頭に次の行を挿入します。  
  
    ```  
    <#@ template debug="false" hostspecific="false" language="C#" #>  
    <#@ output extension=".cs" #>  
    ```  
  
     テンプレートのコード生成機構を [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] で記述する場合は、`language` 属性を `"VB"` ではなく、`"C#"` に設定してください。  
  
     `extension` 属性を、生成するファイルの種類のファイル名拡張子 \(`.cs`、`.resx`、`.xml` など\) に設定します。  
  
6.  ファイルを保存します。  
  
     指定された拡張子の従属ファイルが作成されます。  そのプロパティは、ファイルの種類に対応します。  たとえば、.cs ファイルの **\[ビルド アクション\]** プロパティは **\[コンパイル\]** になります。  
  
     生成されたファイルのコンテンツが、元のファイルと同じであることを確認します。  
  
7.  ファイルの可変部分を見極めます。  たとえば、特定の条件を満たした場合にのみ出力する部分や、繰り返し出力する部分、特定の値をどこで変化させるかなどを決めます。  コードを生成するためのコードを挿入します。  ファイルを保存し、従属ファイルが正しく生成されたことを確認します。  この手順を繰り返します。  
  
## コード生成のガイドライン  
 「[T4 テキスト テンプレートの記述に関するガイドライン](../modeling/guidelines-for-writing-t4-text-templates.md)」を参照してください。  
  
## 次の手順  
  
|次の手順|トピック|  
|----------|----------|  
|補助的な関数、インクルード ファイル、外部データなどを使用したコードを組み合わせて、より高度なテキスト テンプレートを作成し、デバッグする。|[T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)|  
|実行時にテンプレートからドキュメントを生成する。|[T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の外部でテキストの生成を行う。|[TextTransform ユーティリティを使用したファイルの生成](../modeling/generating-files-with-the-texttransform-utility.md)|  
|ドメイン固有言語の形式でデータを変換する。|[ドメイン固有言語からのコード生成](../modeling/generating-code-from-a-domain-specific-language.md)|  
|独自のデータ ソースを変換するためのディレクティブ プロセッサを作成する。|[T4 テキスト変換のカスタマイズ](../modeling/customizing-t4-text-transformation.md)|  
  
## 参照  
 [T4 テキスト テンプレートの記述に関するガイドライン](../modeling/guidelines-for-writing-t4-text-templates.md)