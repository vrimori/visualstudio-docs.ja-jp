---
title: '方法: エスケープ シーケンスを使用して、テンプレートからテンプレートを生成 |Microsoft ドキュメント'
ms.custom: ''
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
ms.openlocfilehash: 160234b8db7f09d25b22e33fb5bc722e06187ba9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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