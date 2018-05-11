---
title: IDebugProgram2::Execute |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: f7f4e26a5c892e1c796a2b6e2f9371898db21f68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)