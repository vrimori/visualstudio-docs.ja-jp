---
title: '&lt;publisherIdentity&gt;要素 (ClickOnce 配置) |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
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
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 4c11e8ed9a3e0b4341708fc849462fbc476dc395
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540097"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt;要素 (ClickOnce 配置)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ &lt;publisherIdentity&gt;要素 (ClickOnce 配置)](https://docs.microsoft.com/visualstudio/deployment/publisheridentity-element-clickonce-deployment)します。  
  
この配置マニフェストに署名した発行元についての情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `publisherIdentity`要素が署名付きマニフェストに必要です。 次の表は、属性を`publisherIdentity`要素をサポートしています。  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|必須。 このアプリケーションを発行したパーティの id をについて説明します。|  
|`issuerKeyHash`|必須。 証明書の発行者の公開キーの sha-1 ハッシュが含まれています。|  
  
#### <a name="parameters"></a>パラメーター  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>要件  
  
## <a name="subhead"></a>小見出し



