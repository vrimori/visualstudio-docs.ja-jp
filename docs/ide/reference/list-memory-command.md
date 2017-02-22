---
title: "ListMemory コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listmemory"
helpviewer_keywords: 
  - "Debug.ListMemory コマンド"
  - "メモリの一覧表示コマンド"
  - "ListMemory コマンド"
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ListMemory コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定範囲のメモリの内容を表示します。  
  
## 構文  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## 引数  
 `expression`  
 省略可能です。  メモリの表示を開始するメモリ アドレス。  
  
## スイッチ  
 \/ANSI&#124;Unicode  
 省略可能です。  メモリの内容を、メモリ バイトに対応する ANSI 文字または Unicode 文字にして表示します。  
  
 \/Count:`number`  
 省略可能です。  表示するメモリを `expression` からのバイト数で指定します。  
  
 \/Format:`formattype`  
 省略可能です。  **\[メモリ\]** ウィンドウにメモリ情報を表示するときの形式を指定します。\[1 バイト\]、\[2 バイト\]、\[4 バイト\]、\[8 バイト\]、\[浮動小数点型\] \(32 ビット\)、または \[倍精度浮動小数点型\] \(64 ビット\) のいずれかです。  \[1 バイト\] を使用する場合、`/Unicode` は使用できません。  
  
 \/Hex&#124;Signed&#124;Unsigned  
 省略可能です。  数字の表示形式を、符号付き、符号なし、または 16 進のいずれかに指定します。  
  
## 解説  
 すべてのスイッチを付けて **Debug.ListMemory** コマンドを完全に記述する代わりに、指定の値を設定するための特定のスイッチがあらかじめ定義されたエイリアスを使用してコマンドを起動することもできます。  次に例を示します。  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
 上のコードの代わりに、次のように入力できます。  
  
```  
>df /Count:30 /Unicode  
```  
  
 **Debug.ListMemory** コマンドで使用できるエイリアスの一覧を次に示します。  
  
|Alias|コマンドおよびスイッチ|  
|-----------|-----------------|  
|**d**|Debug.ListMemory|  
|**da**|Debug.ListMemory \/Ansi|  
|**db**|Debug.ListMemory \/Format:OneByte|  
|**dc**|Debug.ListMemory \/Format:FourBytes \/Ansi|  
|**dd**|Debug.ListMemory \/Format:FourBytes|  
|**df**|Debug.ListMemory \/Format:Float|  
|**dq**|Debug.ListMemory \/Format:EightBytes|  
|**du**|Debug.ListMemory \/Unicode|  
  
## 使用例  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## 参照  
 [ListCallStack コマンド](../../ide/reference/list-call-stack-command.md)   
 [ListThreads コマンド](../../ide/reference/list-threads-command.md)   
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)