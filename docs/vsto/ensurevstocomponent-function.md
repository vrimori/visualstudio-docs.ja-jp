---
title: EnsureVSTOComponent 関数
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 20c4e363b11647609b67a898878dd4b4e59ba180
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2018
---
# <a name="ensurevstocomponent-function"></a>EnsureVSTOComponent 関数
  この API は、Office インフラストラクチャをサポートしてをコードから直接使用するためのものではありません。  
  
## <a name="syntax"></a>構文  
  
```c  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*pProject*|使用しないでください。|  
  
## <a name="return-value"></a>戻り値  
 関数が成功したかどうか、それを返します**S_OK**です。 関数が失敗した場合、エラー コードを返します。  
  
  