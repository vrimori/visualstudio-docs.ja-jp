---
title: "&lt;customizations&gt; 要素 (Visual Studio での Office 開発)"
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
  - "<customizations> 要素"
  - "customizations 要素"
  - "アプリケーション マニフェスト [Visual Studio での Office 開発]、<customizations> 要素"
ms.assetid: fe1133ef-5fdf-4945-a67b-55a66a4e2109
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# &lt;customizations&gt; 要素 (Visual Studio での Office 開発)
  `vstov4` 名前空間の `customizations` 要素には、各 Office ソリューションのインストールおよび読み込みに関するすべての情報が含まれています。  
  
## ドキュメント レベルのカスタマイズの構文  
  
```  
<customizations> <customization id <document solutionId /> </customization> </customizations>  
```  
  
## VSTO アドインの構文  
  
```  
<customizations> <customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization> </customizations>  
```  
  
## 要素と属性  
 `customizations` 要素には、各 Office ソリューションに関する特定の情報が含まれています。 この要素は、名前空間 `vstov4=urn:schemas-microsoft-com:vsto.v4` に属している必要があります。 アセンブリの子要素もこの名前空間に属している必要があります。  
  
 `customizations` 要素に属性はありません。  
  
 `customizations` 要素には、次の子要素があります。  
  
### カスタマイズ  
 必須です。`vstov4` 名前空間の `customization` 要素は [&#60;customization&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/customization-element-office-development-in-visual-studio.md) で定義されます。  
  
## ドキュメント レベルのカスタマイズの例  
  
### 説明  
 次のコード例は、ドキュメント レベルのカスタマイズの `customizations` 要素を示しています。  
  
> [!NOTE]  
>  このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### コード  
  
```  
<vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations>  
```  
  
## VSTO アドインの例  
  
### 説明  
 次のコード例では、VSTO アドインの `customizations` 要素を示しています。 この例は、フォーム領域が含まれた Outlook VSTO アドインです。 このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### コード  
  
```  
<vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations>  
```  
  
## 参照  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)  
  
  