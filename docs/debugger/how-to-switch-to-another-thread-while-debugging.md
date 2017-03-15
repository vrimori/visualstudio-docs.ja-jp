---
title: "方法 : デバッグ中に別のスレッドに切り替える | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "スレッド, 切り替え [デバッグ]"
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 26
---
# 方法 : デバッグ中に別のスレッドに切り替える
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

マルチスレッド アプリケーションをデバッグするとき、いくつかある方法のうちいずれかを使用して、現在作業中のスレッドから別のスレッドにコンテキストを切り替えることができます。  
  
### \[スレッド\] ウィンドウで表示されるスレッドを切り替えるには  
  
-   スレッドをダブルクリックします。  
  
### ソース ウィンドウでスレッドを切り替えるには  
  
-   左端の余白で、スレッド インジケーターを右クリックし、**\[切り替え先\]** をポイントして、切り替え先のスレッドの名前をクリックします。  ショートカット メニューには、その場所にあるスレッドのみが表示されます。  
  
     インジケーターが表示されない場合は、**\[スレッド\]** ウィンドウを右クリックし、**\[ソースのスレッドを表示する\]** が選択されていることを確認します。  
  
### \[デバッグの場所\] ツール バーでスレッドを切り替えるには  
  
1.  **\[デバッグの場所\]** ツール バーの **\[スレッド\]** ボックスをクリックします。  
  
2.  一覧で、切り替え先のスレッドをクリックします。  
  
## 参照  
 [マルチスレッド アプリケーションのデバッグ](../debugger/debug-multithreaded-applications-in-visual-studio.md)