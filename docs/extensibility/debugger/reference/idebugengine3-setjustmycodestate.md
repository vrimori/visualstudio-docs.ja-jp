---
title: IDebugEngine3::SetJustMyCodeState |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9dafc7a98b511c9d7b8367e96621faee9e2cbc22
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914424"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
このメソッドは、JustMyCode 状態情報のデバッグ エンジンを指示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fUpdate`  
 [in]0 以外の場合 (`TRUE`) 現在の情報を更新するには、0 (`FALSE`) (何も以前の設定は無視されます) すべての情報をリセットします。  
  
 `dwModules`  
 [in]情報構造体の数 `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in]配列[JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)を使用する構造体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 JustMyCode をユーザーに属しているコードのみをデバッグして、システム コードなどのすべての中間コードを無視するという概念は、-場合でも、そのシステム コードのソース コードが使用されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)