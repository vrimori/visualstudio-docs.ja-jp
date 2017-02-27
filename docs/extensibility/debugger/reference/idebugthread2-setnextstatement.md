---
title: "IDebugThread2::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::SetNextStatement"
helpviewer_keywords: 
  - "IDebugThread2::SetNextStatement"
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::SetNextStatement
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

特定のコードのコンテキストに現在の命令ポインターを設定します。  
  
## 構文  
  
```cpp#  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```c#  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### パラメーター  
 `pStackFrame`  
 将来使用するために予約されています ; null 値に設定します。  
  
 `pCodeContext`  
 \[入力\] 実行するコードを記述する場所はコンテキスト [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) のオブジェクト。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  次の表は他の値を示します。  
  
|値|Description|  
|-------|-----------------|  
|E\_CAN のない \_SET\_NEXT\_STATEMENT\_ON\_NONLEAF\_FRAME|次のステートメントはフレームのスタック上でさらに深い位置にあるスタック フレームにすることはできません。|  
|E\_CAN のない \_SETIP\_TO\_DIFFERENT\_FUNCTION|次のステートメントはスタック フレームに関連付けられません。|  
|E\_CAN のない \_SET\_NEXT\_STATEMENT\_ON\_EXCEPTION|一部のデバッグ エンジンは例外の後に次のステートメントを設定できません。|  
  
## 解説  
 命令ポインターは次に実行する命令またはステートメントを示します。  このメソッドはソース・コードの行を再試行または別の関数に従うに実行を強制する場合などに使用されます。  
  
## 参照  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)