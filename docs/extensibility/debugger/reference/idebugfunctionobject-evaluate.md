---
title: "IDebugFunctionObject::Evaluate |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugFunctionObject::Evaluate
helpviewer_keywords: IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a665f5db26955db2d3879e0d37c07efd3856bf68
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
関数を呼び出すし、オブジェクトとして結果の値を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppParams`  
 [in]配列[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)入力パラメーターを表すオブジェクト。 これらの各パラメーターがのいずれかで作成された、`Create`内のメソッド、 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)インターフェイスです。  
  
 `dwParams`  
 [in]パラメーターの数、`ppParams`配列。  
  
 `dwTimeout`  
 [in]このメソッドから戻る前に待機するミリ秒単位で最大の時間を指定します。 使用して`INFINITE`無制限に待機します。  
  
 `ppResult`  
 [out]返します、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)関数オブジェクトとしての値を表すです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドを設定およびによって表される関数呼び出しを実行、 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)オブジェクト。  
  
## <a name="see-also"></a>参照  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)