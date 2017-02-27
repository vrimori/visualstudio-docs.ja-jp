---
title: "例外処理 (Visual Studio SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグ SDK] 例外処理のデバッグ"
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 例外処理 (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次は例外がスローされたときに発生するプロセスについて説明します。  
  
## 例外処理の手順  
  
1.  例外がスローされると最初にデバッグするプログラムの例外ハンドラーによって処理される前にデバッグ エンジンは \(DE\) 停止のイベントとしてデバッグ セッションのマネージャー \(SDM\) に [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) を送信します。  `IDebugExceptionEvent2` はユーザーが初回例外通知に停止することを示す例外の設定にのみ \(デバッグのパッケージの例外のダイアログ ボックスで指定\) を指定して送信されます。  
  
2.  SDM は例外のプロパティを取得するに [IDebugExceptionEvent2:: GetException](../Topic/IDebugExceptionEvent2::GetException.md) を呼び出します。  
  
3.  デバッグのパッケージはユーザーに表示されるオプションを確認するに [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) を呼び出します。  
  
4.  デバッグのパッケージは初回例外のダイアログ ボックスを開くことで例外を処理する方法をたずねるメッセージが表示されます。  
  
5.  ユーザーが続行するには SDM は [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) を呼び出します。  
  
    -   メソッドは S\_OK を呼び出します [IDebugExceptionEvent2:: PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)。  
  
         または  
  
         メソッドは S\_FALSE を返しますがデバッグプログラム例外を処理する 2 番目のダイアログ設定する。  
  
6.  デバッグ対象のプログラムにセカンド チャンス例外のハンドラーがない場合de\-DE sends **EVENT\_SYNC\_STOP** として SDM への `IDebugExceptionEvent2`。  
  
7.  デバッグのパッケージは初回例外のダイアログ ボックスを開くことで例外を処理する方法をたずねるメッセージが表示されます。  
  
8.  デバッグのパッケージはユーザーに表示されるオプションを確認するに [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) を呼び出します。  
  
9. デバッグのパッケージはユーザーがセカンド チャンス例外のダイアログ ボックスを開くことで例外を処理する方法をたずねるメッセージが表示されます。  
  
10. メソッドは S\_OK を呼び出します `IDebugExceptionEvent2::PassToDebuggee`。  
  
## 参照  
 [デバッガー イベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)