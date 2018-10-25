---
title: IDebugBinder3::GetMemoryObject |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetMemoryObject
helpviewer_keywords:
- IDebugBinder3::GetMemoryObject method
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f73af4ee866ad41b93162090660ea34701f36710
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896140"
---
# <a name="idebugbinder3getmemoryobject"></a>IDebugBinder3::GetMemoryObject
このメソッドは、このオブジェクトのバインド先のメモリを表すメモリ オブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMemoryObject(  
   IDebugField*   pField,  
   UINT64         uConstant,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int GetMemoryObject(  
   IDebugField      pField,  
   long             uConstant,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pField`  
 [in]メモリ オブジェクトを取得するには、どのフィールドを指定します。  
  
 `uConstant`  
 [in]メモリ アドレス、または定数値の値を表します。  
  
 `ppObject`  
 [out][IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)にこのオブジェクトがバインドされているメモリを表します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)