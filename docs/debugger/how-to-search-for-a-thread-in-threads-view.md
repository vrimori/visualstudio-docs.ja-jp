---
title: "How to: Search for a Thread in Threads View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threads, searching"
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Search for a Thread in Threads View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

スレッド ID またはモジュールの文字列を検索条件として使用して、スレッド ビューで特定のスレッドを検索できます。  検索の最初の方向を指定することもできます。  ダイアログ ボックスのフィールドには、スレッド ツリーで選択したスレッドの属性が表示されます。  
  
### スレッド ビューでスレッドを検索するには  
  
1.  Spy\+\+ とアクティブな[スレッド ビュー](../debugger/threads-view.md) ウィンドウが表示されるように、ウィンドウの位置を調整します。  
  
2.  \[検索\] メニューの \[スレッド検索\] をクリックします。  
  
     [&#91;スレッド検索&#93; ダイアログ ボックス](../debugger/thread-search-dialog-box.md)が開きます。  
  
3.  検索条件として、スレッド ID かモジュールの文字列を入力します。  
  
4.  値を指定しないフィールドは、すべて空白にします。  
  
    > [!TIP]
    >  モジュールが所有するすべてのスレッドを検索する場合は、\[スレッド\] ボックスを空白にし、\[モジュール\] ボックスにモジュール名を入力します。  次に、\[次のスレッドを検索\] を使用してスレッドの検索を続けます。  
  
5.  検索の最初の方向として、\[上へ\] または \[下へ\] を選択します。  
  
6.  **\[OK\]** をクリックします。  
  
 一致するスレッドが見つかると、それがスレッド ビュー ウィンドウで強調表示されます。