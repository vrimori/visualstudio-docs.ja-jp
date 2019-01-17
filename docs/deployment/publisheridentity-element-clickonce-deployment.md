---
title: '&lt;publisherIdentity&gt;要素 (ClickOnce 配置) |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c9c54b539945093e55aa770f07acc54b589f0c70
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950093"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt;要素 (ClickOnce 配置)
この配置マニフェストに署名した発行元についての情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```xml  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `publisherIdentity`要素が署名付きマニフェストに必要です。 次の表は、属性を`publisherIdentity`要素をサポートしています。  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|必須です。 このアプリケーションを発行したパーティの id をについて説明します。|  
|`issuerKeyHash`|必須です。 証明書の発行者の公開キーの sha-1 ハッシュが含まれています。|  
  
#### <a name="parameters"></a>パラメーター  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>コメント  
  
## <a name="requirements"></a>要件  
  
## <a name="subhead"></a>小見出し