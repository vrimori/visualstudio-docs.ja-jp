---
title: 添付ファイルの起動に基づく |Microsoft Docs
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
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3603f14d07eb8531480b89f24d73cbd5045da7c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188308"
---
# <a name="launch-based-attachment"></a>起動ベースのアタッチ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

プログラムを起動ベースの添付ファイルは自動です。 によって、SDM をプログラムをホストするプロセスを起動すると起動ベースの添付ファイルは手動の添付ファイルのメソッドのようなパスに従います。 詳しくは、次を参照してください。[プログラムへのアタッチ](../../extensibility/debugger/attaching-to-the-program.md)します。  
  
## <a name="the-attaching-process"></a>プロセスを接続します。  
 主な違いは、次のイベントのシーケンス、**アタッチ**呼び出すと、次のようにします。  
  
1.  送信、 **IDebugEngineCreateEvent2** SDM にイベント オブジェクト。 詳細については、次を参照してください。[イベントの送信](../../extensibility/debugger/sending-events.md)します。  
  
2.  呼び出す、`IDebugProgram2::GetProgramId`メソッドを**IDebugProgram2**に渡されたインターフェイス、**アタッチ**メソッド。  
  
3.  送信、 **IDebugProgramCreateEvent2** 、SDM を通知するイベント オブジェクトをローカル**IDebugProgram2** DE にプログラムを表現するオブジェクトが作成されました。  
  
4.  送信、 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) SDM を起動したプロセスに、新しいスレッドを作成することを通知するイベント オブジェクト。  
  
## <a name="see-also"></a>関連項目  
 [必要なイベントを送信します。](../../extensibility/debugger/sending-the-required-events.md)   
 [デバッグするプログラムの有効化](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

