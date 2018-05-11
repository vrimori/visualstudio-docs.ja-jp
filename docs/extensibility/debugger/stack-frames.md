---
title: スタック フレーム |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: feb2bc9d87486b6f83cf4b19ecec24c8c03edee5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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