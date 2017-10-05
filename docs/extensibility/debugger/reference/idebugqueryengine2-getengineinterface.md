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
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 598606c6360993e664eda19e30b1a8b017a59e3a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

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
  
## <a name="see-also"></a>関連項目  
 [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
