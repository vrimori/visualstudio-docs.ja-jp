---
title: "&lt;publisherIdentity&gt; 要素 (ClickOnce 配置) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "publisherIdentity 要素 [ClickOnce 配置マニフェスト], 概要"
  - "publisherIdentity 要素 [ClickOnce 配置マニフェスト], 構文, 要素, および 属性"
  - "署名付きマニフェストに必要な要素 [ClickOnce], publisherIdentity 要素"
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;publisherIdentity&gt; 要素 (ClickOnce 配置)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この配置マニフェストに署名した発行者に関する情報が含まれます。  
  
## 構文  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## 要素と属性  
 `publisherIdentity` 要素は、署名付きマニフェストに対して必ず指定します。  `publisherIdentity` 要素でサポートされる属性を次の表に示します。  
  
|属性|Description|  
|--------|-----------------|  
|`name`|必ず指定します。  このアプリケーションの発行者の ID を示します。|  
|`issuerKeyHash`|必ず指定します。  証明書の発行者の公開キーの SHA\-1 ハッシュを示します。|  
  
#### パラメーター  
  
## プロパティ値\/戻り値  
  
## 例外  
  
## 解説  
  
## 必要条件  
  
## 小見出し