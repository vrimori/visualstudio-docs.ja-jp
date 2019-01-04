---
title: デバッガーの起動 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d1c1ba42d1d05217eff6e8ff7a0b6f1209a05db
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990884"
---
# <a name="launch-the-debugger"></a>デバッガーを起動します。
デバッガーを起動するには、メソッドおよびイベントの適切な属性の適切なシーケンスを送信する必要があります。  
  
## <a name="sequences-of-methods-and-events"></a>メソッドとイベントのシーケンス  
  
1.  セッション デバッグ マネージャー (SDM) が選択することによって呼び出される、**デバッグ**メニューをクリックして**開始**します。 詳細については、次を参照してください。 [、プログラムを起動](../../extensibility/debugger/launching-a-program.md)します。  
  
2.  SDM コール[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)メソッド。  
  
3.  デバッグ エンジン (DE) のプロセス モデルに基づく、`IDebugProgramNodeAttach2::OnAttach`メソッドは、次の動作を決定するメソッドを次のいずれかを返します。  
  
     場合`S_FALSE`、仮想マシンを処理中に読み込まれるデバッグ エンジン (DE) を返します。  
  
     または  
  
     場合`S_OK`DE の読み込みが戻る、SDM のプロセスにします。 SDM には、次のタスクを実行します。  
  
    1.  呼び出し[GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) DE のエンジンの情報を取得します。  
  
    2.  併置デを作成します。  
  
    3.  呼び出し[アタッチ](../../extensibility/debugger/reference/idebugengine2-attach.md)します。  
  
4.  DE 送信、 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)に SDM を`EVENT_SYNC`属性。  
  
5.  DE 送信、 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)に SDM を`EVENT_SYNC`属性。  
  
6.  DE 送信、 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)に SDM を`EVENT_SYNC`属性。  
  
7.  DE 送信、 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)に SDM を`EVENT_SYNC`属性。  
  
8.  DE 送信、 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)に SDM を`EVENT_SYNC`属性。  
  
## <a name="see-also"></a>関連項目  
 [デバッガー イベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)   
 [プログラムの起動](../../extensibility/debugger/launching-a-program.md)