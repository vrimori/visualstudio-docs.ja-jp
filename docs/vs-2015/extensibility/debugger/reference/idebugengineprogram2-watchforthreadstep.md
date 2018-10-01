---
title: IDebugEngineProgram2::WatchForThreadStep |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15a4374d8155f4acfd233d0662cb62ed6fe1da54
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538353"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugEngineProgram2::WatchForThreadStep](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep)します。  
  
実行を監視します (または実行の監視を停止します)、特定のスレッドで発生します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]0 以外の値 (`TRUE`) で識別されるスレッド上で実行の監視を始めることを意味`dwTid`。 そうしないと、0 (`FALSE`) 上で実行するための視聴を停止したことを意味`dwTid`します。  
  
 `dwFrame`  
 [in]ステップの種類を制御するフレーム インデックスを指定します。 この値はゼロ (0)、ステップの種類が「ステップ イン」と、スレッドがで識別されるたびに、プログラムを停止する必要があります`dwTid`を実行します。 ときに`dwFrame`0 以外の場合は、ステップの種類が「ステップ オーバー」と、スレッドがで識別される場合にのみ、プログラムを停止する必要があります`dwTid`インデックスが同じか、またはよりスタックの上位フレームで実行されている`dwFrame`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 セッション デバッグ マネージャー (SDM) で識別される、プログラムのステップと、`pOriginatingProgram`パラメーターがこのメソッドを呼び出すことによって接続されている他のすべてのプログラムに通知します。  
  
 このメソッドは、同じスレッドがステップ実行にのみ適用されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

