---
title: "IDebugProcessEx2::Attach |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: da89be65f4b02fa0db254dd85463e422d17fe589
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
このメソッドは、セッションが今すぐ、プロセスをデバッグしているプロセスに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Attach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Attach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pSession`  
 [in]このプロセスにアタッチするセッションを一意に識別する値。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 インターフェイスが渡される`pSession`cookie です。 このプロセスにアタッチするセッションのデバッグ マネージャーを一意に識別する値としてのみ処理されますが、指定されたインターフェイスのメソッドのいずれも機能します。  
  
## <a name="see-also"></a>参照  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)