---
title: IDebugEngineProgram2::WatchForThreadStep |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f7c897c4c5b8488766f72723f3e85909281abbf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
実行は監視 (または実行の監視を停止する) に特定のスレッドで発生します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```csharp  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pOriginatingProgram`  
 [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)ステップが実行されているプログラムを表すオブジェクト。  
  
 `dwTid`  
 [in]ウォッチするスレッドの識別子を指定します。  
  
 `fWatch`  
 [in]0 以外の値 (`TRUE`) によって識別されるスレッド上で実行の監視を始めることを意味`dwTid`以外の場合、0 (`FALSE`) 手段は、上で実行するための視聴を停止`dwTid`です。  
  
 `dwFrame`  
 [in]ステップの種類を制御するフレーム インデックスを指定します。 これは、値はゼロ (0)、ステップの種類が「ステップ イン」と、プログラムがによって識別される、スレッドを停止する必要があります`dwTid`を実行します。 ときに`dwFrame`0 以外の場合は、ステップの種類が「ステップ オーバー」とで、スレッドが識別される場合にのみ、プログラムを停止する必要があります`dwTid`フレームを持つインデックスと等しいかよりスタックの上位で実行されている`dwFrame`です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 場合セッション デバッグ マネージャー (SDM) の手順で識別される、プログラム、`pOriginatingProgram`パラメーター、このメソッドを呼び出すことによって接続されている他のすべてのプログラムをユーザーに通知します。  
  
 このメソッドは、同じスレッドのステップにのみ適用されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)