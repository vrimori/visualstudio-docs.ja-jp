---
title: '方法: エスケープ シーケンスを使用してテンプレートからテンプレートを生成します |。Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, generating templates from templates
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7cc523aed43dfbe3339c3f3cc054c09b39a4f060
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546272"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>方法: エスケープ シーケンスを使用してテンプレートからテンプレートを生成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: テンプレートを使用してエスケープ シーケンスから生成テンプレート](https://docs.microsoft.com/visualstudio/modeling/how-to-generate-templates-from-templates-by-using-escape-sequences)します。  
  
生成されたテキスト出力として別のテキスト テンプレートを作成するテキスト テンプレートを作成することができます。 これを行うには、エスケープ シーケンスを使用して、テキスト テンプレートのタグを区切る必要があります。 エスケープ シーケンスを使用しない場合、生成されたテキスト テンプレートが定義済みの意味になります。 テキスト テンプレートでエスケープ シーケンスの使用に関する詳細については、次を参照してください。[テキスト テンプレートでのエスケープ シーケンスを使用して](../modeling/using-escape-sequences-in-text-templates.md)します。  
  
### <a name="to-generate-a-text-template-from-within-a-text-template"></a>テキスト テンプレート内のテキスト テンプレートを生成するには  
  
-   バック スラッシュを使用 (\\) ディレクティブ、ステートメント、式、テキスト テンプレート内で必要なマークアップ タグを作成し、別のテキスト テンプレート ファイルの機能をクラスにエスケープ文字として。  
  
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



