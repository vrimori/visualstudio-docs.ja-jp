---
title: プログラムに直接アタッチ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6885cb0dea801ab95e2e88e3f8168c139fea0e0c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100378"
---
# <a name="attaching-directly-to-a-program"></a>プログラムに直接接続
ユーザーが既に実行されている通常のプロセスでプログラムをデバッグするには、このプロセスに従います。  
  
1.  IDE では、選択、**デバッグ プロセス**コマンドを**ツール**メニュー。  
  
     **プロセス** ダイアログ ボックスが表示されます。  
  
2.  プロセスを選択し、クリックして、**アタッチ**ボタンをクリックします。  
  
     **プロセスにアタッチする** ダイアログ ボックスが表示されたら、コンピューターにインストールされているすべてのデバッグ エンジン (DEs) を一覧表示します。  
  
3.  指定を使用して、選択したプロセスをデバッグし、をクリックする DEs **OK**です。  
  
 デバッグ パッケージでは、デバッグ セッションを開始し、DEs の一覧を渡します。 デバッグ セッションは、コールバック関数を選択したプロセスをと共に、この一覧が渡されます、その実行中のプログラムを列挙するプロセスを求めます。  
  
 プログラムでは、ユーザーの要求に応答してで、デバッグ パッケージはセッション デバッグ マネージャー (SDM) をインスタンス化しを選択した DEs の一覧を渡します。 デバッグ パッケージが、SDM を渡します一覧と共に、 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)インターフェイスです。 デバッグ パッケージが選択したプロセスを呼び出すことによって DEs の一覧を渡します[IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)です。 SDM を呼び出して[IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)プロセスで実行するプログラムを列挙するポート。  
  
 この時点から、各デバッグ エンジンの詳細に説明とまったく同じプログラムにアタッチされて[、起動後にアタッチ](../../extensibility/debugger/attaching-after-a-launch.md)、2 つの例外。  
  
 効率性のため、各 DE がある一連のプログラムにアタッチできるように、DEs、SDM のアドレス空間を共有するために実装されているにグループ化されます。 この場合、 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)呼び出し[IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)し、それにアタッチするプログラムの配列を渡します。  
  
 2 つ目の例外は、既に実行されているプログラムへのアタッチ DE によって送信されたスタートアップ イベントは通常含まれていないこと、エントリ ポイント イベントです。  
  
## <a name="see-also"></a>関連項目  
 [スタートアップ イベントを起動後に送信します。](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)