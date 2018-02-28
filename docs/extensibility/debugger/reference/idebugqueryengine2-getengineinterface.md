---
title: "IDebugQueryEngine2::GetEngineInterface |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 65f40bf3e0e110a6d945921d06443f0c8a608d20
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
カスタム デバッグ エンジン (DE) インターフェイスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetEngineInterface(   
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetEngineInterface(   
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppUnk`  
 [out]返します、`IUnknown`オブジェクトを表し、デバッグ エンジン (DE) を DE に関連付けられているその他の有効なインターフェイスのクエリを実行できます (たとえば[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)または[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md))。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドから取得されたインターフェイスを使用した呼び出しは、セッション デバッグ マネージャーの処理を回避し、SDM を不適切な状態にまたはデバッグ中にエラーは生成されない可能性がありますので注意して、結果として得られるインターフェイスを使用してください。  
  
## <a name="see-also"></a>参照  
 [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)