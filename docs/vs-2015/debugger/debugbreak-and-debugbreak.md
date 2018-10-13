---
title: DebugBreak と _ _debugbreak |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DebugBreak
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 73b818269695322d06c95e5ae39f5bdfd7059dae
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281113"
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak と __debugbreak
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DebugBreak Win32 関数を呼び出すことができます、または[_ _debugbreak](http://msdn.microsoft.com/library/1d1e1c0c-891a-4613-ae4b-d790094ba830)コード内の任意の時点で組み込み。 `DebugBreak` および `__debugbreak` を呼び出した場合の動作は、その位置にブレークポイントを設定した場合と同様です。  
  
 `DebugBreak` はシステム関数の呼び出しであるため、システム デバッグ シンボルをインストールして、中断の後に正しい呼び出し履歴情報が表示されるようにする必要があります。 そうしなかった場合、デバッガーによって表示される呼び出し履歴情報は、1 フレームずれて表示されることがあります。 `__debugbreak` を使用した場合、シンボルは不要です。  
  
## <a name="see-also"></a>関連項目  
 [コンパイラの組み込み](http://msdn.microsoft.com/library/48bb9929-7d78-4fd8-a092-ae3c9f971858)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)   
 [シンボルとソース コードの管理](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)



