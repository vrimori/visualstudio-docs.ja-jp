---
title: IDebugField::Equal |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7fdfc2abd407c586c949ade4e8085e282fb465a8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984354"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
このメソッドは、このフィールドに等しいかどうかを指定したフィールドを比較します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pField`  
 [in]この 1 と比較するフィールドです。  
  
## <a name="return-value"></a>戻り値  
 フィールドが同じ場合は、返す`S_OK`します。 フィールドが異なる場合は、返す`S_FALSE.`それ以外の場合、エラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)