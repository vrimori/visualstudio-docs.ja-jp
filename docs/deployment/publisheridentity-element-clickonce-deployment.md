---
title: "&lt;publisherIdentity&gt;要素 (ClickOnce 配置) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: "11"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 527ab7ae43790f7e824ead33fb601f0f8dee2bf0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt;要素 (ClickOnce 配置)
この配置マニフェストに署名した発行元についての情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `publisherIdentity`要素は署名付きマニフェストに必須です。 次の表は、属性を`publisherIdentity`要素をサポートしています。  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|必須。 このアプリケーションを発行したパーティの id をについて説明します。|  
|`issuerKeyHash`|必須。 証明書の発行者の公開キーの sha-1 ハッシュが含まれています。|  
  
#### <a name="parameters"></a>パラメーター  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>コメント  
  
## <a name="requirements"></a>必要条件  
  
## <a name="subhead"></a>小見出し