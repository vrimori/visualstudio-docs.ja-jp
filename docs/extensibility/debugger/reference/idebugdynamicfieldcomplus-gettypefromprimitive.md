---
title: IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
- GetTypeFromPrimitive
ms.assetid: d7f51e2a-1b72-489c-b7b6-4af7b7e4d663
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c7264648775f078af16a0a26ecc3bba3a129374c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909864"
---
# <a name="idebugdynamicfieldcomplusgettypefromprimitive"></a>IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
プリミティブ型を指定する型を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetTypeFromPrimitive(  
   DWORD         dwCorElementType,  
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetTypeFromPrimitive(  
   uint            dwCorElementType,  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwCorElementType`  
 [in]値を[CorElementType 列挙型](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration)プリミティブ型を表します。  
  
 `ppType`  
 [out]返します、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)型を表します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)