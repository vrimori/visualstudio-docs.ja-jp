---
title: IDebugFunctionObject::CreatePrimitiveObject |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 477bdb12cef6711c6b946b3ddd8d9550e48c01b0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111304"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
単純な整数などのプリミティブ データ オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ot`  
 [in]値、 [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md)を作成するプリミティブ型の型を表す列挙体です。  
  
 `ppObject`  
 [out]返します、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)新しく作成されたオブジェクトを表すです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 パラメーターによって表される関数を指定するプリミティブ オブジェクトを表すオブジェクトを作成するには、このメソッドを呼び出す、 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)インターフェイスです。 たとえば、式の文字列が"myString(5)"の場合は、5 の整数を表すオブジェクトを作成するこのメソッドが使用されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)