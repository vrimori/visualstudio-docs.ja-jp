---
title: "実行の制御と状態の評価 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f2f76f97111f24a7b6b4ea1a7a22004d6867fcd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="execution-control-and-state-evaluation"></a>実行の制御と状態の評価
アプリケーションをデバッグするには、関数にステップ イン、ブレークポイント、停止、および実行を継続としてこのような実行の制御機能を実装する必要があります。 Visual Studio ベースのデバッグ イベントの場合は、その実行コントロールは、デバッガー コンポーネント間で送信されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プログラムの制御](../../extensibility/debugger/program-control.md)  
 プログラムのレベルで発生した次のルーチンの一覧: 次のステートメントを設定、実行、ステップ実行、続行、一時停止、および再開します。  
  
 [ブレークポイントに関連するメソッド](../../extensibility/debugger/breakpoint-related-methods.md)  
 バインドを定義し、保留中の Visual Studio でサポートされているブレークポイントの型。  
  
 [呼び出し履歴の評価](../../extensibility/debugger/call-stack-evaluation.md)  
 中断モード中に、呼び出し履歴のスタック フレームを表示できるようにするメソッドの実装について説明します。  
  
 [式の評価](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 デバッグ エンジン (DE) の式の評価 (EE) およびセッションのデバッグ マネージャーは、解析中に含まれると、式の評価が IDE のウィンドウの 1 つに入力した説明します。  
  
 [管理イベント](../../extensibility/debugger/control-events.md)  
 プログラムの制御された実行中にイベントを送信するためのインターフェイスについて説明します。