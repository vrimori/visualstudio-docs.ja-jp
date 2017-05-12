---
title: "&lt;formRegions&gt; 要素 (Visual Studio での Office 開発)"
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
  - "formRegions 要素"
  - "<formRegions> 要素"
  - "アプリケーション マニフェスト [Visual Studio での Office 開発]、<formRegions> 要素"
ms.assetid: 71faa2da-9d38-43e8-9d7d-0bcd944ef9a3
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;formRegions&gt; 要素 (Visual Studio での Office 開発)
  `vstov4`  名前空間の `formRegions` 要素には、VSTO アドインに関連付けられている Microsoft Office Outlook フォーム領域が含まれています。  
  
## 構文  
  
```  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## 要素と属性  
 `vstov4`  名前空間の`formRegions` 要素には、Outlook VSTO アドインの `formRegion` 要素がすべて含まれています。 それは、フォーム領域のある Outlook VSTO アドインにのみ必要です。  
  
 アプリケーション マニフェストで定義できる `formRegions` 要素は 1 つだけです。  
  
 `formRegions` 要素に属性はありません。  
  
 `formRegions` 要素には次の要素があります。  
  
### formRegion  
 フォーム領域のある Outlook VSTO アドインに必要です。`formRegion` 要素は [&#60;formRegion&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/formregion-element-office-development-in-visual-studio.md) で定義されます。  
  
## VSTO アドインの例  
  
### 説明  
 次のコード例は、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] を使用して展開したアプリケーション レベルの Office ソリューションに対するアプリケーション マニフェストの `formRegions` 要素を示しています。 このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### コード  
  
```  
<vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions>  
```  
  
## 参照  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)  
  
  