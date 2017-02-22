---
title: "Processes View | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.externaltools.spyplus.processesview"
helpviewer_keywords: 
  - "Processes view"
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Processes View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プロセス ビューには、システム上でアクティブなすべてのプロセスのツリーが表示されます。  プロセス ID とモジュール名が表示されます。  特定のシステム プロセスを調べるには、プロセス ビューを使用してください。通常、システム プロセスは実行中のプログラムに対応します。  プロセスはモジュール名で識別されます。または、"システム プロセス" と指定されます。  
  
 Microsoft Windows は複数のプロセスをサポートします。  各プロセスは 1 つ以上のスレッドから構成でき、各スレッドには 1 つ以上のトップレベルのウィンドウを関連付けることができます。  それぞれのトップレベルのウィンドウは、一連のウィンドウを所有できます。  \+ 記号は、レベルが折りたたまれていることを示します。  折りたたまれたビューは、プロセスごとに 1 つの行から構成されます。  レベルを展開するには、\+ 記号をクリックします。  
  
 特定のシステム プロセスを調べるには、プロセス ビューを使用してください。通常、システム プロセスは実行中のプログラムに対応します。  プロセスはモジュール名で識別されます。または、"システム プロセス" と指定されます。プロセスを見つけるには、ツリーを折りたたみ、リストを検索します。  
  
## 手順  
  
#### プロセス ビューを開くには  
  
1.  \[スパイ\] メニューの \[プロセス\] をクリックします。  
  
 ![Spy&#43;&#43; プロセス ビュー](../debugger/media/spy--_processes.png "Spy\+\+\_Processes")  
Spy\+\+ プロセス ビュー  
  
 上の図に示されているのは、プロセス ノードとスレッド ノードが展開されている状態のプロセス ビューです。  
  
### このセクションの内容  
 [プロセス ビューでのプロセスの検索](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 プロセス ビューで特定のプロセスを検索する方法について説明します。  
  
 [プロセス プロパティの表示](../debugger/how-to-display-process-properties.md)  
 メッセージの詳細情報を表示する方法について説明します。  
  
### 関連項目  
 [Spy\+\+ ビュー](../debugger/spy-increment-views.md)  
 ウィンドウ、メッセージ、プロセス、およびスレッドの Spy\+\+ ツリー ビューについて説明します。  
  
 [Spy\+\+ の使用](../debugger/using-spy-increment.md)  
 Spy\+\+ ツールとその使用方法について説明します。  
  
 [&#91;プロセス検索&#93; ダイアログ ボックス](../debugger/process-search-dialog-box.md)  
 プロセス ビューで特定のプロセスのノードを検索するために使用します。  
  
 [&#91;プロセス プロパティ&#93; ダイアログ ボックス](../debugger/process-properties-dialog-box.md)  
 プロセス ビューで選択したプロセスのプロパティを表示します。  
  
 [Spy\+\+ リファレンス](../debugger/spy-increment-reference.md)  
 Spy\+\+ の各メニューとダイアログ ボックスについて説明するセクションが含まれます。