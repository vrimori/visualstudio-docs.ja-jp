---
title: スタック フレーム |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35b22c47aa80713ae494f868996142e776c94a0a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020336"
---
# <a name="stack-frames"></a>スタック フレーム
デバッガーのアーキテクチャで、*スタック フレーム*:  
  
-   スレッドの実行コンテキストを提供するスタックの抽象化です。 スレッドは、関数内で常に実行されます。 スタック フレームをローカル変数、関数の引数を保持します。 を Visual Studio でデバッグするために、言語またはデバッグ中の環境は、スタック フレームをサポートする必要があります。  
  
-   両方を特定し、それ自体を記述および関連付けられたスレッドを返すことができます。 スタック フレームでは、現在の命令ポインターと関連付けられているドキュメントを表す、コードのコンテキストや式の評価コンテキストを返すこともできます。  
  
-   名前、種類、およびローカル変数と引数の値を記述して、さまざまな IDE のデバッグ ウィンドウに表示されるプロパティがあります。  
  
-   によって表される、 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)デバッグ エンジン (DE) またはスレッドの実行の結果として、仮想マシンによって作成された通常のインターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)