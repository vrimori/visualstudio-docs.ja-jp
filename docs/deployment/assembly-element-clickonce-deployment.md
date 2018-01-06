---
title: "&lt;アセンブリ&gt;要素 (ClickOnce 配置) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: "11"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: c19312b005a1f8dfeefa766ed3a5e6a8ab1c566c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;アセンブリ&gt;要素 (ClickOnce 配置)
配置マニフェストの最上位要素です。  
  
## <a name="syntax"></a>構文  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `assembly`要素はルート要素がありが必要です。 その最初の構成要素である必要があります、`assemblyIdentity`要素。 マニフェストの要素は、次の名前空間である必要があります: `urn:schemas-microsoft-com:asm.v1`、 `urn:schemas-microsoft-com:asm.v2`、および`http://www.w3.org/2000/09/xmldsig#`です。 アセンブリの子要素は、これらの名前空間を継承またはタグ付けによってもする必要があります。  
  
 `assembly`要素には、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`manifestVersion`|必須。 この属性に設定する必要があります`1.0`です。|  
  
## <a name="example"></a>例  
 次のコード例を示しています、`assembly`を使用してデプロイされたアプリケーションの配置マニフェスト内の要素[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]です。 このコード例に示されている例の一部である、 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)トピックです。  
  
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
  
## <a name="see-also"></a>参照  
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [\<アセンブリ > 要素](../deployment/assembly-element-clickonce-application.md)