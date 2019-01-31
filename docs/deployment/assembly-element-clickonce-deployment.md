---
title: '&lt;アセンブリ&gt;要素 (ClickOnce 配置) |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e6192c7705555e817ed82d452d703f0affd9609
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932702"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;アセンブリ&gt;要素 (ClickOnce 配置)
配置マニフェストの最上位要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `assembly`要素はルート要素でありが必要です。 その最初の構成要素である必要があります、`assemblyIdentity`要素。 マニフェストの要素は次の名前空間内に存在する必要があります: `urn:schemas-microsoft-com:asm.v1`、 `urn:schemas-microsoft-com:asm.v2`、および`http://www.w3.org/2000/09/xmldsig#`します。 アセンブリの子要素は、これらの名前空間を継承またはタグ付けによってもあります。  
  
 `assembly` 要素には、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`manifestVersion`|必須です。 この属性に設定する必要があります`1.0`します。|  
  
## <a name="example"></a>例  
 次のコード例を示しています、`assembly`要素を使用してデプロイされたアプリケーションの配置マニフェストで[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]します。 このコード例が示されている例の一部、 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)トピック。  
  
```xml  
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
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [\<アセンブリ > 要素](../deployment/assembly-element-clickonce-application.md)
