---
title: "&lt;description&gt; 要素 (Visual Studio での Office 開発) | Microsoft Docs"
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
  - "description 要素"
  - "<description> 要素"
  - "アプリケーション マニフェスト [Visual Studio での Office 開発]、<description> 要素"
ms.assetid: 27c90f8c-393d-4557-9371-2e4e3c4a2d95
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# &lt;description&gt; 要素 (Visual Studio での Office 開発)
  `vstov4`  名前空間の `description` 要素は、Microsoft Office アプリケーションの \[COM アドイン\] ダイアログ ボックスに表示される Office ソリューションの説明を格納します。  
  
## 構文  
  
```  
<description>  
</description>  
```  
  
## 要素と属性  
 省略可能です。`description` 要素は `vstov4`  名前空間に属します。 この要素は、Microsoft Office アプリケーションの \[COM アドイン\] ダイアログ ボックスに表示されるアドインの説明を格納します。  
  
 `description` 要素には、属性も要素もありません。  
  
## VSTO アドインの例  
  
### 説明  
 次のコード例は、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] を使用して配置されるアプリケーションレベルのソリューションの `description` 要素を示しています。 このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### コード  
  
```  
<vstov4:description> ContosoOutlookAddIn - Outlook add-in created with Visual Studio Tools for Office </vstov4:description>  
```  
  
## 参照  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)  
  
  