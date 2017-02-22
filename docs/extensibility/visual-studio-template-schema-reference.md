---
title: "Visual Studio テンプレート スキーマ参照 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".vstemplate ファイル"
  - "Visual Studio のテンプレート, スキーマ"
  - "VSTEMPLATE ファイル"
ms.assetid: 6f74a2d5-3811-43d6-8b10-eb5823ad8995
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# Visual Studio テンプレート スキーマ参照
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このセクションでは、.vstemplate ファイル内の XML 要素について説明します。.vstemplate ファイルとは、プロジェクト テンプレート、項目テンプレート、およびスタート キットのメタデータを格納するファイルのことです。  
  
 カスタムの .vstemplate ファイルを検証するには、vstemplate.xsd を使用します。  このファイルは、..\\*Visual Studio installation folder*\\Xml\\Schemas\\1033\\vstemplate.xsd に含まれています。  
  
|要素|子要素|属性|  
|--------|---------|--------|  
|[AppliesTo](../extensibility/appliesto-element-visual-studio-templates.md)|なし|なし|  
|[Assembly \(テンプレート\)](../extensibility/assembly-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Assembly \(ウィザード拡張\)](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|\-\-|\-\-|  
|[BuildProjectOnload](../extensibility/buildprojectonload-element-visual-studio-templates.md)|\-\-|\-\-|  
|[CreateInPlace](../extensibility/createinplace-visual-studio-templates.md)|\-\-|\-\-|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|\-\-|\-\-|  
|[CustomDataSignature](../extensibility/customdatasignature-element-visual-studio-templates.md)|\-\-|\-\-|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|\-\-|Name<br /><br /> Value|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|CustomParameter|\-\-|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Description](../extensibility/description-element-visual-studio-templates.md)|\-\-|Package<br /><br /> ID|  
|[EnableEditOfLocationField](../extensibility/enableeditoflocationfield-element-visual-studio-templates.md)|\-\-|\-\-|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Folder](../extensibility/folder-element-visual-studio-project-templates.md)|ProjectItem<br /><br /> Folder|Name|  
||\[deprecated\]|\-\-|  
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|\-\-|\-\-|  
|[Hidden](../extensibility/hidden-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Icon](../extensibility/icon-element-visual-studio-templates.md)|\-\-|Package<br /><br /> ID|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|\-\-|\-\-|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|\-\-|\-\-|  
|[MaxFrameworkVersion](../extensibility/maxframeworkversion-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Name](../extensibility/name-element-visual-studio-templates.md)|\-\-|Package<br /><br /> ID|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|\-\-|\-\-|  
|[PreviewImage](../extensibility/previewimage-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Folder<br /><br /> ProjectItem|File<br /><br /> TargetFileName<br /><br /> ReplaceParameters|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|\-\-|  
|[ProjectItem \(項目テンプレート\)](../extensibility/projectitem-element-visual-studio-item-templates.md)|\-\-|SubType<br /><br /> CustomTool<br /><br /> ItemType<br /><br /> ReplaceParameters<br /><br /> TargetFileName|  
|[ProjectItem \(プロジェクト テンプレート\)](../extensibility/projectitem-element-visual-studio-project-templates.md)|\-\-|TargetFileName<br /><br /> ReplaceParameters<br /><br /> OpenInEditor<br /><br /> OpenOrder<br /><br /> OpenInWebBrowser<br /><br /> OpenInHelpBrowser|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|\-\-|\-\-|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|\-\-|ProjectName|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|\-\-|\-\-|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|\-\-|\-\-|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Reference](../extensibility/reference-element-visual-studio-templates.md)|Assembly|\-\-|  
|[References](../extensibility/references-element-visual-studio-templates.md)|Reference|\-\-|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|\-\-|\-\-|  
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|\-\-|Version|  
|[SDKReference](72c8b352-0b7a-42b3-ba5d-2a2d1e90c3)|\-\-|Package|  
|[ShowByDefault](../extensibility/showbydefault-visual-studio-templates.md)|\-\-|\-\-|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|Name|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|\-\-|\-\-|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|\-\-|\-\-|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|\-\-|\-\-|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|\-\-|\-\-|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|RequiredPlatformVersion|\-\-|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|ProjectCollection<br /><br /> プロジェクト<br /><br /> 参考文献<br /><br /> ProjectItem<br /><br /> CustomParameters|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|名前<br /><br /> 説明<br /><br /> Icon<br /><br /> PreviewImage<br /><br /> ProjectType<br /><br /> ProjectSubType<br /><br /> TemplateID<br /><br /> TemplateGroupID<br /><br /> SortOrder<br /><br /> CreateNewFolder<br /><br /> DefaultName<br /><br /> ProvideDefaultName<br /><br /> PromptForSaveOnCreation<br /><br /> EnableLocationBrowseButton<br /><br /> EnableEditOfLocationField<br /><br /> Hidden<br /><br /> DisplayInParentCategories<br /><br /> LocationFieldMRUPrefix<br /><br /> NumberOfParentCategoriesToRollUp<br /><br /> CreateInPlace<br /><br /> BuildOnLoad<br /><br /> BuildProjectOnload<br /><br /> ShowByDefault<br /><br /> LocationField<br /><br /> SupportsMasterPage<br /><br /> SupportsCodeSeparation<br /><br /> SupportsLanguageDropDown<br /><br /> RequiredFrameworkVersion<br /><br /> FrameworkVersion<br /><br /> MaxFrameworkVersion<br /><br /> CustomDataSignature<br /><br /> TargetPlatformName|\-\-|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|\-\-|\-\-|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|\-\-|\-\-|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|TemplateData<br /><br /> TemplateContent<br /><br /> WizardExtension<br /><br /> WizardData|Type<br /><br /> Version|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|\-\-|Name|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Assembly<br /><br /> FullClassName|\-\-|  
  
## 参照  
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [方法 : スタート キットを作成する](../ide/how-to-create-starter-kits.md)