---
title: 実行制御と状態の評価 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a90f1fa098cfb60e6a3939332095dca5e52e3eb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852102"
---
# <a name="execution-control-and-state-evaluation"></a>実行の制御と状態の評価
アプリケーションをデバッグするには、関数にステップ イン、ブレークポイント、停止、および実行を継続としてこのような実行管理機能を実装する必要があります。 Visual Studio ベースのデバッグ イベントの場合は、その実行コントロールは、デバッガーのコンポーネント間で送信されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プログラムの制御](../../extensibility/debugger/program-control.md)  
 プログラムのレベルで発生する次のルーチンを一覧表示されます。 次のステートメントを設定、実行、ステップ実行、続行、中断、および再開します。  
  
 [ブレークポイントに関連するメソッド](../../extensibility/debugger/breakpoint-related-methods.md)  
 バインドを定義および保留中の Visual Studio をサポートするためのブレークポイントの型。  
  
 [呼び出しスタックの評価](../../extensibility/debugger/call-stack-evaluation.md)  
 中断モード中に、コール スタックのスタック フレームを表示できるようにするメソッドの実装について説明します。  
  
 [式の評価](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 デバッグ エンジン (DE) の式の評価 (EE) およびセッション デバッグ マネージャーは、解析に関連して、IDE の windows のいずれかに入力された式の評価について説明します。  
  
 [コントロールのイベント](../../extensibility/debugger/control-events.md)  
 プログラムの制御された実行中にイベントを送信するためのインターフェイスについて説明します。