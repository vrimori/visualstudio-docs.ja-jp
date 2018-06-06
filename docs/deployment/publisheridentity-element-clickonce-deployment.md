---
title: '&lt;publisherIdentity&gt;要素 (ClickOnce 配置) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
ms.openlocfilehash: 92b0082d7a2b062d946d132c5a86fbceb5208802
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815143"
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