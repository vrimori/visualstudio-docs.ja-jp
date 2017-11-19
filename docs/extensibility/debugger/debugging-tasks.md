---
title: "タスクのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8bd22d71753a8bf86adbe2b437407481388c48d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-tasks"></a>タスクのデバッグ
プログラムをデバッグする場合、起動する必要あるしデバッグ エンジン (DE) に接続する必要があります。 追加しない、DE は、以前に起動されたプログラムに関連付ける必要があります。 アタッチされる、デは特定スタートアップ イベントを生成する必要があります。 応答して、デバッグ パッケージは、IDE で設定されたブレークポイントをバインドしようとします。 プログラムでバインドされたブレークポイントに達すると停止し、ユーザー入力を待機します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [セキュリティ上の問題](../../extensibility/debugger/security-issues.md)  
 プログラムをデバッグするために必要なセキュリティ手順について説明します。  
  
 [プログラムの起動](../../extensibility/debugger/launching-a-program.md)  
 プログラムを起動するオペレーティング システムを呼び出す、DE を指定する方法の手順を説明します。  
  
 [プログラムへ直接アタッチする](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 既に実行されているプロセスで、プログラムのデバッグに使用するプロセスについて説明します。  
  
 [起動の後のスタートアップ イベントの送信](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 プログラムのメイン エントリ ポイントでは、デバッグの準備ができてまで、プログラムに、DE が結び付けられるに発生するイベントを一覧表示します。  
  
 [実行の制御](../../extensibility/debugger/control-of-execution.md)  
 送信する方法、DE 通常エントリ ポイント イベント、読み込み完了のイベントや状況に応じて、停止イベントについて説明します。  
  
 [ブレークポイントのバインド](../../extensibility/debugger/binding-breakpoints.md)  
 方法については、ユーザーは、ブレークポイントを設定、IDE 要求の作成し、プロンプト ブレークポイントを作成する、デバッグ セッションについて説明します。  
  
 [評価式](../../extensibility/debugger/evaluating-expressions.md)  
 式の作成方法と、式を評価する際の動作について説明します。  
  
 [データの視覚化と表示](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 ビジュアライザーの型とカスタム ビューアーが (EE) の式エバリュエーターでサポートされている方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)  
 デバッグ アーキテクチャ、主要な概念をについて説明します。  
  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)  
 DE、EE、およびシンボル ハンドラー (SH) を含む Visual Studio デバッグ コンポーネントの概要を示します。  
  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)  
 デの動作方法に同時にコード、ドキュメント、および式の評価のコンテキスト内でについて説明します。 3 つのコンテキスト、場所、位置、またはそれに関連する評価ごとに説明します。  
  
## <a name="see-also"></a>関連項目  
 [はじめに](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)