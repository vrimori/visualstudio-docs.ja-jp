---
title: "&lt;formRegion&gt; 要素 (Visual Studio での Office 開発) | Microsoft Docs"
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
  - "アプリケーション マニフェスト [Visual Studio での Office 開発]、<formRegion> 要素"
ms.assetid: d397cf31-c0ef-47f0-860a-cd816e4bf6eb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# &lt;formRegion&gt; 要素 (Visual Studio での Office 開発)
  `vstov4`  名前空間の `formRegion` 要素は、VSTO アドインに関連付けられている Microsoft Office Outlook フォーム領域を識別します。  
  
## 構文  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## 要素と属性  
 `vstov4`  名前空間の `formRegion` 要素は、Outlook VSTO アドインに関連付けられているフォーム領域を識別します。 この要素は、フォーム領域のある Outlook VSTO アドインでのみ必要です。  
  
 1 つの VSTO アドインに対して、`formRegions` 要素内で複数の `formRegion` 要素を定義できます。  
  
 `formRegion` 要素には、次の属性があります。  
  
|属性|説明|  
|--------|--------|  
|`name`|必須です。 フォーム領域の名前を識別します。|  
  
 `formRegion` 要素には、次の子要素があります。  
  
### messageClass  
 `messageClass`  要素は、フォーム領域に関連付けられる Outlook フォームを指定します。  
  
 `messageClass` 要素には、次の属性があります。  
  
|属性|説明|  
|--------|--------|  
|`name`|必須です。 フォーム領域に関連付けられるフォームを識別します。|  
  
## 使用例  
 次のコード例は、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] を使用して配置される Outlook VSTO アド インのアプリケーション マニフェスト内の `formRegion` 要素を示しています。 ここでは、1 つのフォーム領域に 3 つのメッセージ クラスが関連付けられています。 このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
```  
<vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion>  
```  
  
## 参照  
 [Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)   
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)  
  
  