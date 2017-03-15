---
title: "ポインターがメモリ アドレスを破壊しているかどうか見つけるには | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
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
  - "C++"
helpviewer_keywords: 
  - "アドレス, メモリ アドレス破損の原因となっているポインター"
  - "破損したメモリ アドレス"
  - "デバッグ [C++], メモリの破損"
  - "メモリ アドレスの破損 (ポインターによる)"
  - "メモリ, 破損"
  - "ポインター, 破損 (メモリ アドレスを)"
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ポインターがメモリ アドレスを破壊しているかどうか見つけるには
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## 問題の説明  
 ポインターの 1 つがアドレス 0x00408000 のメモリを破壊してしまったようです。  どうなっているのか調べる方法はありますか。  
  
## 解決方法  
  
#### ヒープ破損のチェック  
  
-   メモリの破損は、その多くがヒープの破損に起因します。  グローバル フラグ ユーティリティ \(gflags.exe\) または pageheap.exe を使用してください。  [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470) を参照してください。  
  
#### メモリ アドレスの変更箇所を見つけるには  
  
1.  0x00408000 にデータ ブレークポイントを設定します。  「[データ変更ブレークポイントを設定する \(ネイティブ C\+\+ のみ\)](../debugger/using-breakpoints.md#BKMK_Set_a_data_change_breakpoint__native_C___only_)」を参照してください。  
  
2.  ブレークポイントにヒットしたら、**\[メモリ\]** ウィンドウを使用して、0x00408000 から始まるメモリの内容を表示します。  詳細については、「[\[メモリ\] ウィンドウ](../Topic/Memory%20Windows.md)」を参照してください。  
  
## 参照  
 [ネイティブ コードのデバッグに関する FAQ](../debugger/debugging-native-code-faqs.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)