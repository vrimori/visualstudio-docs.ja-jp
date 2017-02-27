---
title: "方法: エスケープ シーケンスを使用してテンプレートからテンプレートを生成する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "テキスト テンプレート, 生成 (テンプレートからテンプレートを)"
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 35
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 35
---
# 方法: エスケープ シーケンスを使用してテンプレートからテンプレートを生成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

生成されるテキスト出力として別のテキスト テンプレートを作成するテキスト テンプレートを作成できます。  そのためには、エスケープ シーケンスを使用してテキスト テンプレート タグを記述する必要があります。  エスケープ シーケンスを使用しないと、生成されたテキスト テンプレートは、定義済みの意味を持つことになります。  テキスト テンプレートにおけるエスケープ シーケンスの使用の詳細については、「[テキスト テンプレートでのエスケープ シーケンスの使用](../modeling/using-escape-sequences-in-text-templates.md)」を参照してください。  
  
### テキスト テンプレート内からテキスト テンプレートを生成するには  
  
-   テキスト テンプレート内で、別のテキスト テンプレート ファイルのディレクティブ、ステートメント、式、およびクラス機能に必要なマークアップ タグを生成するには、エスケープ文字として円記号 \(\\\) を使用します。  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## 使用例  
 次の例では、エスケープ文字を使用して、テキスト テンプレートからテキスト テンプレートを生成します。  `output` ディレクティブによって、生成されるファイルの種類をテキスト テンプレートのファイル形式 \(.tt\) に設定します。  
  
```c#  
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
  
 生成されるテキスト出力はテキスト テンプレートです。  
  
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