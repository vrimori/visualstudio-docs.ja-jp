---
title: IDebugApplication インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3483bea94d7a53fabf3f552df97a681307b885c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349726"
---
# <a name="idebugapplication-interface"></a>IDebugApplication インターフェイス
言語エンジンとホストで使用するための非リモート デバッグ メソッドを公開します。  
  
 継承されたメソッドだけでなく`IRemoteDebugApplication`、`IDebugApplication`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|アプリケーションの名前を設定します。|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|シングル ステップ モードで、言語エンジンがその呼び出し元に戻ることをプロセス デバッグ マネージャーに通知します。|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|デバッガー IDE に表示する、指定した文字列をによりします。|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|IDE の既定のデバッガーを起動し、既にアタッチされていない場合、このアプリケーションでは、デバッグ セッションをアタッチします。|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|現在のスレッドをブロックして、デバッガー IDE にブレークポイントの通知を送信します。|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|によりこのアプリケーションはすべての参照を解放し、非アクティブな状態を入力します。|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|アプリケーションの現在の区切りフラグを返します。|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|現在実行中のスレッドに関連付けられたスレッドを返します。|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|指定された同期デバッグ操作への非同期アクセスを提供します。|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|このアプリケーションには、スタック フレームの列挙子のプロバイダーを追加します。|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|このアプリケーションからのスタック フレームの列挙子のプロバイダーを削除します。|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|現在の実行中のスレッドがデバッガー スレッドであるかどうかを判断します。|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|呼び出し元が、デバッガー スレッドでコードを実行するためのメカニズムを提供します。|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|特定のドキュメント プロバイダーに関連付けられたアプリケーションの新しいノードを作成します。|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|デバッガーの一般的なイベントが発生した`IApplicationDebugger`インターフェイス。|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|現在のスレッドをブロックして、デバッガー IDE にエラーの通知を送信します。|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|ジャストイン タイム (JIT) デバッガーが登録されているかどうかを決定します。|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|JIT デバッガーが自動デバッグ ダム ホストに登録されている場合を決定します。|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|このアプリケーションには、グローバルな式のコンテキスト プロバイダーを追加します。|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|このアプリケーションからは、グローバルな式のコンテキスト プロバイダーを削除します。|