---
title: "スタック フレーム | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デバッグのスタック フレーム"
  - "[デバッグ SDK] スタック フレームのデバッグ"
  - "スタック フレーム"
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# スタック フレーム
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッガーのアーキテクチャという点では **スタック フレーム** :  
  
-   スレッドの実行コンテキストを提供するスタックの抽象化です。  スレッドは関数内で常に実行されます。  スタック フレームは関数のローカル変数と引数を保持します。  Visual Studio でデバッグするにはデバッグ言語または環境はスタック フレームをサポートする必要があります。  
  
-   これを識別しついて関連付けられたスレッドを返すことができます。  スタック フレームは現在の命令ポインターを表しおよび関連するドキュメントと式の評価のコンテキストを返すコード コンテキストできます。  
  
-   ローカル変数と引数の名前型および値を記述するさまざまな IDE のデバッグ ウィンドウに表示されるプロパティがあります。  
  
-   通常スレッドの実行結果としてデバッグ エンジン \(DE\) または仮想マシンで作成された [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) のインターフェイスにより表されます。  
  
## 参照  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [エンジンをデバッグします。](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)