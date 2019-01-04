---
title: IDebugProgram2::Execute |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e119224ac628f26f2f1b23eb5c4d65db13b73b2c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873497"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
停止状態からこのプログラムの実行が続行されます。 (ステップ) など、以前の実行状態がオフになって、され、プログラムでは、もう一度実行が開始されます。  
  
> [!NOTE]
>  このメソッドが非推奨とされます。 使用して、 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 ユーザーは、いくつかその他のプログラムのスレッドを停止状態から実行を起動するときに、このプログラムでこのメソッドが呼び出されます。 ユーザーが選択すると、このメソッドが呼び出されますも、**開始**コマンドから、**デバッグ**IDE のメニュー。 このメソッドの実装を呼び出す可能性があります、[再開](../../../extensibility/debugger/reference/idebugthread2-resume.md)プログラムの現在のスレッドでメソッド。  
  
> [!WARNING]
>  停止イベントまたは直接 (同期) イベントを送信しない[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md); この呼び出しを処理中にそれ以外の場合、デバッガーがハングします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)