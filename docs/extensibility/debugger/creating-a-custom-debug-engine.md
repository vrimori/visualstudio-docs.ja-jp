---
title: "カスタム デバッグ エンジンを作成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デバッグ エンジンを実装します。"
  - "カスタム デバッグ エンジンは、"
  - "[デバッグ SDK] カスタム デバッグ エンジンのデバッグ"
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# カスタム デバッグ エンジンを作成します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッグ エンジンはコンポーネント \(DE\) 特定のランタイム アーキテクチャを利用できるビューのデバッグです。  ランタイム環境に対してだけ1 人の de\-DE implementation があります。  
  
> [!NOTE]
>  Transact\-SQL の de\-DE implementationsJScript のがVBScriptJScript ではde\-DE を共有します。  
  
 DE はインタープリター システムまたは操作を実行制御ブレークポイントや式の評価などのデバッグ サービスを提供します。  これらのサービスは de\-DE interfaces を通じて実行してさまざまなオペレーショナル モードの切り替えにデバッガーが発生することがあります。  詳細については、「[操作モード](../../extensibility/debugger/operational-modes.md)」を参照してください。  
  
 DE を作成するには次の手順で構成されます :  
  
1.  Visual Studio での de\-DE の登録  
  
2.  デバッグするプログラムを有効にします。  
  
3.  実行状態とコントロールの評価  
  
4.  イベントの送信  
  
5.  終了とデタッチ  
  
## このセクションの内容  
 [カスタム デバッグ エンジンを登録します。](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 使用できるように Visual Studio を使用してデバッグ エンジンを登録するために必要な手順について説明します。  
  
 [デバッグするプログラムを有効にします。](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 DE がプログラムをデバッグするにはde\-DE の起動または既存のプログラムにアタッチする必要があることを示します。  
  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 アプリケーションのデバッグ実行コントロールの機能を実行するには必要な方法について説明します。  
  
 [イベントを送信します。](../../extensibility/debugger/sending-events.md)  
 DCOM に基づいてイベント モデルとしてデバッガーと DE 間の通信について説明します。  
  
 [終了とデタッチ](../../extensibility/debugger/termination-and-detaching.md)  
 正常に終了した場合の実行方法を説明するのでデバッグ アプリケーションにブレークポイント例外ランタイム エラーまたは無限ループを示します。  
  
 [デバッガー イベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)  
 デバッグ セッションで発生するイベントの呼び出し順序について説明します。  
  
 [方法: カスタム デバッグ エンジンをデバッグします。](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 カスタム DE をデバッグする方法について説明します。  
  
## 参照  
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)