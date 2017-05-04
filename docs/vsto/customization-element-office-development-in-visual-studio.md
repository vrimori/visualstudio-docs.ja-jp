---
title: "&lt;customization&gt; 要素 (Visual Studio での Office 開発) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "アプリケーション マニフェスト [Visual Studio での Office 開発]、<customization> 要素"
ms.assetid: a3bf7f35-bd98-4530-9226-46489cd37bb1
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;customization&gt; 要素 (Visual Studio での Office 開発)
  `vstov4` 名前空間の `customization` 要素では、特定の Office ソリューションについて記述します。 ドキュメント レベルのカスタマイズと VSTO アドインでは、子要素が異なります。  
  
## ドキュメント レベルのカスタマイズの構文  
  
```  
<customization id <document solutionId /> </customization>  
```  
  
## VSTO アドインの構文  
  
```  
<customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization>  
```  
  
## 要素と属性  
 `customization` 要素には、カスタマイズ固有の情報が含まれています。 この要素は、名前空間 `vstov4=urn:schemas-microsoft-com:vsto.v4` に存在する必要があります。 Office ソリューションごとに、`customization` 要素が 1 つあります。 たとえば、複数プロジェクトの配置で 3 つの Office ソリューションを配置する場合は、アプリケーション マニフェストに 3 つの `customization` 要素を定義します。  
  
 アセンブリの子要素が、この名前空間に存在する必要もあります。  
  
 `customization` 要素には、次の属性があります。  
  
|属性|説明|  
|--------|--------|  
|`id`|複数プロジェクトの配置の場合は必須です。`id` 要素によって、Office ソリューションを一意に識別します。|  
  
### ドキュメント レベルのカスタマイズ  
 `customization` 要素には、次の子要素があります。  
  
#### ドキュメント  
 `vstov4` 名前空間の `document` 要素は [&#60;document&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/document-element-office-development-in-visual-studio.md) で定義されます。  
  
### VSTO アドイン  
 `customization` 要素には、次の子要素があります。  
  
#### appAddin  
 `vstov4` 名前空間の `appAddin` 要素は [&#60;appAddin&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md) で定義されます。  
  
## ドキュメント レベルのカスタマイズの例  
  
### 説明  
 次のコード例は、ドキュメント レベルのカスタマイズの `customization` 要素を示しています。 このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### コード  
  
```  
<vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization>  
```  
  
## VSTO アドインの例  
  
### 説明  
 次のコード例は、VSTO アドインの `customization` 要素を示しています。 これは、フォーム領域が含まれた Outlook VSTO アドインです。 このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### コード  
  
```  
<vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization>  
```  
  
## 参照  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)  
  
  