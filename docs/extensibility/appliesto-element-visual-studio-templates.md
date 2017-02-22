---
title: "AppliesTo 要素 (Visual Studio テンプレート) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# AppliesTo 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

省略可能な式を 1 つ以上の機能と一致するように指定します   \(「<xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>」を参照してください\)。  機能は、<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5> プロパティとして、階層を介してプロジェクトの種類によって公開されます。  このようにすると、共通の適用可能な機能を持つ複数のプロジェクトの種類によってテンプレートを共有できます。  
  
 この要素は省略可能です。  テンプレート ファイルには、最大で 1 つのインスタンスがあります。  この要素は、現在選択されているアクティブなプロジェクトの機能に基づいて、項目テンプレートを適用可能として利用できるようにするだけです。  項目テンプレートを適用不可にするためには使用できません。  `AppliesTo` が存在しない場合、または式を正常に利用できない場合は、製品の以前のバージョンの場合と同様に、テンプレートを適用可能にするために `TemplateID` または `TemplateGroupID` が使用されます。  
  
 Visual Studio 2013 更新プログラム 2 で導入されました。  正確なバージョンについては、「[Referencing Assemblies Delivered in the Visual Studio 2013 SDK Update 2](http://msdn.microsoft.com/ja-jp/42b65c3e-e42b-4c39-98c8-bea285f25ffb)」を参照してください。  
  
## 構文  
  
```  
<AppliesTo>Capability1</AppliesTo>    
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|テンプレートをカテゴリに分類します。|  
  
## テキスト値  
 テキスト値が必要です。  このテキストでプロジェクトの機能を指定します。  
  
 有効な式の構文は次のように定義されます。  
  
-   "\(VisualC &#124; CSharp\) \+ \(MSTest &#124; NUnit\)" などの機能の式。  
  
-   "&#124;" は OR 演算子です。  
  
-   "&" および "\+" 文字は、どちらも AND 演算子です。  
  
-   "\!" 文字は NOT 演算子です。  
  
-   かっこで囲むことで、評価の優先順位が強制的に設定されます。  
  
-   Null または空の式は、一致として評価されます。  
  
-   プロジェクトの機能には、予約文字「"'\`:;,\+\-\*\/\\\!~&#124;&%$@^\(\)\={}\[\]\<\>?」を除く文字を使用できます。  を除く文字を使用できます。  
  
## 使用例  
 次の例に、3 種類のテンプレートを示します。  `Template1` は、C\# のすべてのプロジェクトの種類、または `WindowsAppContainer` 機能をサポートする他のプロジェクトの種類に適用されます。  `Template2` は、すべての種類の C\# プロジェクトに適用されます。  `Template3` は、`WindowsAppContainer` プロジェクトではない C\# プロジェクトに適用されます。  
  
```xml  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 2 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
```  
  
## 参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)