---
title: "Windows スクリプト ホスト | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows スクリプト ホスト, 実装 (ホストを)"
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Windows スクリプト ホスト
Microsoft Windows のスクリプトのホストを実行すると、安全にホストが次の処理を行う間だけスクリプト エンジンが基本スレッドのコンテキストで [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) のインターフェイスを呼び出すとする:  
  
-   基本スレッド \(一般に、メッセージ ループを含むスレッド\) を選択します。  
  
-   基本スレッドのスクリプト エンジンをインスタンス化します。  
  
-   [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) と [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md)の状況では特に、許可する基本スレッドからのみ呼び出しのスクリプト エンジンのメソッド、います。  
  
-   基本スレッドからのみスクリプト エンジンのディスパッチ オブジェクトを呼び出します。  
  
-   ウィンドウ ハンドルが提供された場合は基本スレッドのメッセージ ループの実行を確認します。  
  
-   、ホストのオブジェクト モデルの基本スレッドのソース イベントのオブジェクトだけを確認します。  
  
 これらの規則は、すべてのシングルスレッド ホストに自動的に表示されます。  上記の制限されたモデルは完全に意図的に Loose はホストがスタックしたスクリプトを別のスレッドからの [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) \(CTRL\+BREAK のハンドラーまたは LIKE による\) 呼び出すことによって中断、[IActiveScript::Clone](../winscript/reference/iactivescript-clone.md)を使用して新しいスレッドのスクリプトを複製するようにするには。  
  
## 解説  
 これらの制限がない場合 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) のフリー スレッド インターフェイス、およびフリー スレッド オブジェクト モデルを実装するために選択するホストには適用されません。  このようなホストは無制限に、すべてのスレッドからの [IActiveScript](../winscript/reference/iactivescript.md) のインターフェイスを使用できます。  
  
## 参照  
 [\<PAVE OVER\> Microsoft Windows スクリプト インターフェイス \- 概要](../Topic/%3CPAVE%20OVER%3E%20Microsoft%20Windows%20Script%20Interfaces%20-%20Introduction.md)