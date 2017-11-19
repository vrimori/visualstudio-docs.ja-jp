---
title: "IDebugEngine2::CauseBreak |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::CauseBreak
helpviewer_keywords: IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eeb8c262d6e1abc88e40f027d921ae2d4ae12cf2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
要求のすべてのプログラムによってこのデバッグ エンジン、次回の実行を停止するには、(DE) デバッグ中のスレッドの 1 つ実行されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは非同期: [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)イベントは、次に、プログラムはこのメソッドが呼び出された後に実行しようとしたときに送信します。  
  
## <a name="see-also"></a>関連項目  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)