---
title: エスケープ シーケンスを使用してテンプレートからテンプレートを生成する方法
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 13ca6a9aef2f0944ba1f42c849d9f8079a56a82b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947483"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>エスケープ シーケンスを使用してテンプレートからテンプレートを生成する方法
別のテキスト テンプレートを作成するテキスト出力として生成されたテキスト テンプレートを作成することができます。 これを行うには、テキスト テンプレートのタグを区切るためにエスケープ シーケンスを使用する必要があります。 エスケープ シーケンスを使用しない場合、生成されたテキスト テンプレートは定義済みの意味を持ちます。 テキスト テンプレートでのエスケープ シーケンスの使用の詳細については、次を参照してください。[テキスト テンプレートでのエスケープ シーケンスの使用](../modeling/using-escape-sequences-in-text-templates.md)

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>テキスト テンプレート内でテキスト テンプレートを生成するには

-   別のテキスト テンプレート ファイル内で、ディレクティブ、ステートメント、式、クラス機能といった必要なマークアップ タグをテキスト テンプレート内で作成するためにエスケープ文字として、バックスラッシュ (\\) を使用します。

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>例
 次の例では、エスケープ文字を使用して、テキスト テンプレートからテキスト テンプレートを生成します。 `output` ディレクティブは、変換先ファイルのテキスト テンプレート ファイルの種類 (.tt) を設定します。

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
