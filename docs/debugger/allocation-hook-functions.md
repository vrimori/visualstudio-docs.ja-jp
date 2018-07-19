---
title: 割り当てフック関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c8a051641811da3658ffe556982c67649704069
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433357"
---
# <a name="allocation-hook-functions"></a>割り当てフック関数
使用してインストール、割り当てフック関数[_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)メモリを割り当て、再割り当てまたは解放するたびに呼び出されます。 さまざまな目的は、この種のフック関数を使用できます。 テスト方法、アプリケーションが処理メモリ不足の状況など、割り当てパターンを調査するには使用または後で分析割り当て情報を記録します。  
  
> [!NOTE]
>  説明されている、割り当てフック関数での C ランタイム ライブラリ関数の使用に関する制限に注意してください。[割り当てフック関数と C ランタイムのメモリ割り当て](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)します。  
  
 割り当てフック関数は、次の例のようなプロトタイプが必要です。  
  
```cpp
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 渡すポインター [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)の種類は **_CRT_ALLOC_HOOK**CRTDBG で定義されている、します。H:  
  
```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 ランタイム ライブラリは、フック関数を呼び出すときに、 *nAllocType*引数は、どのような割り当てを示します操作ができるようにしようとしています (**_HOOK_ALLOC**、 **_HOOK_REALLOC**、または。**_HOOK_FREE**)。 無料または再割り当て、`pvData`が解放されるブロックのユーザーの記事へのポインター。 ただし、割り当ての this ポインターが null、割り当てが発生していないためです。 残りの引数には、割り当てのサイズには、問題のブロックの型、およびファイル名へのポインターに関連付けられているシーケンシャル要求番号が含まれています。 可能な場合、引数には割り当てが行われた行番号も含まれます。 フック関数がどのような分析を実行すると、他のタスクをいずれかを返す必要が**TRUE**、割り当て処理を継続できることを示すまたは**FALSE**を示しますが、操作が失敗する必要があります。 この種類の簡単なフック可能性がありますこれまでに割り当てられたメモリの容量を確認し、返す**FALSE**その量は、小規模の制限を超えた場合。 この関数を使用すると、メモリがかなり不足している場合だけに発生するメモリ割り当てエラーを意図的に発生させることができます。 さらに複雑なフック関数としては、割り当てパターンを追跡したり、メモリの使用状況を分析したり、特定の状態が発生したときにレポートを作成したりする関数が考えられます。  
  
## <a name="see-also"></a>関連項目  
 [割り当てフック関数と C ランタイムのメモリ割り当て](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [デバッグ用フック関数の作成](../debugger/debug-hook-function-writing.md)   
