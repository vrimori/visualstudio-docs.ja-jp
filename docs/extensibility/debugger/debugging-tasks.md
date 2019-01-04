---
title: タスクのデバッグ |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aa719871e075a5448fa2d351c5bd7950a833601a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900153"
---
# <a name="debug-tasks"></a>タスクをデバッグします。
起動できることをプログラムをデバッグして、デバッグ エンジン (DE) をアタッチする必要があります。 そう、DE は、以前に起動されたプログラムにアタッチする必要があります。 アタッチされると、デは特定のスタートアップ イベントを生成する必要があります。 応答では、パッケージのデバッグは、IDE で設定されたブレークポイントをバインドしようとします。 プログラムがバインドされたブレークポイントに達するときに停止し、ユーザー入力を待機します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [セキュリティの問題](../../extensibility/debugger/security-issues.md)  
 プログラムをデバッグするために必要なセキュリティ手順について説明します。  
  
 [プログラムを起動します。](../../extensibility/debugger/launching-a-program.md)  
 プログラムを起動するオペレーティング システムを呼び出す、DE を指定する方法の手順を説明します。  
  
 [プログラムに直接アタッチします。](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 既に実行されているプロセスでプログラムをデバッグするために使用するプロセスについて説明します。  
  
 [起動の後のスタートアップ イベントを送信します。](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 プログラムのメイン エントリ ポイントでし、デバッグの準備が整うまで、プログラム、DE がアタッチされると発生するイベントを一覧表示します。  
  
 [実行の制御](../../extensibility/debugger/control-of-execution.md)  
 送信する方法、DE 通常エントリ ポイント イベント、読み込み完了イベントの場合、または、状況に応じて、停止イベントについて説明します。  
  
 [ブレークポイントをバインドします。](../../extensibility/debugger/binding-breakpoints.md)  
 方法については、ユーザーは、ブレークポイントを設定、IDE、要求の作成し、プロンプトをブレークポイントを作成する、デバッグ セッションをについて説明します。  
  
 [式を評価します。](../../extensibility/debugger/evaluating-expressions.md)  
 式の作成方法と、式が評価されるときの動作について説明します。  
  
 [視覚化し、データを表示します。](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 式エバリュエーター (EE) で型のビジュアライザーおよびカスタム ビューアーをサポートする方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)  
 デバッグ アーキテクチャの主要な概念をについて説明します。  
  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)  
 DE、EE、およびシンボル ハンドラー (SH) を含む Visual Studio のデバッグ コンポーネントの概要を示します。  
  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)  
 コード、ドキュメント、および式の評価のコンテキスト内で、DE がどの同時に動作について説明します。 3 つのコンテキスト、場所、位置、またはそれに関連する評価ごとに説明します。  
  
## <a name="see-also"></a>関連項目  
 [開始するには](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)