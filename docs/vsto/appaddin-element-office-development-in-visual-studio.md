---
title: "&lt;appAddin&gt; 要素 (Visual Studio での Office 開発) | Microsoft Docs"
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
  - "アプリケーション マニフェスト [Visual Studio での Office 開発]、<appAddin> 要素"
ms.assetid: 6152fe5b-6af1-465d-aee7-19e4fd4d04c1
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# &lt;appAddin&gt; 要素 (Visual Studio での Office 開発)
  `vstov4`  名前空間の `appAddin` 要素には、VSTO アドイン用のカスタマイズ固有の情報が格納されます。  
  
## 構文  
  
```  
<appAddin  
  application  
  loadBehavior  
  keyName>  
  <friendlyName>  
  <description>  
  <formRegions></formRegions>  
</appAddin>  
```  
  
## 要素と属性  
 `appAddin` 要素は必須です。この要素は `vstov4`  名前空間にあります。 アプリケーション マニフェストで定義された `appAddin` 要素が 1 つだけあります。  
  
 `appAddin` 要素には、次のような属性があります。  
  
|属性|説明|  
|--------|--------|  
|`application`|必須です。 Microsoft Office アプリケーションを指定します。 この値は、Excel、InfoPath、Outlook、PowerPoint、Project、Visio、Word のいずれか 1 つになります。|  
|`loadBehavior`|省略可能です。 既定では、この値が 3 に設定され、`loadBehavior` が有効になっています。 デバッグする場合は、この値を 2 に設定して VSTO アドインを無効にできます。 詳細については、「[VSTO アドインのレジストリ エントリ](../vsto/registry-entries-for-vsto-add-ins.md)」の表「LoadBehavior の値」を参照してください。|  
|`keyName`|必須です。 この値は、アプリケーションが VSTO アドインを読み込むのに使用するレジストリ キーの名前です。 詳細については、「[VSTO アドインのレジストリ エントリ](../vsto/registry-entries-for-vsto-add-ins.md)」を参照してください。|  
  
 `appAddin` 要素には、次の子要素があります。  
  
### friendlyName  
 省略可能です。`friendlyName` 要素については、「[&#60;friendlyName&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)」を参照してください。  
  
### 説明  
 省略可能です。`description` 要素については、「[&#60;description&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/description-element-office-development-in-visual-studio.md)」を参照してください。  
  
### formRegions  
 フォーム領域を含んでいる Outlook VSTO アドインでのみ必須です。`formRegions` 要素については、「[&#60;formRegions&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)」を参照してください。  
  
## VSTO アドインの例  
  
### 説明  
 次のコード例は、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] を使用して配置される Outlook ソリューションの `appAddin` 要素を示しています。 このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### コード  
  
```  
<vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn>  
```  
  
## 参照  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)  
  
  