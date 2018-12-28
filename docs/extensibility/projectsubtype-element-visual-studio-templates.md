---
title: ProjectSubType 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 046893f3bb3fb6dc0b4461e2d9cadcb2a95ba7bc
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561708"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType 要素 (Visual Studio テンプレート)
テンプレートで指定された値のサブカテゴリには、分類、`ProjectType`要素。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProjectSubType >  
  
## <a name="syntax"></a>構文  
  
```xml  
<ProjectSubType> SubType </ProjectSubType>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必須の要素です。<br /><br /> テンプレートをカテゴリに分類し、 **[新しいプロジェクト]** ダイアログ ボックス、または **[新しい項目の追加]** ダイアログ ボックスでどのように表示させるかを定義します。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値が必要です。  
  
 この値は、テンプレートのサブカテゴリを指定します。  
  
## <a name="remarks"></a>Remarks  
 `ProjectSubType` は、`TemplateData` の子要素で、省略可能な要素です。  
  
 `ProjectSubType`要素は、サブカテゴリを[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)要素。 この値を含めることができます。  
  
- `SmartDevice-NETCFv1`:指定するテンプレートの対象と、[!INCLUDE[Compact](../extensibility/includes/compact_md.md)]バージョン 1.0。  
  
- `SmartDevice-NETCFv2`:指定するテンプレートの対象と、[!INCLUDE[Compact](../extensibility/includes/compact_md.md)]バージョン 2.0。  
  
  テンプレートが含まれている場合、`ProjectType`要素の値を持つ`Web`、`ProjectSubType`要素がテンプレートのプログラミング言語を指定します。 この要素は、次の値を持つことができます。  
  
- `CSharp`:テンプレートを作成するを指定します、 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Web プロジェクトまたは項目。  
  
- `VisualBasic`:テンプレートを作成するを指定します、 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Web プロジェクトまたは項目。  
  
## <a name="example"></a>例  
 次の例のためのプロジェクト テンプレート メタデータを[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]デバイス アプリケーションを対象とする、[!INCLUDE[Compact](../extensibility/includes/compact_md.md)]バージョン 2.0。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
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
 [プロジェクトと項目テンプレートを作成します。](../ide/creating-project-and-item-templates.md)   
 [ProjectType 要素 (Visual Studio テンプレート)](../extensibility/projecttype-element-visual-studio-templates.md)