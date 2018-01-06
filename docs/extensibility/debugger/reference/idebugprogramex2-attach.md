---
title: "IDebugProgramEx2::Attach |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramEx2::Attach
helpviewer_keywords: IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 440a4ce6b008efe541187d1d99d886f4c7c5f9ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
プログラムにセッションをアタッチします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)にイベントをアタッチされたデバッグ エンジンに送信するコールバック関数を表すオブジェクト。  
  
 `dwReason`  
 [in]値、 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)アタッチ操作の理由を説明する列挙体です。  
  
 `pSession`  
 [in]プログラムにアタッチされているセッションを一意に識別する値。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 それ以外の場合はエラー コードを返します。 このメソッドが返す`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`プログラムが既にアタッチされている場合。  
  
## <a name="remarks"></a>コメント  
 プログラムが含まれているポートの値を使用できます`pSession`をプログラムにアタッチしようとしてセッションを確認します。 たとえば、ポートは、プロセスにアタッチする、一度に 1 つのみのデバッグ セッションを許可している場合、ポートを判断できます、同じセッションが既にプロセス内の他のプログラムにアタッチされているかどうか。  
  
> [!NOTE]
>  インターフェイスが渡される`pSession`のみ、クッキー、セッション デバッグ マネージャーです。 このプログラムへのアタッチを一意に識別する値として扱われますが、指定されたインターフェイスのメソッドのいずれも機能します。  
  
## <a name="see-also"></a>参照  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)