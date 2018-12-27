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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 39dcdcc5e3b8e6e5bc5834e7e05ea22516d8c7e6
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648614"
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
  
  