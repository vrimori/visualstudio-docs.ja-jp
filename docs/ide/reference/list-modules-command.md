---
title: "List Modules コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listmodules"
helpviewer_keywords: 
  - "Debug.ListModules コマンド"
  - "モジュールの一覧表示コマンド"
  - "ListModules コマンド"
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# List Modules コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

現在のプロセスのモジュールが一覧表示されます。  
  
## 構文  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### パラメーター  
 \/Address:`yes|no`  
 省略可能です。  モジュールのメモリ アドレスを表示するかどうかを指定します。  既定値は `yes`です。  
  
 \/Name:`yes|no`  
 省略可能です。  モジュールの名前を表示するかどうかを指定します。  既定値は `yes`です。  
  
 \/Order:`yes|no`  
 省略可能です。  モジュールの順序を表示するかどうかを指定します。  既定値は `no`です。  
  
 \/Path:`yes|no`  
 省略可能です。  モジュールのパスを表示するかどうかを指定します。  既定値は `yes`です。  
  
 \/Process:`yes|no`  
 省略可能です。  モジュールのプロセスを表示するかどうかを指定します。  既定値は `no`です。  
  
 \/SymbolFile:`yes|no`  
 省略可能です。  モジュールのシンボル ファイルを表示するかどうかを指定します。  既定値は `no`です。  
  
 \/SymbolStatus:`yes|no`  
 省略可能です。  モジュールのシンボル ステータスを表示するかどうかを指定します。  既定値は `yes`です。  
  
 \/Timestamp:`yes|no`  
 省略可能です。  モジュールのタイムスタンプを表示するかどうかを指定します。  既定値は `no`です。  
  
 \/Version:`yes|no`  
 省略可能です。  モジュールのバージョンを表示するかどうかを指定します。  既定値は `no`です。  
  
## 解説  
  
## 使用例  
 この例では、現在のプロセスのモジュール名、アドレス、およびタイムスタンプを一覧表示します。  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [方法 : \[モジュール\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Modules%20Window.md)