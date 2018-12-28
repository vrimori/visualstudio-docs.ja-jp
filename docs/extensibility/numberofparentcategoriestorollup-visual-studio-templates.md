---
title: NumberOfParentCategoriesToRollUp 要素 (Visual Studio テンプレート)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 36c3f8ef1e8016fd1ab46cb61f5e076afdd4190a
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2018
ms.locfileid: "53562283"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>NumberOfParentCategoriesToRollUp 要素 (Visual Studio テンプレート)
親カテゴリ内のテンプレートを表示する数を指定します、**新しいプロジェクト** ダイアログ ボックス。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<NumberOfParentCategoriesToRollUp >  
  
## <a name="syntax"></a>構文  
  
```xml
<NumberOfParentCategoriesToRollUp>  
1  
</NumberOfParentCategoriesToRollUp>  
```
  
## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|テンプレートをカテゴリに分類し、 **[新しいプロジェクト]** ダイアログ ボックス、または **[新しい項目の追加]** ダイアログ ボックスでどのように表示させるかを定義します。|  
  
## <a name="text-value"></a>テキスト値  
 `integer`値が必要です。  
  
 この値は、親カテゴリ内のテンプレートを表示する数を指定します、**新しいプロジェクト** ダイアログ ボックス。  
  
## <a name="remarks"></a>Remarks  
 `NumberOfParentCategoriesToRollUp` は、省略可能な要素です。  
  
## <a name="example"></a>例  
 この例でのメタデータを[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]Windows アプリケーション。 このメタデータを含むテンプレートには最上位レベルの下 2 つのフォルダーが配置されている場合[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]ノードの最上位レベルのノードで、テンプレートが表示されます、**新しいプロジェクト** ダイアログ ボックス。 場合、`NumberOfParentCategoriesToRollUp`テンプレートのみが表示されます ノードでそのが物理的に配置されているが設定されています。
  
```xml
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)