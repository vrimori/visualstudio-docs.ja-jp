---
title: "スタック フレーム |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2b225d84bfae6d182da86b2878a3761f67572be
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="stack-frames"></a>スタック フレーム
デバッガーのアーキテクチャの観点から、**スタック フレーム**:  
  
-   スレッドの実行コンテキストを提供するスタックの抽象です。 スレッドは、関数内で常に実行します。 スタック フレームは、ことへの関数、および引数のローカル変数を保持します。 を Visual Studio でデバッグするために、言語、またはデバッグされている環境は、スタック フレームをサポートする必要があります。  
  
-   どちらも識別自己記述し、関連付けられたスレッドを返すことができます。 スタック フレームには、現在の命令ポインターだけでなく、関連するドキュメントを表す、コードのコンテキストや式の評価コンテキストを返すこともできます。  
  
-   名前、型、およびローカル変数と引数の値を記述して、さまざまな IDE デバッグ ウィンドウに表示されるプロパティがあります。  
  
-   によって表される、 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)インターフェイス、通常、デバッグ エンジン (DE) またはスレッドを実行する対象の仮想マシンによって作成します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)