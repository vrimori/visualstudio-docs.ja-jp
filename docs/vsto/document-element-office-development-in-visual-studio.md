---
title: "&lt;document&gt; 要素 (Visual Studio での Office 開発)"
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
  - "document 要素"
  - "アプリケーション マニフェスト [Visual Studio での Office 開発]、<document> 要素"
  - "<document> 要素"
ms.assetid: b4525a0e-8a03-4881-a3e2-8cc019029071
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;document&gt; 要素 (Visual Studio での Office 開発)
  `vstov4` 名前空間の `document` 要素には、ドキュメント レベルのカスタマイズ用のカスタマイズ固有の情報が格納されます。  
  
## 構文  
  
```  
<document solutionId />  
```  
  
## 要素と属性  
 ドキュメント レベルのカスタマイズでのみ必須です。  `document` 要素は、`vstov4` 名前空間にあります。  `document` 要素には、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`solutionId`|必ず指定します。  ドキュメント レベルのソリューションを識別して Office ランタイムの Visual Studio のツールによって使用される GUID。  この値は、\_AssemblyLocation カスタム ドキュメント プロパティとして格納されます。  詳細については、「[カスタム ドキュメント プロパティの概要](../vsto/custom-document-properties-overview.md)」を参照してください。|  
  
 `document` には子要素がありません。  
  
## ドキュメント レベルのカスタマイズの例  
  
### Description  
 次のコード例は、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] を使用して配置されるドキュメント レベルの Office ソリューション内の `document` 要素を示しています。  このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」で紹介されている大きな例の一部です。  
  
### コード  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## 参照  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)  
  
  