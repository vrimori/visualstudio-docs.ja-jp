---
title: "実行の制御と状態の評価 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグ SDK] 実行制御のデバッグ"
  - "式の評価、実行の制御"
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 実行の制御と状態の評価
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

アプリケーションをデバッグするには、関数にステップ イン、ブレークポイント、停止、および実行を継続としてこのような実行の制御機能を実装する必要があります。 Visual Studio ベースのデバッグ イベントには、その実行制御は、デバッガーのコンポーネント間で送信されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プログラムの制御](../../extensibility/debugger/program-control.md)  
 プログラムのレベルで発生する次のルーチンの一覧: 次のステートメントを設定を実行する、ステップ実行、続行、中断する、および再開します。  
  
 [ブレークポイントに関連するメソッド](../../extensibility/debugger/breakpoint-related-methods.md)  
 バインドを定義し、保留中の Visual Studio でサポートされているブレークポイントの種類。  
  
 [呼び出しスタックの評価](../../extensibility/debugger/call-stack-evaluation.md)  
 中断モードで呼び出し履歴のスタック フレームを表示できるように、メソッドの実装について説明します。  
  
 [式の評価](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 デバッグ エンジン (DE) の解析では、式の評価 (EE) とセッションのデバッグ マネージャーと、IDE のウィンドウの 1 つに入力された式の評価について説明します。  
  
 [コントロールのイベント](../../extensibility/debugger/control-events.md)  
 プログラムの制御された実行中にイベントを送信するためのインターフェイスについて説明します。