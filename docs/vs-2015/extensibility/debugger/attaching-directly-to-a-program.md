---
title: 直接プログラムへのアタッチ |Microsoft Docs
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
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de07b2fc8846bd24bb3e4483c78eb339d9d49e4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817549"
---
# <a name="attaching-directly-to-a-program"></a>プログラムへ直接アタッチする
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

通常は既に実行されているプロセスでプログラムをデバッグする必要のあるユーザーでは、このプロセスに従います。  
  
1. IDE では、選択、**デバッグ プロセス**コマンドから、**ツール**メニュー。  
  
    **[プロセス]** ダイアログ ボックスが表示されます。  
  
2. プロセスを選択およびクリックして、**アタッチ**ボタンをクリックします。  
  
    **プロセスにアタッチ** ダイアログ ボックスが表示されたら、コンピューターにインストールされたすべてのデバッグ エンジン (DEs) を一覧表示します。  
  
3. 指定を使用して、選択したプロセスをデバッグおよびクリックして DEs **OK**します。  
  
   デバッグ パッケージは、デバッグ セッションを開始し、DEs の一覧を渡します。 デバッグ セッションを選択したプロセスへのコールバック関数と共に、このリストを渡しのその実行中のプログラムを列挙するプロセスを尋ねます。  
  
   プログラムでは、ユーザー要求に応答してで、デバッグ パッケージはセッション デバッグ マネージャー (SDM) をインスタンス化して、選択した DEs の一覧を渡します。 デバッグ パッケージは、リスト、および、SDM を渡す、 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)インターフェイス。 呼び出してデバッグ パッケージが選択したプロセスに DEs の一覧を渡します[IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)します。 SDM を呼び出して[IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)プロセスで実行されているプログラムを列挙するポート。  
  
   」で詳しく説明とまったく同じプログラムにこの時点から各デバッグ エンジンが接続されている[、起動後にアタッチ](../../extensibility/debugger/attaching-after-a-launch.md)、2 つの例外。  
  
   効率性のため、各 DE がある一連のプログラムに接続できるように、DEs、SDM とアドレス空間を共有する実装されているにグループ化されます。 この場合、 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)呼び出し[IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)し、それにアタッチするプログラムの配列を渡します。  
  
   2 つ目の例外は、スタートアップ イベントが既に実行されているプログラムにアタッチ DE によって送信されるは通常含まれていないこと、エントリ ポイント イベントです。  
  
## <a name="see-also"></a>関連項目  
 [起動の後のスタートアップ イベントを送信します。](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)

