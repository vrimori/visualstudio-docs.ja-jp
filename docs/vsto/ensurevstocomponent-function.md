---
title: EnsureVSTOComponent 関数
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 912c28086bb918afa406fca7cf4acce06e5be099
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866078"
---
# <a name="ensurevstocomponent-function"></a>EnsureVSTOComponent 関数
  この API は、オフィスのインフラストラクチャをサポートしているし、コードから直接使用するものではありません。  
  
## <a name="syntax"></a>構文  
  
```csharp  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*pProject*|使用しないでください。|  
  
## <a name="return-value"></a>戻り値  
 返します、関数が成功したかどうかは**S_OK**します。 関数が失敗した場合、エラー コードを返します。  
