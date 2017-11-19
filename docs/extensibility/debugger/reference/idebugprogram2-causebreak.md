---
title: "IDebugProgram2::CauseBreak |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::CauseBreak
helpviewer_keywords: IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a58abdcf816896c0705a7ecce32ae82c9c8f16d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
プログラムが次の実行を停止する要求を実行するには、そのスレッド試行の回数が 1 回目です。  
  
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
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)イベントは、次に、プログラムはこのメソッドが呼び出された後にコードを実行しようとしたときに送信します。  
  
 メソッドは必ずしもを停止するプログラムを待たずにすぐに返します点で、このメソッドは非同期です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)