---
title: LocationField 要素 (Visual Studio プロジェクト テンプレート) |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1bbdff5e2dcee4611b5a46cc74f0255f94d30744
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868503"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>LocationField 要素 (Visual Studio プロジェクト テンプレート)
指定するかどうか、**場所**テキスト ボックスに、**新しいプロジェクト** ダイアログ ボックスが有効になっている、無効になっている、またはプロジェクトのテンプレートの非表示になります。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<LocationField >  
  
## <a name="syntax"></a>構文  
  
```  
<LocationField> Enabled/Disabled/Hidden </LocationField>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必須の要素です。<br /><br /> テンプレートを分類し、いずれかでどのように表示を定義、**新しいプロジェクト**します。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値が必要です。  
  
 有効なテキスト値は次のとおりです。  
  
-   `Enabled`、いることを指定します、**場所**のボックス、**新しいプロジェクト** ダイアログ ボックスが有効にします。  
  
-   `Disabled`、いることを指定します、**場所**のボックス、**新しいプロジェクト** ダイアログ ボックスが無効になります。  
  
-   `Hidden`、いることを指定します、**場所**のボックス、**新しいプロジェクト** ダイアログ ボックスは表示されません。  
  
## <a name="remarks"></a>Remarks  
 既定値は `Enabled` です。  
  
 **場所**テキスト ボックスに、**新しいプロジェクト**ダイアログ ボックスでユーザーを新しいプロジェクトを保存する既定のディレクトリを変更します。  
  
 指定された値、`Location`基になるプロジェクト システムがサポートされている場合に、要素は、ダイアログ ボックスで受け入れられますのみです。  
  
## <a name="example"></a>例  
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] テンプレートのメタデータの例を次に示します。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <LocationField>Disabled</LocationField>  
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
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)