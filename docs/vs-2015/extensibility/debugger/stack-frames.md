---
title: スタック フレーム |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d1efbc05528dd009098749fbe75316c0261b1b20
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540326"
---
# <a name="stack-frames"></a>スタック フレーム
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[スタック フレーム](https://docs.microsoft.com/visualstudio/extensibility/debugger/stack-frames)します。  
  
デバッガーのアーキテクチャの観点から、**スタック フレーム**:  
  
-   スレッドの実行コンテキストを提供するスタックの抽象化です。 スレッドは、関数内で常に実行されます。 スタック フレームをローカル変数、関数の引数を保持します。 を Visual Studio でデバッグするために、言語またはデバッグ中の環境は、スタック フレームをサポートする必要があります。  
  
-   両方を特定し、それ自体を記述および関連付けられたスレッドを返すことができます。 スタック フレームを返すことも、現在の命令ポインターだけでなく、関連付けられているドキュメントを表す、コードのコンテキストや式の評価コンテキスト。  
  
-   名前、種類、およびローカル変数と引数の値を記述して、さまざまな IDE のデバッグ ウィンドウに表示されるプロパティがあります。  
  
-   によって表される、 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)デバッグ エンジン (DE) またはスレッドの実行の結果として、仮想マシンによって作成された通常のインターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)

