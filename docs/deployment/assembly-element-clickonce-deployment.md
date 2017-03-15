---
title: "&lt;assembly&gt; 要素 (ClickOnce 配置) | Microsoft Docs"
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
  - "<assembly> 要素 [ClickOnce 配置マニフェスト]"
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# &lt;assembly&gt; 要素 (ClickOnce 配置)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

配置マニフェストのトップレベルの要素です。  
  
## 構文  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## 要素と属性  
 `assembly` 要素はルート要素であり、必ず指定します。  この要素に最初に含まれる要素は `assemblyIdentity` でなければなりません。  マニフェスト要素は、`urn:schemas-microsoft-com:asm.v1` 名前空間、`urn:schemas-microsoft-com:asm.v2` 名前空間、または `http://www.w3.org/2000/09/xmldsig#` 名前空間に存在する必要があります。  アセンブリの子要素は、継承またはタグ設定によってこれらの名前空間にも配置する必要があります。  
  
 `assembly` 要素には、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`manifestVersion`|必ず指定します。  この属性は `1.0` に設定する必要があります。|  
  
## 使用例  
 次のコード例は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] を使用して配置されるアプリケーションの配置マニフェスト内の `assembly` 要素を示しています。  このコード例は、「[ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)」で示されている例の一部の抜粋です。  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
```  
  
## 参照  
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [\<assembly\> 要素](../deployment/assembly-element-clickonce-application.md)