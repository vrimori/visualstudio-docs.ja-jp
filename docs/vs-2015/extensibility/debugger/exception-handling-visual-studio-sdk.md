---
title: 例外処理 (Visual Studio SDK) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ac3e05d37c844006642469e28eadff22553ec31e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269218"
---
# <a name="exception-handling-visual-studio-sdk"></a>例外処理 (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 [デバッガーのイベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)

