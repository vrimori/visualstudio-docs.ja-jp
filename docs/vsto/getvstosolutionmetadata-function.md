---
title: GetVstoSolutionMetadata 関数
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
ms.openlocfilehash: e6289a0d19bc6621d98edfc974ad265791876a70
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673635"
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
  
  