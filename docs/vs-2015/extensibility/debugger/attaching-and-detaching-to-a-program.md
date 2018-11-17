---
title: アタッチとデタッチ プログラム |Microsoft Docs
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
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b6bba6600d3ea32073a908199f5cd6ddaa33ef9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762794"
---
# <a name="attaching-and-detaching-to-a-program"></a>プロジェクトへのアタッチとデタッチ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

デバッガーをアタッチするには、メソッドおよび適切な属性を持つイベントの適切なシーケンスを送信する必要があります。  
  
## <a name="sequence-of-methods-and-events"></a>メソッドとイベントのシーケンス  
  
1. セッション デバッグ マネージャー (SDM) を呼び出す、 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)メソッド。  
  
    デバッグ エンジン (DE) のプロセス モデルに基づく、`IDebugProgramNodeAttach2::OnAttach`メソッドは、次の動作を決定するメソッドを次のいずれかを返します。  
  
    場合`S_FALSE`デバッグ エンジンは、プログラムに正常に関連付けられている、返されます。 それ以外の場合、[アタッチ](../../extensibility/debugger/reference/idebugengine2-attach.md)アタッチ プロセスを完了するメソッドが呼び出されます。  
  
    場合`S_OK`が返されます、DE、SDM と同じプロセスに読み込まれます。 SDM は、次のタスクを実行します。  
  
   1.  呼び出し[GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) DE のエンジンの情報を取得します。  
  
   2.  併置デを作成します。  
  
   3.  呼び出し[アタッチ](../../extensibility/debugger/reference/idebugengine2-attach.md)します。  
  
2. DE 送信、 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)に SDM を`EVENT_SYNC`属性。  
  
3. DE 送信、 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)に SDM を`EVENT_SYNC`属性。  
  
4. DE 送信、 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)に SDM を`EVENT_SYNC_STOP`属性。  
  
   プログラムからデタッチ単純な 2 段階のプロセスのとおりです。  
  
5. SDM コール[デタッチ](../../extensibility/debugger/reference/idebugprogram2-detach.md)します。  
  
6. DE 送信、 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのイベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)

