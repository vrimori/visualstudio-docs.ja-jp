---
title: IDebugProgramEx2::Attach |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 349b1614caa5b2b6e02520d4136f570c09e54aa2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842730"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

セッションは、プログラムにアタッチします。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)アタッチされたデバッグ エンジンにイベントを送信するコールバック関数を表すオブジェクト。  
  
 `dwReason`  
 [in]値、 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)アタッチ操作の理由を説明する列挙体。  
  
 `pSession`  
 [in]プログラムにアタッチするセッションを一意に識別する値。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外の場合はエラー コードを返します。 このメソッドが返す必要があります`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`プログラムが既にアタッチされている場合。  
  
## <a name="remarks"></a>Remarks  
 プログラムを含むポート値を使用できる`pSession`をプログラムにアタッチしようとしているセッションを確認します。 たとえば、ポートは、一度にプロセスにアタッチする 1 つだけのデバッグ セッションを許可している場合、ポートによってできます同じのセッションが既にプロセス内の他のプログラムにアタッチするかどうかを決定します。  
  
> [!NOTE]
>  インターフェイスが渡された`pSession`がクッキー、セッション デバッグ マネージャー; このプログラムへのアタッチを一意に識別する値としてのみ扱われる、指定されたインターフェイスのメソッドのいずれも機能します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)

