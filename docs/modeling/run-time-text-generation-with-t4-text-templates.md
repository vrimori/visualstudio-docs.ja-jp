---
title: T4 テキスト テンプレートを使用した実行時テキスト生成
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5b39437dc5f81b17c0bcfe27dbb7b8d99bebbc87
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953116"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>T4 テキスト テンプレートを使用した実行時テキスト生成

Visual Studio の実行時テキスト テンプレートを使用して、実行時に、アプリケーションでのテキスト文字列を生成できます。 アプリケーションが実行されるコンピューターは、Visual studio をする必要はありません。 実行時テンプレートとも呼ばれる「前処理されたテキスト テンプレート」テンプレートは、コンパイル時に実行時に実行されるコードを生成するためです。

各テンプレートは、テキストの組み合わせ、生成された文字列は、およびプログラム コードのフラグメントに表示されます。 プログラムのフラグメントは、文字列の変数部分の値を指定しも条件付きおよび繰り返される部分を制御します。

たとえば、次のテンプレートは、HTML レポートを作成するアプリケーションで使用可能性があります。

```html
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

テンプレートは、プログラム コードに置き換えられました変数部分を HTML ページであることを確認します。 静的な HTML ページのプロトタイプを記述して、このようなページのデザインを開始する可能性があります。 何度で 1 つから、次に変化するコンテンツを生成するプログラム コードで、テーブルとその他の変数部分を置換でした。

テンプレートを使用して、アプリケーションでは出力の最終的な形式をたとえば、長い一連の書き込みステートメントよりもわかりやすくします。 簡単かつ確実には、出力の形式に変更を加えるです。

## <a name="creating-a-run-time-text-template-in-any-application"></a>任意のアプリケーションで実行時テキスト テンプレートの作成

### <a name="to-create-a-run-time-text-template"></a>実行時テキスト テンプレートを作成するには

1. ソリューション エクスプ ローラーで、プロジェクトのショートカット メニューを選択**追加**、**新しい項目の**します。

2. **新しい項目の追加**ダイアログ ボックスで、**実行時テキスト テンプレート**です。 (Visual Basic では、下にある検索**共通項目** > **全般**)。

3. テンプレート ファイルの名前を入力します。

    > [!NOTE]
    > テンプレート ファイルの名前は、生成されたコード内のクラス名として使用されます。 そのため、その必要はありませんスペースまたは句読点。

4. **[追加]** をクリックします。

    新しいファイルが作成された拡張子を持つ **.tt**です。 その**カスタム ツール**プロパティに設定されている**TextTemplatingFilePreprocessor**です。 次の行が含まれています。

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>既存のファイルを実行時テンプレートに変換します。

テンプレートを作成することをお勧めは、既存の出力の例を変換します。 たとえば、アプリケーションは HTML ファイルを生成する場合は、プレーン HTML ファイルを作成することで開始できます。 正常に動作して、外観が正しいことを確認してください。 Visual Studio プロジェクトに追加し、テンプレートに変換します。

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>実行時テンプレートに既存のテキスト ファイルを変換するには

1. Visual Studio プロジェクトにファイルをインクルードします。 ソリューション エクスプ ローラーで、プロジェクトのショートカット メニューを選択**追加** > **既存項目の**します。

2. ファイルの設定**カスタム ツール**プロパティを**TextTemplatingFilePreprocessor**です。 ソリューション エクスプ ローラーで、ファイルのショートカット メニューを選択**プロパティ**です。

    > [!NOTE]
    > プロパティは既に設定されている場合であることを確認してください**TextTemplatingFilePreprocessor**および not **TextTemplatingFileGenerator**です。 これは、既に拡張子を持つファイルを含める場合に発生することができます **.tt**です。

3. ファイル名拡張子を変更する **.tt**です。 この手順はオプションですが、これを回避できます不適切なエディターでファイルを開きます。

4. ファイル名の本体からスペースや句読点を削除します。 たとえば"My Web Page.tt"がない、正しいであっても"MyWebPage.tt"が正しくです。 ファイル名は、生成されたコード内のクラス名として使用されます。

5. ファイルの先頭に次の行を挿入します。 Visual Basic プロジェクトで作業している場合交換して"c#""VB"を使用してください。

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>実行時テンプレートの内容

### <a name="template-directive"></a>Template ディレクティブ

ファイルを作成した時とは、テンプレートの最初の行をしてください。

`<#@ template language="C#" #>`

Language パラメーターは、プロジェクトの言語によって異なります。

### <a name="plain-content"></a>プレーン コンテンツ

編集、 **.tt**アプリケーションを生成するテキストを格納するファイル。 例えば:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>埋め込まれたプログラム コード

間でのプログラム コードを挿入する`<#`と`#>`です。 例えば:

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

間、ステートメントが挿入されることに注意してください。`<# ... #>`は式に挿入し`<#= ... #>`です。 詳細については、次を参照してください。 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)です。

## <a name="using-the-template"></a>テンプレートの使用

### <a name="the-code-built-from-the-template"></a>テンプレートから構築されたコード

保存すると、 **.tt**ファイル、子会社 **.cs**または **.vb**ファイルを生成します。 ソリューション エクスプ ローラーでこのファイルを表示する展開、 **.tt**ファイル ノード。 Visual Basic プロジェクトで最初に選択**すべてのファイル**ソリューション エクスプ ローラーのツールバー。

従属ファイルが呼び出されるメソッドを格納する部分クラスが含まれている通知`TransformText()`です。 このメソッドは、アプリケーションから呼び出すことができます。

### <a name="generating-text-at-run-time"></a>実行時にテキストを生成します。

アプリケーション コードでは、次のような呼び出しを使用して、テンプレートのコンテンツを生成できます。

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

特定の名前空間で生成されたクラスを配置するには設定、**カスタム ツール Namespace**テキスト テンプレート ファイルのプロパティです。

### <a name="debugging-runtime-text-templates"></a>デバッグの実行時テキスト テンプレート

デバッグし、通常のコードと同じ方法で実行時テキスト テンプレートをテストします。

テキスト テンプレートでは、ブレークポイントを設定できます。 Visual Studio からのデバッグ モードでアプリケーションを起動する場合、コードをステップ実行し、通常の方法でウォッチ式を評価できます。

### <a name="passing-parameters-in-the-constructor"></a>コンス トラクターにパラメーターの引き渡し

通常、テンプレートでは、アプリケーションの他の部分から一部のデータをインポートする必要があります。 簡単にするには、テンプレートに組み込まれているコードは、部分クラスです。 プロジェクトで、別のファイルで、同じクラスの別の部分を作成できます。 そのファイルには、パラメーター、プロパティ、およびテンプレートに埋め込まれているコードと、アプリケーションの残りの部分の両方にアクセスできる関数を持つコンス トラクターを含めることができます。

たとえば、別のファイルを作成できます**MyWebPageCode.cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

テンプレートは、ファイルで**MyWebPage.tt**、記述できます。

```html
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

Visual Basic では、別のファイルで**MyWebPageCode.vb**が含まれています。

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

```html
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

テンプレートは、コンス トラクターにパラメーターを渡すことによって呼び出すことができます。

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>テンプレートのプロパティでデータの受け渡し

データの受け渡しをテンプレートに別の方法では、部分クラス定義内のテンプレート クラスにパブリック プロパティを追加します。 呼び出す前に、アプリケーションが、プロパティを設定できます`TransformText()`です。

部分定義で、テンプレート クラスにフィールドを追加することもできます。 これにより、テンプレートの連続的に実行の間でデータを渡すことができます。

### <a name="use-partial-classes-for-code"></a>コードの部分クラスを使用します。

多くの開発者は、テンプレートで、大量のコードを記述しないでを優先します。 代わりに、テンプレート ファイルと同じ名前を持つ部分クラスにメソッドを定義できます。 テンプレートからこれらのメソッドを呼び出します。 これにより、複数のテンプレートは明確にターゲットの出力の文字列のようになります。 結果の外観に関するディスカッションは、表示されるデータの作成のロジックから分離できます。

### <a name="assemblies-and-references"></a>アセンブリと参照

場合は、テンプレート コードなど、.NET またはその他のアセンブリの参照を**System.Xml.dll**、プロジェクトの追加**参照**通常の方法でします。

同じ方法で名前空間をインポートするかどうか、`using`ステートメントでは、これを行うと、`import`ディレクティブ。

```
<#@ import namespace="System.Xml" #>
```

これらのディレクティブは、後すぐに、ファイルの先頭に配置する必要があります、`<#@template`ディレクティブです。

### <a name="shared-content"></a>共有コンテンツ

複数のテンプレート間で共有されるテキストがあれば、別のファイルに配置およびを表示する各ファイルに含めるようにできます。

```
<#@include file="CommonHeader.txt" #>
```

含まれるコンテンツは、プログラム コードおよびテキストの形式の任意の組み合わせを含めることができ、その他を含めることができます、include ディレクティブや他のディレクティブ。

Include ディレクティブは、テンプレート ファイルまたはインクルード ファイルのテキスト内の任意の場所で使用できます。

### <a name="inheritance-between-run-time-text-templates"></a>実行時テキスト テンプレート間の継承

抽象にすることで、基底クラス テンプレートを記述して実行時テンプレート間でコンテンツを共有することができます。 使用して、`inherits`のパラメーター、`<@#template#>`別の実行時テンプレート クラスを参照するディレクティブ。

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>継承のパターン: 基本メソッド内の断片化

パターンでは、次の例で使用される、次の点に注意してください。

- 基本クラス`SharedFragments`クラス機能ブロック内でメソッドを定義`<#+ ... #>`です。

- 基本クラスには、フリー テキストが含まれていません。 代わりに、すべてのテキスト ブロックは、クラス機能のメソッド内で発生します。

- 派生クラスで定義されているメソッドを呼び出します`SharedFragments`です。

- アプリケーションの呼び出し、 `TextTransform()` 、派生クラスのメソッドの基本クラスを変換しませんが、`SharedFragments`です。

- 両方の基本クラスと派生クラスは、実行時テキスト テンプレートです。つまり、**カスタム ツール**プロパティに設定されている**TextTemplatingFilePreprocessor**です。

**SharedFragments.tt:**

```
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

```
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

**結果として得られる出力:**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>基本の本文にテキストを継承のパターン:

テンプレートの継承を使用する他の方法でテキストの大部分は、基本テンプレートで定義されます。 派生テンプレートがデータを提供し、テキスト フラグメントを基本コンテンツに適合します。

**AbstractBaseTemplate1.tt:**

```
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

```
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

**アプリケーション コードに示します。**

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

デザイン時テンプレート: アプリケーションの一部になるコードを生成するテンプレートを使用する場合を参照してください[T4 テキスト テンプレートを使用して、デザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)です。

実行時テンプレートは、コンパイル時にテンプレートおよびその内容を特定のアプリケーションで使用できます。 実行時に、変更のテンプレートからテキストを生成する Visual Studio 拡張機能を記述するかどうかを参照してください。 [VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md)です。

## <a name="see-also"></a>関連項目

- [コード生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)
- [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)
- [T4 ツールボックス](http://olegsych.com/T4Toolbox/)