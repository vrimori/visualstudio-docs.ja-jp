---
title: デバッグ エンジンのカスタムの作成 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ece2b480890054526552ad3aeea4f3bd1a437f74
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203681"
---
# <a name="create-a-custom-debug-engine"></a>カスタム デバッグ エンジンを作成します。
デバッグ エンジン (DE) は、特定のランタイム アーキテクチャのデバッグを許可するコンポーネントです。 通常は実行時環境ごとに 1 つだけ DE 実装です。  
  
> [!NOTE]
>  TRANSACT-SQL および JScript 別々 の DE 実装もありますが、VBScript や JScript 単一 DE を共有します。  
  
 DE は、実行の制御やブレークポイントなど、式の評価などのデバッグ サービスを提供する、インタープリターや操作のシステムで動作します。 これらのサービスでは、DE インターフェイスを通じては実装され、デバッガーは別の操作モード間の遷移が発生することができます。 詳細については、次を参照してください。[操作モード](../../extensibility/debugger/operational-modes.md)します。  
  
 作成、DE、次の手順で構成されます。  
  
1.  Visual Studio を使用した、DE を登録します。  
  
2.  デバッグするプログラムを有効にします。  
  
3.  実行の制御と状態の検証を実装します。  
  
4.  イベントを送信します。  
  
5.  切り離しとデタッチを設定します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [カスタム デバッグ エンジンを登録します。](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 使用できるように、Visual Studio を使用したデバッグ エンジンを登録するために必要な手順について説明します。  
  
 [デバッグするプログラムを有効にします。](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 DE、プログラムをデバッグする前にする必要があります最初に起動する、DE か、既存のプログラムにアタッチについて説明します。  
  
 [実行の制御と状態の検証を実装します。](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 なぜアプリケーションのデバッグが必要です実行制御の機能の実装について説明します。  
  
 [イベントを送信します。](../../extensibility/debugger/sending-events.md)  
 DCOM に基づくイベント モデルとして、デバッガーとデ間の通信について説明します。  
  
 [切り離しとデタッチを設定します。](../../extensibility/debugger/termination-and-detaching.md)  
 ブレークポイント、例外、実行時エラー、またはデバッグするアプリケーションでは無限ループがないことを意味する通常の終了を実現する方法について説明します。  
  
 [デバッガー イベントを呼び出す](../../extensibility/debugger/calling-debugger-events.md)  
 デバッグ セッションで発生するイベントの呼び出しの順序について説明します。  
  
 [方法: カスタム デバッグ エンジンをデバッグ](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 カスタム DE をデバッグする方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)