---
title: "例外処理 (Visual Studio SDK) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4a0d950de8e9f91232e3526064561a7508c133b4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="exception-handling-visual-studio-sdk"></a>例外処理 (Visual Studio SDK)
次に、例外がスローされたときに発生するプロセスについて説明します。  
  
## <a name="exception-handling-process"></a>例外処理  
  
1.  最初に例外をスローが、デバッグ中のプログラムでの例外ハンドラーが処理する前に、デバッグ エンジン (DE) が送信時に、 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)停止イベントとしてセッション デバッグ マネージャー (SDM) にします。 `IDebugExceptionEvent2` (デバッグ パッケージの [例外] ダイアログ ボックスで指定) は、例外の設定では、ユーザーが初回例外通知を停止することを指定する場合のみに送信します。  
  
2.  SDM 呼び出し[IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)例外のプロパティを取得します。  
  
3.  デバッグ パッケージ呼び出し[IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)をユーザーに提示するオプションを決定します。  
  
4.  デバッグ パッケージは、初回例外 ダイアログ ボックスを開くことによって、例外を処理する方法をユーザーに確認します。  
  
5.  SDM を呼び出す場合、ユーザーは、続行を選択する、 [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)です。  
  
    -   場合は S_OK を返すメソッドを呼び出す[IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)です。  
  
         または  
  
         メソッドは、プログラムは S_FALSE を返す場合、デバッグ中は例外を処理する 2 番目の機会を付与します。  
  
6.  デバッグ中のプログラムには、次の例外のハンドラーがあるない、デ送信、`IDebugExceptionEvent2`として SDM に**EVENT_SYNC_STOP**です。  
  
7.  デバッグ パッケージは、初回例外 ダイアログ ボックスを開くことによって、例外を処理する方法をユーザーに確認します。  
  
8.  デバッグ パッケージ呼び出し[IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)をユーザーに提示するオプションを決定します。  
  
9. デバッグ パッケージは、次の例外 ダイアログ ボックスを開くことによって、例外を処理する方法をユーザーに確認します。  
  
10. 場合は S_OK を返すメソッドを呼び出す`IDebugExceptionEvent2::PassToDebuggee`です。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのイベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)