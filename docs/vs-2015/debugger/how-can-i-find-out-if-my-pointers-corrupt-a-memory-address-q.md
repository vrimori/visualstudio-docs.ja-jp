---
title: ポインターがメモリ アドレスを破壊しているかどうか見つけるには | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04df8c5dfc0d6fbf57183cf90ab0fd8a4fc79686
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49217326"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>ポインターがメモリ アドレスを破壊しているかどうか見つけるには
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

問題の説明  
 ポインターの 1 つがアドレス 0x00408000 のメモリを破壊してしまったようです。 どうなっているのか調べる方法はありますか。  
  
## <a name="solution"></a>ソリューション  
  
#### <a name="check-for-heap-corruption"></a>ヒープ破損のチェック  
  
-   メモリの破損は、その多くがヒープの破損に起因します。 グローバル フラグ ユーティリティ (gflags.exe) または pageheap.exe を使用してください。 参照してください[ http://support.microsoft.com/default.aspx?scid=kb; en-ご; 286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470)します。  
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>メモリ アドレスの変更箇所を見つけるには  
  
1.  0x00408000 にデータ ブレークポイントを設定します。 参照してください[データ変更ブレークポイントを設定 (ネイティブ C++ のみ)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only)します。  
  
2.  ブレークポイントがヒットしたらを使用して、**メモリ**0x00408000 から始まるメモリを表示するウィンドウの内容します。 詳細については、次を参照してください。[メモリ Windows](../debugger/memory-windows.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグに関する Faq](../debugger/debugging-native-code-faqs.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)



