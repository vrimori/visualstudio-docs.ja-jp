---
title: '&lt;アセンブリ&gt;要素 (ClickOnce アプリケーション) |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: edd968ffb6f2b0422e54bc6d456c1090d189fcc0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544357"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;アセンブリ&gt;要素 (ClickOnce アプリケーション)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[&lt;アセンブリ&gt;要素 (ClickOnce アプリケーション)](https://docs.microsoft.com/visualstudio/deployment/assembly-element-clickonce-application)します。  
  
アプリケーション マニフェストの最上位要素。  
  
## <a name="syntax"></a>構文  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `assembly`要素はルート要素でありが必要です。 その最初の構成要素である必要があります、`assemblyIdentity`要素。 マニフェストの要素は、次の名前空間のいずれかである必要があります。  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 アセンブリの子要素は、これらの名前空間を継承またはタグ付けによってもあります。  
  
 `assembly`要素には、次の属性。  
  
|属性|説明|  
|---------------|-----------------|  
|`manifestVersion`|必須。 `manifestVersion`に属性を設定する必要があります`1.0`します。|  
  
## <a name="example"></a>例  
 次のコード例を示しています、`assembly`に対するアプリケーション マニフェスト内の要素を[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション。 このコード例で示されている例の一部は、 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)   
 [\<assembly> 要素](../deployment/assembly-element-clickonce-deployment.md)



