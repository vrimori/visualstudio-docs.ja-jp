---
title: "VSTemplate 要素 (Visual Studio テンプレート) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords: VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4a191c94731560cbc36b4738d16ef202f051873
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate 要素 (Visual Studio テンプレート)
プロジェクト テンプレート、項目テンプレート、またはスタート キットに関するすべてのメタデータが含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
<VSTemplate Type="TemplateType" Version="x.x.x">  
    <TemplateData>    </TemplateData>  
    <TemplateContent>    </TemplateContent>  
    ...  
</VSTemplate>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`Type`|プロジェクト テンプレートと項目テンプレートのテンプレートを識別します。 この属性の値をとります。`Project`または`Item`です。|  
|`Version`|テンプレートのバージョン番号を指定します。 テンプレートで[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]と[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]が、`Version`属性の値の`3.0.0`します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必須の要素です。<br /><br /> テンプレートを分類しでの表示方法を定義するデータを指定します、**新しいプロジェクト**または**新しい項目の追加** ダイアログ ボックス。|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必須の要素です。<br /><br /> テンプレートの内容を指定します。|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|省略可能な要素です。|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|省略可能な要素です。|  
  
### <a name="parent-elements"></a>親要素  
 なし。  
  
## <a name="remarks"></a>コメント  
 `VSTemplate`要素は、.vstemplate ファイルのルート要素です。  
  
## <a name="example"></a>例  
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] アプリケーションでのプロジェクト テンプレートのメタデータの例を次に示します。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs</ProjectItem>  
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