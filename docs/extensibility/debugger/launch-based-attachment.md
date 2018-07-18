---
title: 添付ファイルの起動に基づく |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 892518cc92286f9415e39c96b6ed2afa8eb0d792
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099377"
---
# <a name="launch-based-attachment"></a>添付ファイルの起動に基づく
プログラムを起動ベースの添付ファイルは自動です。 プログラムをホストしているプロセスを開始するには、SDM によって、起動ベースの添付ファイルは手動の添付ファイルのメソッドと同様のパスに従います。 詳細については、次を参照してください。[プログラムへのアタッチ](../../extensibility/debugger/attaching-to-the-program.md)です。  
  
## <a name="the-attaching-process"></a>プロセスを接続します。  
 主な違いは次のイベントの順序、**アタッチ**を呼び出すと、次のようにします。  
  
1.  送信、 **IDebugEngineCreateEvent2** SDM にイベント オブジェクトです。 詳細については、「[送信イベント](../../extensibility/debugger/sending-events.md)です。  
  
2.  呼び出す、`IDebugProgram2::GetProgramId`メソッドを**IDebugProgram2**に渡されたインターフェイス、**アタッチ**メソッドです。  
  
3.  送信、 **IDebugProgramCreateEvent2** 、SDM に通知するイベント オブジェクトをローカル**IDebugProgram2**デにプログラムを表すオブジェクトが作成されました。  
  
4.  送信、 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)に起動されたプロセスに対して新しいスレッドを作成する、SDM を通知するイベント オブジェクトです。  
  
## <a name="see-also"></a>関連項目  
 [必要なイベントを送信します。](../../extensibility/debugger/sending-the-required-events.md)   
 [デバッグするプログラムの有効化](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)