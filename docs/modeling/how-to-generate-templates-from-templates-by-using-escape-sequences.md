---
title: '方法: エスケープ シーケンスを使用してテンプレートからテンプレートを生成する'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: d7c53657faa23b57e3aef45ff8c404f2d326e489
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>方法: エスケープ シーケンスを使用してテンプレートからテンプレートを生成する
生成されたテキスト出力として別のテキスト テンプレートを作成するテキスト テンプレートを作成することができます。 これを行うには、テキスト テンプレートのタグを区切るためにエスケープ シーケンスを使用する必要があります。 エスケープ シーケンスを使用しない場合、生成されたテキスト テンプレートは定義済みの意味を持ちます。 テキスト テンプレートでエスケープ シーケンスの使用の詳細については、次を参照してください。[テキスト テンプレートでエスケープ シーケンスを使用して](../modeling/using-escape-sequences-in-text-templates.md)です。

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>テキスト テンプレート内のテキスト テンプレートを生成するには

-   バック スラッシュを使用して (\\) ディレクティブ、ステートメント、式、テキスト テンプレート内で必要なマークアップ タグを作成し、別のテキスト テンプレート ファイル内の機能のクラスにエスケープ文字として。

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>例
 次の例では、エスケープ文字を使用して、テキスト テンプレートからのテキスト テンプレートを生成します。 `output`ディレクティブは、テキスト テンプレート ファイルの種類 (.tt) に変換先ファイルの種類を設定します。

```csharp
\<#@ output extension=".tt" \#>
\<#@ assembly name="System.Xml.dll" \#>
\<#@ import namespace="System.Xml" \#>
\<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {\#>
           \<#= attr.Name \#>
       \<#}
     }
\#>
```

 生成されたテキスト出力は、テキスト テンプレートです。

```
<#@ output extension=".tt" #>
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {#>
           <#= attr.Name #>
       <#}
     }
#>
```