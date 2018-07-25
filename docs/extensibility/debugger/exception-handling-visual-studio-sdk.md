---
title: 例外処理 (Visual Studio SDK) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab3a3aafdca83305b86ce083e53e654b637cf110
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232066"
---
# <a name="exception-handling-visual-studio-sdk"></a>例外処理 (Visual Studio SDK)
次に、例外がスローされたときに発生するプロセスについて説明します。  
  
## <a name="exception-handling-process"></a>例外処理のプロセス  
  
1.  例外がスローされた最初が、デバッグ エンジン (DE) を送信前に、デバッグ中のプログラム内の例外ハンドラーによって処理される、ときに、 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) stopping イベントとしてセッション デバッグ マネージャー (SDM)。 `IDebugExceptionEvent2` (デバッグ パッケージの [例外] ダイアログ ボックスで指定された) 例外の設定、ユーザーが初回例外通知を停止することを指定する場合のみ送信されます。  
  
2.  SDM コール[IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)例外のプロパティを取得します。  
  
3.  デバッグ パッケージ呼び出し[IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)をユーザーに提示するオプションを決定します。  
  
4.  デバッグ パッケージは、ユーザーに初回例外ダイアログ ボックスを開くことで、例外を処理する方法を確認します。  
  
5.  ユーザーの続行を選択する場合、SDM を呼び出す[IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)します。  
  
    -   場合は S_OK を返すと、メソッドを呼び出す[IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)します。  
  
         - または -  
  
         メソッドは、プログラムは S_FALSE を返す場合、デバッグ中は例外を処理するチャンスをもう 1 を付与します。  
  
6.  デバッグ中のプログラムに次の例外のハンドラーがあるない場合、DE の送信、`IDebugExceptionEvent2`として SDM を**EVENT_SYNC_STOP**します。  
  
7.  デバッグ パッケージは、ユーザーに初回例外ダイアログ ボックスを開くことで、例外を処理する方法を確認します。  
  
8.  デバッグ パッケージ呼び出し[IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)をユーザーに提示するオプションを決定します。  
  
9. デバッグ パッケージは、次の例外のダイアログ ボックスを開き、例外を処理する方法をユーザーに確認します。  
  
10. 場合は S_OK を返すと、メソッドを呼び出す`IDebugExceptionEvent2::PassToDebuggee`します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガー イベントを呼び出す](../../extensibility/debugger/calling-debugger-events.md)