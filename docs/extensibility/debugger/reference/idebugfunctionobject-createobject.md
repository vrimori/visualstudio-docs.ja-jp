---
title: "IDebugFunctionObject::CreateObject |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugFunctionObject::CreateObject
helpviewer_keywords: IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9ba06089624a585688f481719b2ce51397653cd1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
コンス トラクターを使用してオブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pConstructor`  
 [in][IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)を作成するオブジェクトのコンス トラクターを表すオブジェクト。  
  
 `dwArgs`  
 [in]パラメーターの数、`pArg`配列。 コンス トラクターに渡されるパラメーターの数を表します。  
  
 `pArg`  
 [in]配列[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)コンス トラクターに渡されるパラメーターを表すオブジェクトします。  
  
 `ppObject`  
 [out]返します、`IDebugObject`新しく作成されたオブジェクトを表すです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 クラス (またはその他の複合型コンス トラクターが必要です) のインスタンスを表すオブジェクトを作成するには、このメソッドの呼び出しによって表される関数のパラメーターは、 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)インターフェイスです。  
  
 オブジェクトのパラメーターにコンス トラクターが必要としない場合は、呼び出し、 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)