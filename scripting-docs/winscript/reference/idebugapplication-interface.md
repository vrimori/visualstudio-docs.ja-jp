---
title: IDebugApplication インターフェイス |Microsoft ドキュメント
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
ms.openlocfilehash: 07964292785634212099a0bfcf8174ebb55e8713
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727442"
---
# <a name="idebugapplication-interface"></a>IDebugApplication インターフェイス
言語エンジンとホストが使用するための非リモート デバッグ メソッドを公開します。  
  
 継承されたメソッドだけでなく`IRemoteDebugApplication`、`IDebugApplication`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|アプリケーションの名前を設定します。|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|シングル ステップ モードで言語エンジンを呼び出し元に、プロセスのデバッグ マネージャーに通知します。|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|により、デバッガーの IDE に表示する特定の文字列。|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|IDE の既定のデバッガーを起動し、いずれかが既にアタッチされていない場合は、このアプリケーションにデバッグ セッションをアタッチします。|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|現在のスレッドをブロックして、デバッガーの IDE に、ブレークポイントの通知を送信します。|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|によりこのアプリケーションはすべての参照を解放し、非アクティブな状態を入力します。|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|アプリケーションの現在の区切りフラグを返します。|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|現在実行中のスレッドに関連付けられているスレッドを返します。|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|指定された同期デバッグ操作への非同期アクセスを提供します。|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|このアプリケーションには、スタック フレームの列挙子のプロバイダーを追加します。|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|このアプリケーションからのスタック フレームの列挙子のプロバイダーを削除します。|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|現在の実行中のスレッドが、デバッガー スレッドであるかどうかを判断します。|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|呼び出し元がデバッガー スレッドでコードを実行するメカニズムを提供します。|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|特定のドキュメント プロバイダーに関連付けられている新しいアプリケーション ノードを作成します。|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|デバッガーの一般的なイベントを発生させる`IApplicationDebugger`インターフェイスです。|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|現在のスレッドをブロックして、デバッガーの IDE にエラーの通知を送信します。|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|・ イン タイム (JIT) のデバッガーが登録されているかどうかを判断します。|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|JIT デバッガーが自動デバッグ ダム ホストに登録されている場合を判断します。|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|このアプリケーションにグローバル式のコンテキスト プロバイダーを追加します。|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|このアプリケーションからのグローバル式のコンテキスト プロバイダーを削除します。|