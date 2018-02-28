---
title: "IDebugFunctionObject::CreateArrayObject |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5dfe24252ce2ce51ff86fa680d94964b86d09365
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
配列オブジェクトを作成します。 この配列では、いずれかのプリミティブ型を含むしたり、オブジェクトのインスタンスの値することができます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ot`  
 [in]値を指定して、 [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md)新しい配列のオブジェクトの種類を示す列挙値。  
  
 `pClassField`  
 [in][IDebugField](../../../extensibility/debugger/reference/idebugfield.md)オブジェクトの配列のインスタンスの値を作成する場合は、オブジェクトのクラスを表すオブジェクト。 プリミティブ オブジェクトの配列を作成するには、このパラメーターは、null 値を使用します。  
  
 `dwRank`  
 [in]ランクまたは配列の次元の数。  
  
 `dwDims`  
 [in]配列の各次元のサイズ。  
  
 `dwLowBounds`  
 [in]各ディメンションの原点 (通常 0 または 1)。  
  
 `ppObject`  
 [out]返します、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)を新しく作成された配列を表すオブジェクト。 これは、実際には、 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 によって表される関数を配列パラメーターを表すオブジェクトを作成するには、このメソッドを呼び出す、 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)インターフェイスです。  
  
## <a name="see-also"></a>参照  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)