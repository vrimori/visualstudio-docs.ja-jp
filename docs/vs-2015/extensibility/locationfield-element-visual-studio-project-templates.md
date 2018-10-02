---
title: LocationField 要素 (Visual Studio プロジェクト テンプレート) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea66808097c0e62d6c36781d7f288ed06975f6e1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544346"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>LocationField 要素 (Visual Studio プロジェクト テンプレート)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[LocationField 要素 (Visual Studio プロジェクト テンプレート)](https://docs.microsoft.com/visualstudio/extensibility/locationfield-element-visual-studio-project-templates)します。  
  
指定するかどうか、**場所**テキスト ボックスに、**新しいプロジェクト** ダイアログ ボックスが有効になっている、無効になっている、またはプロジェクトのテンプレートの非表示になります。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<LocationField >  
  
## <a name="syntax"></a>構文  
  
```  
<LocationField> Enabled/Disabled/Hidden </LocationField>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
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
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] テンプレートのメタデータの例を次に示します。  
  
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

