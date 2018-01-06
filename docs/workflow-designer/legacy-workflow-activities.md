---
title: "従来のワークフロー アクティビティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 756fa86cf892120b0062e2816f146425ac1b4fa3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-workflow-activities"></a>従来のワークフロー アクティビティ
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] に含まれる既定のアクティビティ セットは、制御フロー、条件、イベント処理、状態管理、アプリケーションやサービスとの通信などの機能を提供します。 ワークフローを設計するとき、[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]に付属しているシステム標準のアクティビティを使用することも、独自のカスタム アクティビティを作成することもできます。  
  
 次の表は、[!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] フレームワークに付属ですぐに使用できるアクティビティ セットの一覧です。 多くの場合、すべてではなく、これらのアクティビティはからアクセスできるアクティビティ デザイナーによって表される、**ツールボックス**の[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]です。 アクティビティを作成するからそのデザイナーをドラッグ、**ツールボックス**し、デザイン画面にドロップします。  
  
|アクティビティ|説明|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|使用される、 **HandleExternalEventActivity**アクティビティと共に、ローカル サービスの入力と出力します。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][CallExternalMethodActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65060)です。|  
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|複合アクティビティのすべての子の実行が完了する前に取り消された複合アクティビティのクリーンアップ ロジックを格納するために使用されます。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][許容される CancellationHandlerActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65061)です。|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Visual Basic または C# のコードをワークフローに追加できます。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][CodeActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65062)です。|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|補正可能バージョン[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)です。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][CompensatableSequenceActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65002)です。|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|補正可能バージョン**TransactionScopeActivity**です。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][CompensatableTransactionScopeActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65063)です。|  
|[CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|エラー発生時に、ワークフローによって実行された操作を取り消すか補正するコードを呼び出すことができます。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][CompensateActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65064)です。|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|完了した TransactionScopeActivity アクティビティの補正を実行する 1 つまたは複数のアクティビティのラッパー [!INCLUDE[crdefault](../test/includes/crdefault_md.md)] [CompensationHandlerActivity アクティビティ](http://go.microsoft.com/fwlink?LinkID=65065)です。|  
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|適用する条件に基づいて子アクティビティを実行、 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)アクティビティ自体とそれぞれの子に個別に適用する条件に基づいて。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][ConditionedActivityGroup アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65066)です。|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|タイムアウト期間に基づいて、ワークフロー内に遅延を作成できます。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][DelayActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65067)です。|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|指定されたイベントが発生すると実行される 1 つまたは複数のアクティビティをラップします。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][EventDrivenActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65068)です。|  
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|イベントをアクティビティに関連付けるフレームワークを提供します。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][EventHandlersActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65069)です。|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|同時に、主要な子アクティビティの実行、 [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)です。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][EventHandlingScopeActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65070)です。|  
|[許容される FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|指定した種類の例外を処理するために使用します。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][許容される FaultHandlerActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65071)です。|  
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|型の子アクティビティの順序付きリストを持つ複合アクティビティを表す[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)です。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][許容される FaultHandlersActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65072)です。|  
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|組み合わせて使用、 [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)アクティビティと共に、ローカル サービスの入力と出力します。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][HandleExternalEventActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65073)です。|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|各分岐の条件をテストし、条件と等しい最初の分岐アクティビティを実行**true**です。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][IfElseActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65074)です。|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|分岐を表す、 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)です。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][IfElseBranchActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65075)です。|  
|[する InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|ワークフローから Web サービスを呼び出すことができます。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][InvokeWebServiceActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65076)です。|  
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|ワークフローから別のワークフローを呼び出すことができます。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][InvokeWorkflowActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65077)です。|  
|[ListenActivity には](http://go.microsoft.com/fwlink?LinkID=65037)|だけを含む複合アクティビティ[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)子アクティビティ。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][ListenActivity にアクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65078)です。|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|2 つ以上の子のスケジュールを設定する方法を提供**SequenceActivity**アクティビティ分岐を同時に処理します。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][ParallelActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65079)です。|  
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|ルールのコレクションを表すために使用されます。 ルールは、条件とその結果としてのアクションから構成されます。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][PolicyActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65004)です。|  
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|1 つの子アクティビティから複数のインスタンスを作成します。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][ReplicatorActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65080)です。|  
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|複数のアクティビティをまとめて順次実行するための簡単な方法を提供します。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][SequenceActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65081)です。|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|新しいステート (状態) への移行を指定します。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][SetStateActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65082)です。|  
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|ステート マシン ワークフローにおける状態を表します。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][StateActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65083)です。|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|使用される、 [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)アクティビティを終了するときに実行される子アクティビティのコンテナーとして、 **StateActivity**アクティビティ。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][StateFinalizationActivity アクティビティ](http://go.microsoft.com/fwlink?LinkID=65008)です。|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|使用される、 [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)アクティビティに入るときに実行される子アクティビティのコンテナーとして、 **StateActivity**アクティビティ。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][StateInitializationActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65006)です。|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|特に注意が必要なエラー条件が発生したとき、ワークフローの実行を保留して介入できるようにします。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][SuspendActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65084)です。|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|同期されたドメイン内に含まれるアクティビティを順次実行します。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][SynchronizationScopeActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65085)です。|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|エラー条件が発生したとき、ワークフローの実行を即座に終了できます。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][TerminateActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65086)です。|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|ワークフローのプロセス メタデータの一部としてスローされた業務処理例外をキャプチャできます。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][ThrowActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65087)です。|  
|[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|トランザクションと例外処理のフレームワークを提供します。 詳細については、次を参照してください。 [TransactionScopeActivity アクティビティ](http://go.microsoft.com/fwlink?LinkID=65088)です。|  
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Web サービスで発生するエラーをモデル化できます。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][WebServiceFaultActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65089)です。|  
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Web サービスからデータを取得します。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][WebServiceInputActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65090)です。|  
|[WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Web サービスからワークフローに対する要求に応答します。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][WebServiceOutputActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65092)です。|  
|[WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|条件が満たされるまで、ワークフローをループさせることができます。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][WhileActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65091)です。|  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]カスタム アクティビティを作成、表示する方法[カスタム アクティビティの開発](http://go.microsoft.com/fwlink?LinkID=65023)と[従来のアクティビティ デザイナーを使用して](../workflow-designer/using-the-legacy-activity-designer.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [アクティビティ ビュー (レガシ)](../workflow-designer/activity-views-legacy.md)  
 アクティビティのさまざまなデザイン ビューについて説明します。  
  
 [方法: ツールボックスにアクティビティを追加する (レガシ)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 ツール ボックスにアクティビティを追加する方法を示します。  
  
 [方法: 宣言的ルール条件を作成する (レガシ)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 宣言的ルール条件を作成する手順を示します。  
  
 [方法: PolicyActivity ルール セットを作成する (レガシ)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 PolicyActivity ルール セットを作成する手順を示します。  
  
 [方法: WCF コントラクト操作 (レガシ) を実装します。](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] コントラクト操作を実装する手順を示します。  
  
 [方法: WCF コントラクト操作 (レガシ) を呼び出す](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] コントラクト操作を呼び出す手順を示します。  
  
## <a name="see-also"></a>参照  
 [Windows Workflow Foundation アクティビティ](http://go.microsoft.com/fwlink?LinkID=65005)   
 [ワークフローの開発](http://go.microsoft.com/fwlink?LinkID=65010)   
 [ワークフロー活動の開発](http://go.microsoft.com/fwlink?LinkID=65023)