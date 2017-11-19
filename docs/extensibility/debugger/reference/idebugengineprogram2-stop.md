---
title: "IDebugEngineProgram2::Stop |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2::Stop
helpviewer_keywords: IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 21dd14e1cc4d4e8c6b65b5285763a680a5f327f7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
このプログラムで実行されているすべてのスレッドを停止します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Stop(   
   void   
);  
```  
  
```csharp  
int Stop();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 複数のプログラムの環境でこのプログラムをデバッグするときに、このメソッドが呼び出されます。 他のプログラムから停止イベントを受信すると、このプログラムにこのメソッドが呼び出されます。 このメソッドの実装が非同期; する必要があります。つまり、いないすべてのスレッドは、このメソッドが戻る前に停止する必要する必要があります。 このメソッドの実装を呼び出すなどの単純な可能性があります、 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)このプログラムのメソッドです。  
  
 このメソッドへの応答では、デバッグ イベントは送信されません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)