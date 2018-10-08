---
title: メッセージ ビュー |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d603ad157786df756f130c3bf203961b48a610f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546998"
---
# <a name="messages-view"></a>メッセージ ビュー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[メッセージ ビュー](https://docs.microsoft.com/visualstudio/debugger/messages-view)します。  
  
各ウィンドウには、関連のメッセージ ストリームがあります。 メッセージ ビュー ウィンドウには、このメッセージのストリームが表示されます。 ウィンドウ ハンドル、メッセージのコードとメッセージが表示されます。 スレッドまたはプロセスもメッセージ ビューを作成することができます。 これにより、特定のプロセスまたはスレッドは初期化のウィンドウ メッセージをキャプチャするために特に便利ですが所有するすべてのウィンドウに送信されるメッセージを表示することができます。  
  
 以下の一般的なメッセージ ビュー ウィンドウが表示されます。 最初の列には、ウィンドウ ハンドルが含まれていますし、2 番目の列には、メッセージ コードが含まれています (で説明されている[メッセージ コード](../debugger/message-codes.md))。 デコードされたメッセージのパラメーターと戻り値が右にします。  
  
 ![Spy&#43; &#43;メッセージ ビューを](../debugger/media/spy-messagesview.png "スパイ + _MessagesView")  
Spy++ メッセージ ビュー  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>ウィンドウ、プロセス、またはスレッドのメッセージ ビューを開く  
  
1.  フォーカスを移動する、 [Windows ビュー](../debugger/windows-view.md)、[プロセス ビュー](../debugger/processes-view.md)、または[スレッド ビュー](../debugger/threads-view.md)ウィンドウ。  
  
2.  確認するメッセージが含まれる項目のノードを検索し、それを選択します。  
  
3.  **スパイ**] メニューの [選択**ログ メッセージ**します。  
  
     [メッセージ オプション ダイアログ ボックス](../debugger/message-options-dialog-box.md)が開きます。  
  
4.  メッセージを表示するためのオプションを選択します。  
  
5.  キーを押して**OK**メッセージのログ記録を開始します。  
  
     ビュー ウィンドウが開き、メッセージおよび**メッセージ**spy++ ツールバーにメニューが追加されます。 選択したオプションに応じて、メッセージは、アクティブなメッセージ ビュー ウィンドウにストリーミングを開始します。  
  
6.  十分なメッセージを使用する場合は、選択**ログの停止**から、**メッセージ**メニュー。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [メッセージ ビューを制御します。](../debugger/how-to-control-messages-view.md)  
 メッセージ ビューを管理する方法について説明します。  
  
 [メッセージ ビューでメッセージの検索](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 メッセージ ビューで、特定のメッセージを検索する方法について説明します。  
  
 [開始および停止メッセージ ログの表示](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 メッセージのログ記録の停止を起動する方法について説明します。  
  
 [メッセージ コード](../debugger/message-codes.md)  
 メッセージ ビューで表示されているメッセージのコードを定義します。  
  
 [メッセージのプロパティを表示します。](../debugger/how-to-display-message-properties.md)  
 メッセージに関する詳細情報を表示する方法。  
  
## <a name="related-sections"></a>関連項目  
 [Spy++ ビュー](../debugger/spy-increment-views.md)  
 Windows、メッセージ、プロセス、およびスレッドの spy++ ツリー ビューについて説明します。  
  
 [Spy++ の使用](../debugger/using-spy-increment.md)  
 Spy++ ツールを紹介し、使用方法について説明します。  
  
 [[メッセージ オプション] ダイアログ ボックス](../debugger/message-options-dialog-box.md)  
 メッセージがアクティブなメッセージ ビューで一覧表示を選択するために使用します。  
  
 [[メッセージ検索] ダイアログ ボックス](../debugger/message-search-dialog-box.md)  
 メッセージ ビューで特定のメッセージのノードを検索するために使用します。  
  
 [[メッセージ プロパティ] ダイアログ ボックス](../debugger/message-properties-dialog-box.md)  
 メッセージ ビューで選択したメッセージのプロパティを表示するために使用します。  
  
 [Spy++ リファレンス](../debugger/spy-increment-reference.md)  
 各 spy++ メニューおよびダイアログ ボックスについて説明するセクションが含まれています。



