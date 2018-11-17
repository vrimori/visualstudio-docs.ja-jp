---
title: 割り当てフック関数 |Microsoft Docs
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
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d201f22d461a04890899ac1cebc177cb1521555
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743346"
---
# <a name="allocation-hook-functions"></a>割り当てフック関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用してインストール、割り当てフック関数[_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d)メモリを割り当て、再割り当て、または解放するたびに呼び出されます。 この種のフック関数はさまざまな目的に利用できます。 たとえば、メモリ不足の状態でアプリケーションの動作をテストしたり、割り当てパターンを調査したり、後から分析するために割り当て情報を記録したりなどの目的に利用できます。  
  
> [!NOTE]
>  説明されている、割り当てフック関数での C ランタイム ライブラリ関数の使用に関する制限に注意してください。[割り当てフック関数と C ランタイムのメモリ割り当て](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)します。  
  
 割り当て用のフック関数には、次のようなプロトタイプが必要です。  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 渡すポインター [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d)の種類は **_CRT_ALLOC_HOOK**CRTDBG で定義されている、します。H:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 ランタイム ライブラリは、フック関数を呼び出すときに、 *nAllocType*引数は、どのような割り当てを示します操作の実行 (**_HOOK_ALLOC**、 **_HOOK_REALLOC**、または。**_HOOK_FREE**)。 メモリの解放または再割り当ての場合、引数 `pvData` には、解放されるブロックへのポインターが格納されます。 一方、割り当ての場合は、まだ割り当てが行われていないため、このポインターは null になります。 その他の引数には、必要に応じて、対象ブロックの割り当てサイズ、ブロック型、順番に付けられた割り当て要求番号、割り当てが行われた場所のファイル名と行番号へのポインターが格納されます。 フック関数がどのような分析を実行すると、他のタスクをいずれかを返す必要が**TRUE**、割り当て処理を継続できることを示すまたは**FALSE**を示しますが、操作が失敗する必要があります。 この種類の簡単なフック可能性がありますこれまでに割り当てられたメモリの容量を確認し、返す**FALSE**その量は、小規模の制限を超えた場合。 この関数を使用すると、メモリがかなり不足している場合だけに発生するメモリ割り当てエラーを意図的に発生させることができます。 さらに複雑なフック関数としては、割り当てパターンを追跡したり、メモリの使用状況を分析したり、特定の状態が発生したときにレポートを作成したりする関数が考えられます。  
  
## <a name="see-also"></a>関連項目  
 [割り当てフック関数と C ランタイムのメモリ割り当て](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [デバッグ用フック関数の作成](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 サンプル](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



