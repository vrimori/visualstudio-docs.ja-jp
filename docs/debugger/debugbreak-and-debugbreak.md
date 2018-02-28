---
title: "DebugBreak と _ _debugbreak |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 83128e4d5bd274013db1e7195e8182d021c257d5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak と __debugbreak
DebugBreak Win32 関数を呼び出すことができます、または[_ _debugbreak](/cpp/intrinsics/debugbreak)コード内の任意の時点で組み込みです。 `DebugBreak` および `__debugbreak` を呼び出した場合の動作は、その位置にブレークポイントを設定した場合と同様です。  
  
 `DebugBreak` はシステム関数の呼び出しであるため、システム デバッグ シンボルをインストールして、中断の後に正しい呼び出し履歴情報が表示されるようにする必要があります。 そうしなかった場合、デバッガーによって表示される呼び出し履歴情報は、1 フレームずれて表示されることがあります。 `__debugbreak` を使用した場合、シンボルは不要です。  
  
## <a name="see-also"></a>参照  
 [コンパイラ組み込み関数](/cpp/intrinsics/compiler-intrinsics)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)   
 [シンボル (.pdb) を指定して、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)