---
title: GetVstoSolutionMetadata 関数
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: f0cb0acd57ff04b7487d5311f8a05219b3ce0c0a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853724"
---
# <a name="getvstosolutionmetadata-function"></a>GetVstoSolutionMetadata 関数
  この API は、オフィスのインフラストラクチャをサポートしているし、コードから直接使用するものではありません。  
  
## <a name="syntax"></a>構文  
  
```csharp
HRESULT WINAPI GetVstoSolutionMetadata(  
    LPCWSTR lpwszSolutionMetadataKey,  
    ISolutionMetadata** ppSolutionInfo  
);  
```  
  
### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*lpwszSolutionMetadataKey*|使用しないでください。|  
|*ppSolutionInfo*|使用しないでください。|  
  
## <a name="return-value"></a>戻り値  
 返します、関数が成功したかどうかは**S_OK**します。 関数が失敗した場合、エラー コードを返します。  
