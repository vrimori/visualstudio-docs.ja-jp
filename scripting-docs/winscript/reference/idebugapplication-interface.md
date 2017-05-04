---
title: "IDebugApplication インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication インターフェイス"
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugApplication インターフェイス
言語のエンジンとホストによって使用されるように、リモート デバッグのメソッドを公開します。  
  
 `IRemoteDebugApplication` から継承するメソッドに加え、`IDebugApplication` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|アプリケーションの名前を設定します。|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|シングル ステップ実行モードの言語のエンジンが呼び出し元に返されるするプロセス デバッグ マネージャーに通知します。|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|特定の文字列をデバッガーの IDE によって表示されます。|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|1 は既にアタッチされていない場合、既定のデバッガーの IDE を起動し、このアプリケーションにデバッグ セッションをアタッチします。|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|現在のスレッドをブロックするに説明し、デバッガーのブレークポイント IDE に通知を送信します。|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|すべての参照を解放し、非アクティブ状態に入るこのアプリケーションが発生します。|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|アプリケーションの現在の中断のフラグを返します。|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|現在実行中のスレッドに関連付けられているスレッドを返します。|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|特定の同期デバッグの非同期操作へのアクセスを提供します。|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|このアプリケーションにスタック フレームの列挙子のプロバイダーを追加します。|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|このアプリケーションからスタック フレームの列挙子のプロバイダーを削除します。|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|現在実行中のスレッドがデバッガーのスレッドかどうかを判定します。|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|デバッガーのスレッドで実行されるコードに呼び出し元に機構を提供します。|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|特定の文書のプロバイダーに関連付けられた新しいアプリケーションのノードを作成します。|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|デバッガーの `IApplicationDebugger` のインターフェイスに汎用イベントを発生させます。|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|現在のスレッドをブロックするに説明し、デバッガーの IDE にエラー通知を送信します。|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Just\-In\-Time \(JIT\) のデバッガーが登録されているかどうかを判定します。|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|JIT デバッガーが自動登録済みのデバッグ中の言えないホストであるかどうかを判定します。|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|このアプリケーションにグローバル コンテキスト式のプロバイダーを追加します。|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|このアプリケーションからグローバル コンテキスト式のプロバイダーを削除します。|