---
title: "テキスト テンプレートのコントロール ブロック | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "テキスト テンプレート, テンプレート コード"
ms.assetid: bad198b9-57a4-4777-bd5b-ab6336c825f3
caps.latest.revision: 32
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 32
---
# テキスト テンプレートのコントロール ブロック
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コントロール ブロックを使用すると、出力を変更するためにテキスト テンプレートにコードを記述できます。  コントロール ブロックは 3 種類あり、左山かっこで区別されます。  
  
-   `<# Standard control blocks #>` には、ステートメントを含めることができます。  
  
-   `<#= Expression control blocks #>` には、式を含めることができます。  
  
-   `<#+ Class feature control blocks #>` には、メソッド、フィールドおよびプロパティを含めることができます。  
  
## 標準コントロール ブロック  
 標準コントロール ブロックには、ステートメントを含めることができます。  たとえば、次の標準ブロックは、XML ドキュメント内のすべての属性の名前を取得します。  
  
```  
<#@ assembly name="System.Xml.dll" #>  
<#@ import namespace="System.Xml" #>  
  
<#  
    List<string> allAttributes = new List<string>();  
    XmlDocument xDoc = new XmlDocument();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes.Count > 0)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {  
           allAtributes.Add(attr.Name);  
       }  
     }    
#>  
```  
  
 `if` や `for` などの複合ステートメント内に、プレーンテキストを埋め込むことができます。  たとえば、次のフラグメントでは、各ループの反復処理で出力行が生成されます。  
  
```  
<#  
       foreach (XmlAttribute attr in attributes)  
       {  
#>  
Found another one!  
<#  
           allAtributes.Add(attr.Name);  
       }  
#>  
```  
  
> [!WARNING]
>  プレーンテキストが埋め込まれた入れ子になったステートメントは、必ず中かっこ \({...}\) で区切ってください。  次の例は正しく動作しません。  
>   
>  `<# if (ShouldPrint) #> Some text.  -- WRONG`  
>   
>  次のように、中かっこ \({ }\) を含める必要があります。  
  
```  
  
<#  
 if (ShouldPrint)  
 {   //  "{" REQUIRED  
#>  
Some text.  
<#  
 }   
#>  
  
```  
  
## 式コントロール ブロック  
 式コントロール ブロックは、出力ファイルに書き込まれる文字列を提供するコードで使用します。  たとえば、前の例のコード ブロックを次のように変更すると、属性の名前を出力ファイルに出力できます。  
  
```  
<#  
    XmlDocument xDoc = new XmlDocument();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {   
#> <#= attr.Name #> <#  
       }  
    }  
#>  
```  
  
## クラス機能コントロール ブロック  
 クラス機能コントロール ブロックを使用すると、メソッド、プロパティ、フィールド、または入れ子になったクラスをテキスト テンプレートに追加できます。  クラス機能ブロックの最も一般的な用途は、テキスト テンプレートの他の部分のコードにヘルパー関数を提供することです。  たとえば、次のクラス機能ブロックは、属性名の最初の文字を大文字にします \(名前に空白文字が含まれている場合は、各単語の最初の文字を大文字にします\)。  
  
```  
<#@ import namespace="System.Globalization" #>  
```  
  
```  
<#+  
    private string FixAttributeName(string name)  
    {  
        return CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name);  
    }  
#>  
```  
  
> [!NOTE]
>  同じテンプレート ファイル内で、クラス機能コントロール ブロックの後に標準コントロール ブロックを配置することはできません。  ただし、この制限は、`<#@include#>` ディレクティブを使用した結果には適用されません。  各インクルード ファイルでは、標準ブロックの後にクラス機能ブロックを配置できます。  
  
 クラス機能コントロール ブロック内にテキスト ブロックと式ブロックを埋め込むことによって、出力を生成する関数を作成できます。  例:  
  
```  
<#+  
    private void OutputFixedAttributeName(string name)  
    {  
#>  
 Attribute:  <#= CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name) #>  
<#+  // <<< Notice that this is also a class feature block.  
    }  
#>  
```  
  
 標準ブロックまたは別のクラス機能ブロックから、この関数を呼び出すことができます。  
  
```  
<# foreach (Attribute attribute in item.Attributes)  
{  
  OutputFixedAttributeName(attribute.Name);  
}  
#>  
```  
  
## コントロール ブロックの使用方法  
 1 つのテンプレート内の標準コントロール ブロックと式コントロール ブロックのコード \(インクルードされたテンプレート内のコードも含む\) はすべて結合され、生成されるコードの `TransformText()` メソッドを形成します   \(`include` ディレクティブを使用して他のテキスト テンプレートをインクルードする方法の詳細については、「[T4 テキスト テンプレートのディレクティブ](../modeling/t4-text-template-directives.md)」を参照してください\)。  
  
 コントロール ブロックの使用時には、次の考慮事項に留意してください。  
  
-   **言語。** テキスト テンプレートでは、C\# または Visual Basic のコードを使用できます。  既定の言語は C\# ですが、`template` ディレクティブの `language` パラメーターで Visual Basic を指定できます。  \(`template` ディレクティブの詳細については、「[T4 テキスト テンプレートのディレクティブ](../modeling/t4-text-template-directives.md)」を参照してください\)。  
  
     コントロール ブロックで使用する言語は、テキスト テンプレートで生成するテキストの言語または書式とは無関係です。  Visual Basic コードを使用して C\# を生成することも、C\# コードを使用して Visual Basic を生成することもできます。  
  
     `include` ディレクティブでインクルードするすべてのテキスト テンプレートを含め、特定のテキスト テンプレートで使用できる言語は 1 つだけです。  
  
-   **ローカル変数。** テキスト テンプレート内の標準コントロール ブロックと式コントロール ブロックのコードはすべて結合され、単一のメソッドとして生成されるため、各ローカル変数の名前が競合しないように注意してください。  他のテキスト テンプレートをインクルードする場合は、インクルードされるすべてのテンプレート間で変数名を一意にする必要があります。  これを実現する 1 つの方法は、各ローカル変数名に、その変数が宣言されたテキスト テンプレートを識別する文字列を追加することです。  
  
     特に複数のテキスト テンプレートをインクルードする場合は、ローカル変数を宣言するときに、そのローカル変数を妥当な値に初期化するのも良い方法です。  
  
-   **コントロール ブロックの入れ子。** コントロール ブロックどうしを入れ子にすることはできません。  次のコントロール ブロックを開始する前に、前のコントロール ブロックを必ず終了する必要があります。  たとえば、式ブロック内のテキストを標準コントロール ブロックの一部として出力する方法を次に示します。  
  
    ```  
    <#   
    int x = 10;  
    while (x-- > 0)  
    {  
    #>  
    <#= x #>  
    <# } #>  
    ```  
  
-   **リファクタリング。** テキスト テンプレートを簡潔で理解しやすい状態に保つために、コードの繰り返しを避けることを強くお勧めします。そのためには、再利用できるコードをクラス機能ブロックのヘルパー関数にファクタリングするか、Microsoft.VisualStudio.TextTemplating.TextTransformation クラスを継承する独自のテキスト テンプレート クラスを作成します。