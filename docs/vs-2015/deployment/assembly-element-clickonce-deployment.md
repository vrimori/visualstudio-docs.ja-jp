---
title: '&lt;assembly&gt;要素 (ClickOnce 配置) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 5fa45d64956fe1347477abb533e45565f27996f7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259949"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;assembly&gt;要素 (ClickOnce 配置)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

配置マニフェストの最上位要素。  
  
## <a name="syntax"></a>構文  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `assembly`要素はルート要素でありが必要です。 その最初の構成要素である必要があります、`assemblyIdentity`要素。 マニフェストの要素は次の名前空間内に存在する必要があります: `urn:schemas-microsoft-com:asm.v1`、 `urn:schemas-microsoft-com:asm.v2`、および`http://www.w3.org/2000/09/xmldsig#`します。 アセンブリの子要素は、これらの名前空間を継承またはタグ付けによってもあります。  
  
 `assembly` 要素には、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`manifestVersion`|必須。 この属性に設定する必要があります`1.0`します。|  
  
## <a name="example"></a>例  
 次のコード例を示しています、`assembly`要素を使用してデプロイされたアプリケーションの配置マニフェストで[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]します。 このコード例が示されている例の一部、 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)トピック。  
  
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
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [\<assembly> 要素](../deployment/assembly-element-clickonce-application.md)



