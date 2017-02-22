---
title: "How to: Search for a Process in Processes View | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Processes view"
  - "processes, searching for"
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# How to: Search for a Process in Processes View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プロセス ID またはモジュールの文字列を検索条件として使用して、プロセス ビューで特定のプロセスを検索できます。  検索の最初の方向を指定することもできます。  ダイアログ ボックスのフィールドには、プロセス ツリーで選択したプロセスの属性が表示されます。  
  
### プロセス ビューでプロセスを検索するには  
  
1.  Spy\+\+ とアクティブな[プロセス ビュー](../debugger/processes-view.md) ウィンドウが表示されるように、ウィンドウの位置を調整します。  
  
2.  \[検索\] メニューの \[プロセス検索\] をクリックします。  
  
     [&#91;プロセス検索&#93; ダイアログ ボックス](../debugger/process-search-dialog-box.md)が開きます。  
  
3.  検索条件として、プロセス ID かモジュールの文字列を入力します。  
  
4.  値を指定しないフィールドは、すべて空白にします。  
  
    > [!TIP]
    >  モジュールが所有するすべてのプロセスを検索する場合は、\[プロセス\] ボックスを空白にし、\[モジュール\] ボックスにモジュール名を入力します。  次に、\[次のプロセスを検索\] を使用してプロセスの検索を続けます。  
  
5.  検索の最初の方向として、\[上へ\] または \[下へ\] を選択します。  
  
6.  **\[OK\]** をクリックします。  
  
 一致するプロセスが見つかると、それがプロセス ビュー ウィンドウで強調表示されます。