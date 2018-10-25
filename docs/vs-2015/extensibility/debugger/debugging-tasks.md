---
title: タスクのデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab02c40911f4dbeb2d4452bebfd42c13ec232fc4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254065"
---
# <a name="debugging-tasks"></a>タスクのデバッグ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

起動できることをプログラムをデバッグして、デバッグ エンジン (DE) をアタッチする必要があります。 そう、DE は、以前に起動されたプログラムにアタッチする必要があります。 アタッチされると、デは特定のスタートアップ イベントを生成する必要があります。 応答では、パッケージのデバッグは、IDE で設定されたブレークポイントをバインドしようとします。 プログラムがバインドされたブレークポイントに達するときに停止し、ユーザー入力を待機します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [セキュリティ上の問題](../../extensibility/debugger/security-issues.md)  
 プログラムをデバッグするために必要なセキュリティ手順について説明します。  
  
 [プログラムの起動](../../extensibility/debugger/launching-a-program.md)  
 プログラムを起動するオペレーティング システムを呼び出す、DE を指定する方法の手順を説明します。  
  
 [プログラムへ直接アタッチする](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 既に実行されているプロセスでプログラムをデバッグするために使用するプロセスについて説明します。  
  
 [起動の後のスタートアップ イベントの送信](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 プログラムのメイン エントリ ポイントでし、デバッグの準備が整うまで、プログラム、DE がアタッチされると発生するイベントを一覧表示します。  
  
 [実行の制御](../../extensibility/debugger/control-of-execution.md)  
 送信する方法、DE 通常エントリ ポイント イベント、読み込み完了イベントの場合、または、状況に応じて、停止イベントについて説明します。  
  
 [ブレークポイントのバインド](../../extensibility/debugger/binding-breakpoints.md)  
 方法については、ユーザーは、ブレークポイントを設定、IDE、要求の作成し、プロンプトをブレークポイントを作成する、デバッグ セッションをについて説明します。  
  
 [評価式](../../extensibility/debugger/evaluating-expressions.md)  
 式の作成方法と、式が評価されるときの動作について説明します。  
  
 [データの視覚化と表示](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 式エバリュエーター (EE) で型のビジュアライザーおよびカスタム ビューアーをサポートする方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)  
 デバッグ アーキテクチャの主要な概念をについて説明します。  
  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)  
 DE、EE、およびシンボル ハンドラー (SH) を含む Visual Studio のデバッグ コンポーネントの概要を示します。  
  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)  
 コード、ドキュメント、および式の評価のコンテキスト内で、DE がどの同時に動作について説明します。 3 つのコンテキスト、場所、位置、またはそれに関連する評価ごとに説明します。  
  
## <a name="see-also"></a>関連項目  
 [はじめに](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

