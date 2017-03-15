---
title: "&lt;assembly&gt; 要素 (ClickOnce アプリケーション) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assembly> 要素 [ClickOnce アプリケーション マニフェスト]"
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# &lt;assembly&gt; 要素 (ClickOnce アプリケーション)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

アプリケーション マニフェストのトップレベルの要素です。  
  
## 構文  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## 要素と属性  
 `assembly` 要素はルート要素であり、必ず指定します。  この要素に最初に含まれる要素は `assemblyIdentity` でなければなりません。  マニフェスト要素は次のいずれかの名前空間に含まれている必要があります。  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 アセンブリの子要素は、継承またはタグ設定によってこれらの名前空間にも配置する必要があります。  
  
 `assembly` 要素には、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`manifestVersion`|必ず指定します。  `manifestVersion` 属性は `1.0` に設定する必要があります。|  
  
## 使用例  
 次のコード例は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションのアプリケーション マニフェスト内の `assembly` 要素を示しています。  このコード例は、「[ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)」で示されている例の一部の抜粋です。  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
```  
  
## 参照  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)   
 [\<assembly\> 要素](../deployment/assembly-element-clickonce-deployment.md)