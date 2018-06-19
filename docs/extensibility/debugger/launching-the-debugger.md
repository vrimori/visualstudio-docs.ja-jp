---
title: デバッガーを起動 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 2606e0f6c7d5dfe17e4c82528c36b3f7cdc26c5e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108931"
---
# <a name="launching-the-debugger"></a>デバッガーを起動します。
デバッガーを起動するには、正しい順序のメソッドとその適切な属性を持つイベントを送信する必要があります。  
  
## <a name="sequences-of-methods-and-events"></a>メソッドとイベントのシーケンス  
  
1.  選択して、セッション デバッグ マネージャー (SDM) が呼び出されます、**デバッグ**メニューをクリックして**開始**です。 参照してください[プログラムの起動](../../extensibility/debugger/launching-a-program.md)詳細についてはします。  
  
2.  SDM 呼び出し[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)メソッドです。  
  
3.  デバッグ エンジン (DE) のプロセス モデルに基づいて、`IDebugProgramNodeAttach2::OnAttach`メソッドでは、次の動作を決定するメソッドを次のいずれかを返します。  
  
     場合`S_FALSE`が返されます、デバッグ エンジン (DE) 中、仮想マシンに読み込まれる。  
  
     - または -  
  
     場合`S_OK`DE が読み込まれるには、返される、SDM の処理中です。 SDM には、次のタスクを実行します。  
  
    1.  呼び出し[GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)デのエンジンの情報を取得します。  
  
    2.  併置デを作成します。  
  
    3.  呼び出し[アタッチ](../../extensibility/debugger/reference/idebugengine2-attach.md)です。  
  
4.  DE 送信、 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)で SDM を`EVENT_SYNC`属性。  
  
5.  DE 送信、 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)で SDM を`EVENT_SYNC`属性。  
  
6.  DE 送信、 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)で SDM を`EVENT_SYNC`属性。  
  
7.  DE 送信、 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)で SDM を`EVENT_SYNC`属性。  
  
8.  DE 送信、 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)で SDM を`EVENT_SYNC`属性。  
  
## <a name="see-also"></a>関連項目  
 [呼び出し元のデバッガー イベント](../../extensibility/debugger/calling-debugger-events.md)   
 [プログラムの起動](../../extensibility/debugger/launching-a-program.md)