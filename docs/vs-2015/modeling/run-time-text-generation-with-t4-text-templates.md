---
title: T4 テキスト テンプレートを使用した実行時テキスト生成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 47b50ece6d4fff79618890cb388c997503d95ad0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214748"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>T4 テキスト テンプレートを使用した実行時テキスト生成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用して、実行時に、アプリケーションでのテキスト文字列を生成できます[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ランタイム テキスト テンプレート。 アプリケーションが実行されるコンピューターを持っていなくて[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 実行時テンプレートとも呼ばれます「前処理されたテキスト テンプレート」ため、コンパイル時に、テンプレートには、実行時に実行されるコードが生成されます。  
  
 各テンプレートは、テキストの組み合わせ、生成された文字列は、およびプログラム コードのフラグメントに表示されます。 プログラムのフラグメントは、文字列の変数部分の値を指定しも条件と繰り返される部分を制御します。  
  
 たとえば、次のテンプレートは、HTML レポートを作成するアプリケーションで使用する可能性があります。  
  
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
  
 テンプレートは、プログラム コードに置き換えられました変数部分を HTML ページであることを確認します。 静的な HTML ページのプロトタイプを記述することで、このようなページのデザインを開始する可能性があります。 次は違いますからが変化するコンテンツを生成するプログラム コードで、テーブルとその他の変数部分を置き換える可能性があります。  
  
 アプリケーションは、テンプレートを使用してこれが、長い一連のステートメントの書き込みなどのよりも、出力の最終形式を参照してください簡単です。 簡単かつ確実には、出力の形式を変更します。  
  
## <a name="creating-a-run-time-text-template-in-any-application"></a>任意のアプリケーションで実行時テキスト テンプレートの作成  
  
#### <a name="to-create-a-run-time-text-template"></a>実行時テキスト テンプレートを作成するには  
  
1.  ソリューション エクスプ ローラーで、プロジェクトのショートカット メニューの 選択**追加**、**新しい項目の**します。  
  
2.  **新しい項目の追加**ダイアログ ボックスで、**ランタイム テキスト テンプレート**します。 (で[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]下を見て**共通 Items\General**)。  
  
3.  テンプレート ファイルの名前を入力します。  
  
    > [!NOTE]
    >  テンプレート ファイルの名前は、生成されたコード内のクラス名として使用されます。 そのため、スペースまたは句読点をことことはできません。  
  
4.  **[追加]** をクリックします。  
  
     拡張子を持つ新しいファイルが作成された **.tt**します。 その**カスタム ツール**プロパティに設定されて**TextTemplatingFilePreprocessor**します。 次の行が含まれています。  
  
    ```  
    <#@ template language="C#" #>  
    <#@ assembly name="System.Core" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="System.Text" #>  
    <#@ import namespace="System.Collections.Generic" #>  
    ```  
  
## <a name="converting-an-existing-file-to-a-run-time-template"></a>既存のファイルを実行時テンプレートに変換します。  
 テンプレートを作成する優れた方法は、既存の出力の例を変換します。 など、アプリケーションは HTML ファイルを生成する場合は、プレーンな HTML ファイルを作成して開始できます。 正しく動作して、その外観が正しいことを確認してください。 含める、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]プロジェクト、テンプレートに変換します。  
  
#### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>実行時テンプレートに既存のテキスト ファイルを変換するには  
  
1.  ファイルを含める、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]プロジェクト。 ソリューション エクスプ ローラーで、プロジェクトのショートカット メニューの 選択**追加**、**既存項目の**します。  
  
2.  ファイルの設定**カスタム ツール**プロパティを**TextTemplatingFilePreprocessor**します。 ソリューション エクスプ ローラーで、ファイルのショートカット メニューの 選択**プロパティ**します。  
  
    > [!NOTE]
    >  プロパティが既に設定されている場合がある確認**TextTemplatingFilePreprocessor**なく**TextTemplatingFileGenerator**します。 拡張機能は既にファイルをインクルードする場合に生じる **.tt**します。  
  
3.  ファイル名拡張子を変更する **.tt**します。 この手順は省略可能ですが、不適切なエディターでファイルを開いてを防ぐことができます。  
  
4.  ファイル名の主要部分から、スペースや句読点を削除します。 たとえば"My Web Page.tt"はいない正しいですが、"MyWebPage.tt"が正しくします。 ファイル名は、生成されたコード内のクラス名として使用されます。  
  
5.  ファイルの先頭に次の行を挿入します。 Visual Basic プロジェクトで作業している場合を交換して"c#"と"VB"です。  
  
     `<#@ template language="C#" #>`  
  
## <a name="the-content-of-the-run-time-template"></a>実行時テンプレートの内容  
  
### <a name="template-directive"></a>テンプレート ディレクティブ  
 ファイルを作成した時とは、テンプレートの最初の行をしてください。  
  
 `<#@ template language="C#" #>`  
  
 言語パラメーターは、プロジェクトの言語によって異なります。  
  
### <a name="plain-content"></a>プレーンなコンテンツ  
 編集、 **.tt**アプリケーションを生成するテキストを格納するファイル。 例えば:  
  
```  
<html><body>  
<h1>Sales for January</h2>  
<!-- table to be inserted here -->  
This report is Company Confidential.  
</body></html>  
```  
  
### <a name="embedded-program-code"></a>埋め込まれたプログラム コード  
 間のプログラム コードを挿入する`<#`と`#>`します。 例えば:  
  
```csharp  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
```  
  
```vb  
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
  
 間、ステートメントが挿入されることに注意してください。`<# ... #>`式に挿入されますと`<#= ... #>`します。 詳細については、次を参照してください。 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)です。  
  
## <a name="using-the-template"></a>テンプレートの使用  
  
### <a name="the-code-built-from-the-template"></a>テンプレートから作成されるコード  
 保存するたびに、 **.tt**ファイル、子会社 **.cs**または **.vb**ファイルが生成されます。 ソリューション エクスプ ローラーでこのファイルを表示するには展開、 **.tt**ファイル ノード。 Visual Basic プロジェクトですることがクリックした後、ノードを展開**すべてのファイル**ソリューション エクスプ ローラーのツールバー。  
  
 この関連会社のファイルと呼ばれるメソッドを含む部分クラスが含まれている通知`TransformText()`します。 このメソッドは、アプリケーションから呼び出すことができます。  
  
### <a name="generating-text-at-run-time"></a>実行時にテキストを生成します。  
 アプリケーション コードでは、このような呼び出しを使用して、テンプレートのコンテンツを生成できます。  
  
```csharp  
MyWebPage page = new MyWebPage();  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
  
```  
  
```vb  
Dim page = New My.Templates.MyWebPage  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
 生成されたクラスを特定の名前空間に配置するには設定、**カスタム ツールの Namespace**テキスト テンプレート ファイルのプロパティ。  
  
### <a name="debugging-runtime-text-templates"></a>ランタイム テキスト テンプレートのデバッグ  
 デバッグし、通常のコードと同じ方法でランタイム テキスト テンプレートをテストします。  
  
 テキスト テンプレートでは、ブレークポイントを設定できます。 Visual Studio からデバッグ モードでアプリケーションを開始する場合は、コードをステップ実行し、通常の方法でウォッチ式を評価できます。  
  
### <a name="passing-parameters-in-the-constructor"></a>コンス トラクターでパラメーターの引き渡し  
 通常、テンプレートでは、アプリケーションの他の部分から一部のデータをインポートする必要があります。 簡単にするには、テンプレートによって作成されるコードは、部分クラスです。 プロジェクトで、別のファイルで、同じクラスの別の部分を作成できます。 そのファイルには、パラメーター、プロパティ、およびテンプレートでは、埋め込まれているコードと、アプリケーションの残りの部分の両方にアクセスできる関数を持つコンス トラクターを含めることができます。  
  
 たとえば、別のファイルを作成できます**MyWebPageCode.cs**:  
  
```csharp  
partial class MyWebPage  
{  
    private MyData m_data;  
    public MyWebPage(MyData data) { this.m_data = data; }}  
```  
  
 テンプレート ファイルで**MyWebPage.tt**、記述する可能性があります。  
  
```csharp  
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
  
 アプリケーションでこのテンプレートを使用します。  
  
```csharp  
MyData data = ...;  
MyWebPage page = new MyWebPage(data);  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
```  
  
#### <a name="constructor-parameters-in-visual-basic"></a>Visual Basic でコンス トラクターのパラメーター  
 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]、別のファイル**MyWebPageCode.vb**が含まれています。  
  
```vb  
Namespace My.Templates  
  Partial Public Class MyWebPage  
    Private m_data As MyData  
    Public Sub New(ByVal data As MyData)  
      m_data = data  
    End Sub  
  End Class  
End Namespace  
```  
  
 テンプレート ファイルを含む可能性があります。  
  
```vb  
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
  
 テンプレート コンス トラクターでパラメーターを渡すことによって呼び出されます。  
  
```vb  
Dim data = New My.Templates.MyData  
    ' Add data values here ....  
Dim page = New My.Templates.MyWebPage(data)  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
#### <a name="passing-data-in-template-properties"></a>テンプレートのプロパティでデータを渡す  
 データ テンプレートを渡すことの代替方法では、部分クラス定義内のテンプレート クラスにパブリック プロパティを追加します。 呼び出す前に、アプリケーションがプロパティを設定できます`TransformText()`します。  
  
 部分定義で、テンプレート クラスにフィールドを追加することもできます。 これは、結果、連続的に、テンプレート実行の間でデータを渡すことができます。  
  
### <a name="use-partial-classes-for-code"></a>部分クラスを使用してコードを  
 多くの開発者は、テンプレートで、大量のコードの作成を回避するために優先します。 代わりに、テンプレート ファイルと同じ名前を持つ部分クラスでメソッドを定義します。 テンプレートからこれらのメソッドを呼び出します。 この方法で、テンプレートではより明確にどのようなターゲット出力文字列のようになります。 結果の外観に関するディスカッションは、作成、表示されるデータのロジックから分離できます。  
  
### <a name="assemblies-and-references"></a>アセンブリと参照  
 場合は、テンプレート コードなど、.NET またはその他のアセンブリの参照を**System.Xml.dll**、プロジェクトに追加する必要があります**参照**通常の方法でします。  
  
 同じ方法で名前空間をインポートするかどうか、`using`ステートメントでは、これを行うと、`import`ディレクティブ。  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 これらのディレクティブは、直後に、ファイルの先頭に配置する必要があります、`<#@template`ディレクティブ。  
  
### <a name="shared-content"></a>共有コンテンツ  
 複数のテンプレート間で共有されるテキストがあれば、別のファイルに配置およびを表示する各ファイルに含めることできます。  
  
```  
<#@include file="CommonHeader.txt" #>  
```  
  
 含まれるコンテンツは、プログラム コードやプレーン テキストでのあらゆる組み合わせを含めることができ、その他を含めることができますディレクティブおよび他のディレクティブが含まれます。  
  
 Include ディレクティブは、テンプレート ファイルまたはインクルード ファイルのテキスト内の任意の場所で使用できます。  
  
### <a name="inheritance-between-run-time-text-templates"></a>実行時テキスト テンプレート間の継承  
 抽象化できる基本クラス テンプレートを記述することで、実行時テンプレート間でコンテンツを共有することができます。 使用して、`inherits`のパラメーター、`<@#template#>`別のランタイム テンプレート クラスを参照するディレクティブ。  
  
#### <a name="inheritance-pattern-fragments-in-base-methods"></a>継承パターン: ベースのメソッドでフラグメント  
 次の例で使用されるパターンでは、次の点に注意してください。  
  
-   基本クラス`SharedFragments`クラス機能ブロック内のメソッドを定義します。`<#+ ... #>`します。  
  
-   基底クラスには、フリー テキストが含まれていません。 代わりに、すべてのテキスト ブロックは、クラスの機能のメソッド内で発生します。  
  
-   派生クラスで定義されているメソッドを呼び出す`SharedFragments`します。  
  
-   アプリケーションの呼び出し、 `TextTransform()` 、派生クラスのメソッドが基底クラスを変換しない`SharedFragments`します。  
  
-   基本と派生クラスの両方が実行時テキスト テンプレート: これは、**カスタム ツール**プロパティに設定されて**TextTemplatingFilePreprocessor**します。  
  
 **SharedFragments.tt:**  
  
```csharp  
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
  
```csharp  
<#@ template language="C#" inherits="SharedFragments" #>  
begin 1  
   <# SharedText(2); #>  
end 1  
  
```  
  
 **MyProgram.cs:**  
  
```csharp  
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
  
#### <a name="inheritance-pattern-text-in-base-body"></a>基本の本文にテキストを継承パターン:  
 テンプレートの継承を使用する別の方法でテキストの大部分は、基本のテンプレートで定義されます。 派生テンプレートは、データを提供し、テキスト フラグメント ベースのコンテンツに適合します。  
  
 **AbstractBaseTemplate1.tt:**  
  
```csharp  
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
  
```csharp  
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
  
```csharp  
...   
DerivedTemplate1 t1 = new DerivedTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **結果の出力。**  
  
```  
Here is the description for this derived template:  
  Description for this derived class  
  
Here is the fragment specific to this derived template:  
     Specific to DerivedTemplate1 : 42  
End of common template.  
End material for DerivedTemplate1.  
```  
  
## <a name="related-topics"></a>関連トピック  
 デザイン時テンプレート: コードを生成するテンプレートを使用する場合になるアプリケーションの一部を参照してください[T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)します。  
  
 実行時テンプレートは、コンパイル時にテンプレートおよびその内容を決定する、任意のアプリケーションで使用できます。 作成する場合は、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]拡張機能を実行時に、「テンプレートからテキストを生成する[VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md)します。  
  
## <a name="see-also"></a>関連項目  
 [コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)   
 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)   
 [Oleg Sych によって理解 T4: 前処理されたテキスト テンプレート](http://www.olegsych.com/2009/09/t4-preprocessed-text-templates/)



