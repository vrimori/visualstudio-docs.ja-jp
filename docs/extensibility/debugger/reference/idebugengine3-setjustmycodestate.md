---
title: "IDebugEngine3::SetJustMyCodeState |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine3::SetJustMyCodeState
helpviewer_keywords: IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 08d396d378f168b9a54e3b640e69dfeb3f6c9ba1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
このメソッドは、JustMyCode 状態情報、デバッグ エンジンを指示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
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
 [in]0 以外 (`TRUE`) 現在の情報を更新するには、0 (`FALSE`) (何も設定されて無視されます) すべての情報をリセットします。  
  
 `dwModules`  
 [in]情報の構造体の数`rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in]配列[JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)を使用する構造体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 JustMyCode の概念、ユーザーが属しているコードのみのデバッグと、システム コードなどのすべての中間コードを無視するは、ソース コードがそのシステム コードの使用可能な場合でもです。  
  
## <a name="see-also"></a>参照  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)