---
title: "IDebugProgram2::Execute |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2e53f13aea93de8f39c5802dd2a12598ad938f64
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
停止状態からこのプログラムの実行が続行されます。 (ステップ) など、以前の実行状態がオフになって、しを再度実行して、プログラムを開始します。  
  
> [!NOTE]
>  このメソッドは推奨されません。 使用して、 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)メソッド代わりにします。  
  
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
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 ユーザーは、他のプログラムのスレッドを停止状態から実行を起動するときに、このプログラムにこのメソッドが呼び出されます。 ユーザーを選択すると、このメソッドが呼び出されますも、**開始**コマンドを**デバッグ**IDE のメニュー。 このメソッドの実装を呼び出すなどの単純な可能性があります、[再開](../../../extensibility/debugger/reference/idebugthread2-resume.md)プログラムに現在のスレッドでのメソッドです。  
  
> [!WARNING]
>  停止イベントまたは直接 (同期) イベントを送信しない[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)です。 この呼び出しを処理中にそれ以外の場合、デバッガーがハングアップします。  
  
## <a name="see-also"></a>参照  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)