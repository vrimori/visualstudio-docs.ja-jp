---
title: "&lt;application&gt; 要素 (Visual Studio での Office 開発)"
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
  - "アプリケーション マニフェスト [Visual Studio での Office 開発]、<application> 要素"
ms.assetid: b8d3db7c-9127-4812-b18f-bb17e1f8788f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# &lt;application&gt; 要素 (Visual Studio での Office 開発)
  `vstav3` 名前空間の `application` 要素は、Office ソリューションの説明をラップします。 ドキュメント レベルのカスタマイズと VSTO アドインでは、子要素が異なります。  
  
## ドキュメント レベルのカスタマイズの構文  
  
```  
<application> <customization id <document solutionId /> </customization> </application>  
```  
  
## アプリケーション レベルのアドインの構文  
  
```  
<application> <customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization> </application>  
```  
  
## 要素と属性  
 `vstav3` 名前空間の `application` 要素は、`vstov4` 名前空間に格納されている、カスタマイズに固有のすべての情報をラップするノードです。  
  
 `application` 要素には属性がありません。  
  
 `application` 要素には、次のような要素があります。  
  
### カスタマイズ  
 `vstov3` 名前空間の `customization` 要素の役割は [&#60;customization&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/customization-element-office-development-in-visual-studio.md) で定義されます。  
  
## ドキュメント レベルのカスタマイズの例  
  
### 説明  
 次のコード例は [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] を使用して配置されるドキュメント レベルの Office ソリューションの `application` 要素を示しています。 このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」にある例から一部を抜粋したものです。  
  
### コード  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## VSTO アドインの例  
  
### 説明  
 次のコード例は [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] を使用して配置されるアプリケーション レベルの Office ソリューションの `application` 要素を示しています。 このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」にある例から一部を抜粋したものです。  
  
### コード  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## 参照  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)  
  
  