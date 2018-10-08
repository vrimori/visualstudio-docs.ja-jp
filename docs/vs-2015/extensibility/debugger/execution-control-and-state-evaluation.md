---
title: 実行制御と状態の評価 |Microsoft Docs
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
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 72b13fece6129c6b3996363bb0ec082330c9b686
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539619"
---
# <a name="execution-control-and-state-evaluation"></a>実行の制御と状態の評価
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[実行の制御と状態を評価して](https://docs.microsoft.com/visualstudio/extensibility/debugger/execution-control-and-state-evaluation)します。  
  
アプリケーションをデバッグするには、関数にステップ イン、ブレークポイント、停止、および実行を継続としてこのような実行管理機能を実装する必要があります。 Visual Studio ベースのデバッグ イベントの場合は、その実行コントロールは、デバッガーのコンポーネント間で送信されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プログラムの制御](../../extensibility/debugger/program-control.md)  
 プログラムのレベルで発生する次のルーチンを一覧表示されます。 次のステートメントを設定、実行、ステップ実行、続行、中断、および再開します。  
  
 [ブレークポイントに関連するメソッド](../../extensibility/debugger/breakpoint-related-methods.md)  
 バインドを定義および保留中の Visual Studio をサポートするためのブレークポイントの型。  
  
 [呼び出し履歴の評価](../../extensibility/debugger/call-stack-evaluation.md)  
 中断モード中に、コール スタックのスタック フレームを表示できるようにするメソッドの実装について説明します。  
  
 [式の評価](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 デバッグ エンジン (DE) の式の評価 (EE) およびセッション デバッグ マネージャーは、解析に関連して、IDE の windows のいずれかに入力された式の評価について説明します。  
  
 [管理イベント](../../extensibility/debugger/control-events.md)  
 プログラムの制御された実行中にイベントを送信するためのインターフェイスについて説明します。

