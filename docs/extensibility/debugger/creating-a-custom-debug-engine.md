---
title: "デバッグ エンジンが、カスタムの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0edee6528919cfe28c542be850b9a104188ce403
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-custom-debug-engine"></a>カスタム デバッグ エンジンを作成します。
デバッグ エンジン (DE) は、特定のランタイム アーキテクチャのデバッグを許可するコンポーネントです。 実行時環境ごとに 1 つだけ DE 実装は通常です。  
  
> [!NOTE]
>  TRANSACT-SQL および JScript の別個の DE 実装があるときに、VBScript と JScript 単一 DE が共有します。  
  
 デは、実行の制御やブレークポイントなどの式の評価などのデバッグ サービスを提供する、インタープリターまたは操作のシステムで動作します。 これらのサービスは、DE インターフェイスによって実装され、デバッガーは別の操作モードの間の遷移が発生することができます。 詳細については、次を参照してください。[の操作モード](../../extensibility/debugger/operational-modes.md)です。  
  
 デの作成は、次の手順で構成されます。  
  
1.  Visual Studio で、DE を登録します。  
  
2.  デバッグするプログラムを有効にします。  
  
3.  実行の制御と状態の評価  
  
4.  イベントの送信  
  
5.  終了およびデタッチ  
  
## <a name="in-this-section"></a>このセクションの内容  
 [カスタム デバッグ エンジンの登録](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 使用できるように、Visual Studio でデバッグ エンジンを登録するために必要な手順について説明します。  
  
 [デバッグするプログラムの有効化](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 DE、プログラムをデバッグする前にする必要があります最初、DE を起動または説明し、既存のプログラムにアタッチします。  
  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 なぜアプリケーションのデバッグが必要です実行制御の機能の実装について説明します。  
  
 [イベントの送信](../../extensibility/debugger/sending-events.md)  
 DCOM に基づいてイベント モデルと、デバッガーとデ間の通信について説明します。  
  
 [切り離しとデタッチ](../../extensibility/debugger/termination-and-detaching.md)  
 ブレークポイント、例外、実行時エラー、またはデバッグするアプリケーションでは無限ループがないことを意味する通常の終了を実現する方法について説明します。  
  
 [デバッガーのイベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)  
 デバッグ セッションで発生するイベントの呼び出しの順序について説明します。  
  
 [方法: カスタム デバッグ エンジンのデバッグ](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 カスタム DE をデバッグする方法について説明します。  
  
## <a name="see-also"></a>参照  
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)