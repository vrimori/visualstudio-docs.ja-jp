---
title: GetValidCompatibleFramework 関数
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
ms.openlocfilehash: 8cc16544df224e09724cae8a1f09f72039cb61e5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894496"
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework 関数
  この API は、オフィスのインフラストラクチャをサポートしているし、コードから直接使用するものではありません。  

## <a name="syntax"></a>構文  

```csharp 
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  

### <a name="parameters"></a>パラメーター  

|パラメーター|説明|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|使用しないでください。|  
|*pbstrValidFrameworkTag*|使用しないでください。|  

## <a name="return-value"></a>戻り値  
 返します、関数が成功したかどうかは**S_OK**します。 関数が失敗した場合、エラー コードを返します。  

