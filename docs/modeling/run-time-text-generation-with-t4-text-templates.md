---
title: "T4 テキスト テンプレートを使用した実行時テキスト生成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "前処理されたテキスト テンプレート プロジェクト項目"
  - "テキスト テンプレート, 生成 (ファイルを実行時に)"
  - "テキスト テンプレート, TransformText() メソッド"
  - "TextTemplatingFilePreprocessor カスタム ツール"
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: 22
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 22
---
# T4 テキスト テンプレートを使用した実行時テキスト生成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用して、アプリケーション実行時の文字列を生成できます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]テキスト テンプレートの実行時。  アプリケーションを実行するコンピューターに [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がインストールされている必要はありません。  コンパイル時に、テンプレートを実行時に実行されるコードが生成されますので実行時のテンプレート「テキスト テンプレートを前処理」呼ばれます。  
  
 各テンプレートは、生成される文字列に表示されるテキストとプログラム コードのフラグメントを組み合わせたものです。  プログラムのフラグメントでは、文字列の可変部分の値を提供すると共に、条件付きの部分と繰り返し部分を制御します。  
  
 たとえば、HTML レポートを作成するアプリケーションでは、次のテンプレートを使用できます。  
  
```  
<#@ template language="C#" #>  
<html><body>  
<h1>Sales for Previous Month</h2>  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
This report is Company Confidential.  
</body></html>  
```  
  
 このテンプレートは、可変部分がプログラム コードに置き換えられた HTML ページであることに注意してください。  このようなページをデザインするには、まず、HTML ページの静的プロトタイプを作成します。  その後、テーブルや他の可変部分を、状況に応じて変化するコンテンツを生成するプログラム コードに置き換えます。  
  
 アプリケーションでテンプレートを使用すると、一連の Write ステートメントなどに比べ、出力の最終的な形式を確認しやすくなります。  出力の形式の変更が容易になり、信頼性も高まります。  
  
## 任意のアプリケーションでの実行時テキスト テンプレートの作成  
  
#### 実行時テキスト テンプレートを作成するには  
  
1.  ソリューション エクスプ ローラーで、プロジェクトのショートカット メニューを選択**追加**、 **新しい項目**。  
  
2.  **\[新しい項目の追加** ダイアログ ボックスで、 **ランタイム テキスト テンプレート**。  \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の場合は、**\[共通項目\] \- \[全般\]** にあります。\)  
  
3.  テンプレート ファイルの名前を入力します。  
  
    > [!NOTE]
    >  このテンプレート ファイル名は、生成されたコードでクラス名として使用されます。  そのため、スペースと区切り記号は使用しないでください。  
  
4.  選択**追加**。  
  
     **.tt** という拡張子を持つ新しいファイルが作成されます。  その "**カスタム ツール**" プロパティは **TextTemplatingFilePreprocessor** に設定されます。  これは、次の行が含まれます。  
  
    ```  
    <#@ template language="C#" #>  
    <#@ assembly name="System.Core" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="System.Text" #>  
    <#@ import namespace="System.Collections.Generic" #>  
    ```  
  
## 既存のファイルから実行時テンプレートへの変換  
 テンプレートを作成する場合は、既存の出力例を変換することをお勧めします。  たとえば、HTML ファイルを生成するアプリケーションの場合は、まずプレーン HTML ファイルを作成します。  このファイルが正しく機能することと、その表示形式が適切であることを確認してください。  その後で、このファイルを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトに追加し、テンプレートに変換します。  
  
#### 既存のテキスト ファイルを実行時テンプレートに変換するには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトにファイルを追加します。  ソリューション エクスプ ローラーで、プロジェクトのショートカット メニューを選択**追加**、 **既存アイテム**。  
  
2.  ファイルの **\[カスタム ツール\]** プロパティを **TextTemplatingFilePreprocessor** に設定します。  ソリューション エクスプ ローラーで、ファイルのショートカット メニューを選択する**のプロパティ**。  
  
    > [!NOTE]
    >  プロパティが既に設定されている場合は、**TextTemplatingFileGenerator** ではなく **TextTemplatingFilePreprocessor** になっていることを確認してください。  この状況は、拡張子が **.tt** のファイルを追加した場合に発生することがあります。  
  
3.  ファイル名拡張子を **.tt** に変更します。  この手順は省略できますが、このようにすると、ファイルが不適切なエディターで開かれるのを防ぐことができます。  
  
4.  ファイル名のメインの部分からスペースと区切り記号を削除します。  たとえば、"My Web Page.tt" ではなく "MyWebPage.tt" が正しい形式です。  このファイル名は、生成されたコードでクラス名として使用されます。  
  
5.  ファイルの先頭に次の行を挿入します。  Visual Basic プロジェクトで作業している場合は、"C\#" を "VB" に置き換えます。  
  
     `<#@ template language="C#" #>`  
  
## 実行時テンプレートのコンテンツ  
  
### template ディレクティブ  
 次のように、テンプレートの先頭行はファイル作成時の状態のままにしておきます。  
  
 `<#@ template language="C#" #>`  
  
 言語のパラメーターは、プロジェクトの言語によって変わります。  
  
### プレーン コンテンツ  
 **.tt** ファイルを編集し、アプリケーションで生成するテキストを追加します。  次に例を示します。  
  
```  
<html><body>  
<h1>Sales for January</h2>  
<!-- table to be inserted here -->  
This report is Company Confidential.  
</body></html>  
```  
  
### 埋め込みプログラム コード  
 `<#` と `#>` の間には、プログラム コードを挿入できます。  次に例を示します。  
  
```c#  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
```  
  
```vb#  
<table>  
<#  
    For i As Integer = 1 To 10  
#>  
    <tr><td>Test name <#= i #> </td>  
      <td>Test value <#= i*i #> </td></tr>  
<#  
    Next  
#>  
</table>  
  
```  
  
 ステートメントは `<# ... #>` の間に挿入され、式は `<#= ... #>` の間に挿入されていることに注意してください。  詳細については、「[T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)」を参照してください。  
  
## テンプレートの使用  
  
### テンプレートからビルドされるコード  
 **.tt** ファイルを保存するたびに、従属する **.cs** ファイルまたは **.vb** ファイルが生成されます。  このファイルをソリューション エクスプローラーで表示するには、**.tt** ファイルのノードを展開します。  Visual Basic プロジェクトの場合、このノードを展開するには、先にソリューション エクスプローラーのツール バーの **\[すべてのファイルを表示\]** をクリックする必要があります。  
  
 この従属ファイルには、`TransformText()` というメソッドを含む部分クラスが含まれます。  このメソッドは、アプリケーションから呼び出すことができます。  
  
### 実行時のテキストの生成  
 アプリケーション コードでは、次のような呼び出しを使用してテンプレートのコンテンツを生成できます。  
  
```c#  
MyWebPage page = new MyWebPage();  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
  
```  
  
```vb#  
Dim page = New My.Templates.MyWebPage  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
 生成されたクラスを特定の名前空間に配置するには、テキスト テンプレート ファイルの **"カスタム ツールの名前空間"** プロパティを設定します。  
  
### ランタイム テキスト テンプレートのデバッグ  
 デバッグし、通常のコードと同じようにランタイム テキスト テンプレートをテストします。  
  
 テキスト テンプレートでは、ブレークポイントを設定できます。  Visual Studio からのデバッグ モードでアプリケーションを起動する場合は、コードをステップ実行し、通常の方法で \[ウォッチ式の評価することができます。  
  
### コンストラクターへのパラメーターの引き渡し  
 通常、テンプレートでは、アプリケーションの他の部分からデータをインポートする必要があります。  この処理を容易にするため、テンプレートによってビルドされるコードは部分クラスになります。  同じクラスの別の部分をプロジェクトの別のファイルに作成できます。  そのファイルには、テンプレートに埋め込まれたコードとアプリケーションの残りの部分の両方からアクセスできるパラメーター、プロパティ、および関数を持つコンストラクターを含めることができます。  
  
 たとえば、**MyWebPageCode.cs** というファイルを別に作成できます。  
  
```c#  
partial class MyWebPage  
{  
    private MyData m_data;  
    public MyWebPage(MyData data) { this.m_data = data; }}  
```  
  
 テンプレート ファイルの **MyWebPage.tt** では、次のように記述できます。  
  
```c#  
<h2>Sales figures</h2>  
<table>  
<# foreach (MyDataItem item in m_data.Items)   
   // m_data is declared in MyWebPageCode.cs  
   { #>  
      <tr><td> <#= item.Name #> </td>  
          <td> <#= item.Value #> </td></tr>  
<# } // end of foreach  
#>  
</table>  
```  
  
 このテンプレートをアプリケーションで使用するには、次のように記述します。  
  
```c#  
MyData data = ...;  
MyWebPage page = new MyWebPage(data);  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
```  
  
#### Visual Basic のコンストラクター パラメーター  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では、**MyWebPageCode.vb** という別のファイルに次のコードが含まれています。  
  
```vb#  
Namespace My.Templates  
  Partial Public Class MyWebPage  
    Private m_data As MyData  
    Public Sub New(ByVal data As MyData)  
      m_data = data  
    End Sub  
  End Class  
End Namespace  
```  
  
 テンプレート ファイルに次のコードを含めることができます。  
  
```vb#  
<#@ template language="VB" #>  
<html><body>  
<h1>Sales for January</h2>  
<table>  
<#  
    For Each item In m_data.Items  
#>  
    <tr><td>Test name <#= item.Name #> </td>  
      <td>Test value <#= item.Value #> </td></tr>  
<#  
    Next  
#>  
</table>  
This report is Company Confidential.  
</body></html>  
  
```  
  
 パラメーターをコンストラクターに渡すことによってテンプレートが呼び出されます。  
  
```vb#  
Dim data = New My.Templates.MyData  
    ' Add data values here ....  
Dim page = New My.Templates.MyWebPage(data)  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
#### テンプレートのプロパティへのデータの引き渡し  
 データをテンプレートに渡す方法として、部分クラス定義でパブリック プロパティをテンプレート クラスに追加する方法もあります。  アプリケーションで、`TransformText()` を呼び出す前にこれらのプロパティを設定できます。  
  
 また、部分定義でテンプレート クラスにフィールドを追加することもできます。  この場合、テンプレートの連続的な実行の間でデータを渡すことができます。  
  
### コードでの部分クラスの使用  
 多くの開発者は、テンプレートにコードの大きな本体を記述するのは望ましくないと考えています。  代わりに、テンプレート ファイルと同じ名前の部分クラスにメソッドを定義します。  テンプレートからこれらのメソッドを呼び出します。  このようにすると、テンプレートによって対象の出力文字列の表示状態がより明確に示されるようになります。  結果の表示状態を、表示されるデータの作成ロジックから切り離して検討できます。  
  
### アセンブリと参照  
 テンプレート コードで .NET やその他のアセンブリ \(**System.Xml.dll** など\) を参照する場合は、通常の方法でプロジェクトの **\[参照設定\]** に追加する必要があります。  
  
 `using` ステートメントと同じ方法で名前空間をインポートする場合は、`import` ディレクティブを使用できます。  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 これらのディレクティブは、ファイルの先頭 \(`<#@template` ディレクティブの直後\) に記述する必要があります。  
  
### 共有コンテンツ  
 複数のテンプレートで共有するテキストがある場合は、そのテキストを独立したファイルに記述し、テキストを使用する各ファイルでそのファイルをインクルードできます。  
  
```  
<#@include file="CommonHeader.txt" #>  
```  
  
 インクルードするコンテンツには、プログラム コードとプレーンテキストの組み合わせを含めることができます。また、他の include ディレクティブやその他のディレクティブを含めることもできます。  
  
 include ディレクティブは、テンプレート ファイルまたはインクルード ファイルのテキスト内の任意の場所で使用できます。  
  
### 実行時テキスト テンプレート間での継承  
 基本クラス テンプレートを作成することで、実行時テンプレート間でコンテンツを共有できます。テンプレートは、抽象基本クラス テンプレートでもかまいません。  使用、 `inherits`のパラメーター、 `<@#template#>`別のランタイムのテンプレート クラスを参照するディレクティブ。  
  
#### 継承パターン: 基本メソッド内のフラグメント  
 次の例で使用しているパターンでは、以下の点に注目してください。  
  
-   `SharedFragments` 基本クラスでは、クラス機能ブロック \(`<#+ ... #>`\) 内でメソッドを定義しています。  
  
-   基本クラスには、フリーテキストは含まれていません。  代わりに、クラス機能メソッド内にすべてのテキスト ブロックが含まれています。  
  
-   `SharedFragments` で定義されたメソッドを派生クラスで呼び出しています。  
  
-   アプリケーションでは、派生クラスの `TextTransform()` メソッドを呼び出していますが、`SharedFragments` 基本クラスは変換していません。  
  
-   ランタイム テキスト テンプレートの基本と派生クラスの両方は：、 **カスタム ツール** でプロパティを設定  **TextTemplatingFilePreprocessor**。  
  
 **SharedFragments.tt:**  
  
```c#  
<#@ template language="C#" #>  
<#+  
protected void SharedText(int n)  
{  
#>  
   Shared Text <#= n #>  
<#+  
}  
// Insert more methods here if required.  
#>  
  
```  
  
 **MyTextTemplate1.tt:**  
  
```c#  
<#@ template language="C#" inherits="SharedFragments" #>  
begin 1  
   <# SharedText(2); #>  
end 1  
  
```  
  
 **MyProgram.cs:**  
  
```c#  
...   
MyTextTemplate1 t1  = new MyTextTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **結果の出力:**  
  
```  
begin 1  
    Shared Text 2  
end 1  
```  
  
#### 継承パターン: 基本本体内のテキスト  
 テンプレートの継承を使用するもう 1 つの方法では、テキストの大半を基本テンプレートに定義します。  派生テンプレートでは、基本コンテンツに組み込むデータとテキスト フラグメントを提供します。  
  
 **AbstractBaseTemplate1.tt:**  
  
```c#  
<#@ template language="C#" #>  
  
Here is the description for this derived template:  
  <#= this.Description #>  
  
Here is the fragment specific to this derived template:  
<#   
  this.PushIndent("  ");  
  SpecificFragment(42);   
  this.PopIndent();  
#>  
End of common template.  
<#+   
  // State set by derived class before calling TextTransform:  
  protected string Description = "";  
  // 'abstract' method to be defined in derived classes:  
  protected virtual void SpecificFragment(int n) { }  
#>  
  
```  
  
 **DerivedTemplate1.tt:**  
  
```c#  
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>  
<#   
  // Set the base template properties:  
  base.Description = "Description for this derived class";   
  
  // Run the base template:  
  base.TransformText();  
  
#>  
End material for DerivedTemplate1.  
  
<#+  
// Provide a fragment specific to this derived template:  
  
protected override void SpecificFragment(int n)  
{  
#>  
   Specific to DerivedTemplate1 : <#= n #>  
<#+  
}  
#>  
  
```  
  
 **アプリケーション コード:**  
  
```c#  
...   
DerivedTemplate1 t1 = new DerivedTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **結果の出力:**  
  
```  
Here is the description for this derived template:  
  Description for this derived class  
  
Here is the fragment specific to this derived template:  
     Specific to DerivedTemplate1 : 42  
End of common template.  
End material for DerivedTemplate1.  
```  
  
## 関連トピック  
 デザイン時テンプレート: テンプレートを使用してアプリケーションの一部になるコードを生成する場合は、「[T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)」を参照してください。  
  
 テンプレートとその内容がコンパイル時に決定されると、任意のアプリケーションで実行時のテンプレートを使用できます。  ただし、実行時に変更されるテンプレートからテキストを生成する [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 拡張機能を作成する場合は、「[VS 拡張機能内でのテキスト変換の呼び出し](../modeling/invoking-text-transformation-in-a-vs-extension.md)」を参照してください。  
  
## 参照  
 [コード生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)   
 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)   
 [T4 の理解: oleg が Sych によってテキスト テンプレートを前処理](http://www.olegsych.com/2009/09/t4-preprocessed-text-templates/)