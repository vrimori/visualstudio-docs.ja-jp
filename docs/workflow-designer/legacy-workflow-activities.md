---
title: 従来のワークフロー アクティビティ |Microsoft ドキュメント
ms.date: 01/18/2017
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f31ff7ac208d4b06ce454ef309d35400cb79f97
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-workflow-activities"></a>従来のワークフロー アクティビティ

[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] に含まれる既定のアクティビティ セットは、制御フロー、条件、イベント処理、状態管理、アプリケーションやサービスとの通信などの機能を提供します。 ワークフローを設計する場合は、Windows ワークフロー デザイナーで用意されているシステム標準アクティビティを行うこともできますか、独自のカスタム アクティビティを作成することができます。

 次の表は、[!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] フレームワークに付属ですぐに使用できるアクティビティ セットの一覧です。 多くの場合、すべてではなく、これらのアクティビティはからアクセスできるアクティビティ デザイナーによって表される、**ツールボックス**の[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]です。 アクティビティを作成するからそのデザイナーをドラッグ、**ツールボックス**し、デザイン画面にドロップします。

|アクティビティ|説明|
|--------------|-----------------|
|<xref:System.Workflow.Activities.CallExternalMethodActivity>|使用される、 **HandleExternalEventActivity**アクティビティと共に、ローカル サービスの入力と出力します。 詳細については、次を参照してください。 [CallExternalMethodActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65060)です。|
|**System.Workflow.Activities.CancellationHandlerActivity**|複合アクティビティのすべての子の実行が完了する前に取り消された複合アクティビティのクリーンアップ ロジックを格納するために使用されます。 詳細については、次を参照してください。 [CancellationHandlerActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65061)です。|
|<xref:System.Workflow.Activities.CodeActivity>|Visual Basic または C# のコードをワークフローに追加できます。 詳細については、次を参照してください。 [CodeActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65062)です。|
|<xref:System.Workflow.Activities.CompensatableSequenceActivity>|<xref:System.Workflow.Activities.SequenceActivity> の補正可能バージョンです。 詳細については、次を参照してください。 [CompensatableSequenceActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65002)です。|
|**System.Workflow.Activities.CompensatableTransactionScopeActivity**|補正可能バージョン**TransactionScopeActivity**です。 詳細については、次を参照してください。 [CompensatableTransactionScopeActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65063)です。|
|**System.Workflow.Activities.CompensateActivity**|エラー発生時に、ワークフローによって実行された操作を取り消すか補正するコードを呼び出すことができます。 詳細については、次を参照してください。 [CompensateActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65064)です。|
|**System.Workflow.Activities.CompensationHandlerActivity**|詳細については、完了した TransactionScopeActivity アクティビティの補正を実行する 1 つまたは複数のアクティビティのラッパーを参照してください[CompensationHandlerActivity アクティビティ](http://go.microsoft.com/fwlink?LinkID=65065)です。|
|<xref:System.Workflow.Activities.ConditionedActivityGroup>|<xref:System.Workflow.Activities.ConditionedActivityGroup> アクティビティ自体に適用される条件と、それぞれの子に個別に適用される条件に基づいて、子アクティビティを実行します。 詳細については、次を参照してください。 [ConditionedActivityGroup アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65066)です。|
|<xref:System.Workflow.Activities.DelayActivity>|タイムアウト期間に基づいて、ワークフロー内に遅延を作成できます。 詳細については、次を参照してください。 [DelayActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65067)です。|
|<xref:System.Workflow.Activities.EventDrivenActivity>|指定されたイベントが発生すると実行される 1 つまたは複数のアクティビティをラップします。 詳細については、次を参照してください。 [EventDrivenActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65068)です。|
|<xref:System.Workflow.Activities.EventHandlersActivity>|イベントをアクティビティに関連付けるフレームワークを提供します。 詳細については、次を参照してください。 [EventHandlersActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65069)です。|
|<xref:System.Workflow.Activities.EventHandlingScopeActivity>|同時に、主要な子アクティビティの実行、<xref:System.Workflow.Activities.EventHandlersActivity>です。 詳細については、次を参照してください。 [EventHandlingScopeActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65070)です。|
|**System.Workflow.Activities.FaultHandlerActivity**|指定した種類の例外を処理するために使用します。 詳細については、次を参照してください。 [FaultHandlerActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65071)です。|
|**System.Workflow.Activities.FaultHandlersActivity**|型の子アクティビティの順序付きリストを持つ複合アクティビティを表す**System.Workflow.Activities.FaultHandlerActivity**です。 詳細については、次を参照してください。 [FaultHandlersActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65072)です。|
|<xref:System.Workflow.Activities.HandleExternalEventActivity>|組み合わせて使用、<xref:System.Workflow.Activities.CallExternalMethodActivity>アクティビティと共に、ローカル サービスの入力と出力します。 詳細については、次を参照してください。 [HandleExternalEventActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65073)です。|
|<xref:System.Workflow.Activities.IfElseActivity>|各分岐の条件をテストし、条件と等しい最初の分岐アクティビティを実行**true**です。 詳細については、次を参照してください。 [IfElseActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65074)です。|
|<xref:System.Workflow.Activities.IfElseBranchActivity>|<xref:System.Workflow.Activities.IfElseActivity> の分岐を表します。 詳細については、次を参照してください。 [IfElseBranchActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65075)です。|
|<xref:System.Workflow.Activities.InvokeWebServiceActivity>|ワークフローから Web サービスを呼び出すことができます。 詳細については、次を参照してください。[する InvokeWebServiceActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65076)です。|
|<xref:System.Workflow.Activities.InvokeWorkflowActivity>|ワークフローから別のワークフローを呼び出すことができます。 詳細については、次を参照してください。 [InvokeWorkflowActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65077)です。|
|<xref:System.Workflow.Activities.ListenActivity>|<xref:System.Workflow.Activities.EventDrivenActivity> 子アクティビティだけを含む複合アクティビティ。 詳細については、次を参照してください。 [ListenActivity にアクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65078)です。|
|<xref:System.Workflow.Activities.ParallelActivity>|2 つ以上の子のスケジュールを設定する方法を提供**SequenceActivity**アクティビティ分岐を同時に処理します。 詳細については、次を参照してください。 [ParallelActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65079)です。|
|<xref:System.Workflow.Activities.PolicyActivity>|ルールのコレクションを表すために使用されます。 ルールは、条件とその結果としてのアクションから構成されます。 詳細については、次を参照してください。 [PolicyActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65004)です。|
|<xref:System.Workflow.Activities.ReplicatorActivity>|1 つの子アクティビティから複数のインスタンスを作成します。 詳細については、次を参照してください。 [ReplicatorActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65080)です。|
|<xref:System.Workflow.Activities.SequenceActivity>|複数のアクティビティをまとめて順次実行するための簡単な方法を提供します。 詳細については、次を参照してください。 [SequenceActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65081)です。|
|<xref:System.Workflow.Activities.SetStateActivity>|新しいステート (状態) への移行を指定します。 詳細については、次を参照してください。 [SetStateActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65082)です。|
|<xref:System.Workflow.Activities.StateActivity>|ステート マシン ワークフローにおける状態を表します。 詳細については、次を参照してください。 [StateActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65083)です。|
|<xref:System.Workflow.Activities.StateFinalizationActivity>|使用される、<xref:System.Workflow.Activities.StateActivity>アクティビティを終了するときに実行される子アクティビティのコンテナーとして、 **StateActivity**アクティビティ。 詳細については、次を参照してください。 [StateFinalizationActivity アクティビティ](http://go.microsoft.com/fwlink?LinkID=65008)です。|
|<xref:System.Workflow.Activities.StateInitializationActivity>|使用される、<xref:System.Workflow.Activities.StateActivity>アクティビティに入るときに実行される子アクティビティのコンテナーとして、 **StateActivity**アクティビティ。 詳細については、次を参照してください。 [StateInitializationActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65006)です。|
|**System.Workflow.Activities.SuspendActivity**|特に注意が必要なエラー条件が発生したとき、ワークフローの実行を保留して介入できるようにします。 詳細については、次を参照してください。 [SuspendActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65084)です。|
|**System.Workflow.Activities.SynchronizationScopeActivity**|同期されたドメイン内に含まれるアクティビティを順次実行します。 詳細については、次を参照してください。 [SynchronizationScopeActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65085)です。|
|**System.Workflow.Activities.TerminateActivity**|エラー条件が発生したとき、ワークフローの実行を即座に終了できます。 詳細については、次を参照してください。 [TerminateActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65086)です。|
|**System.Workflow.Activities.ThrowActivity**|ワークフローのプロセス メタデータの一部としてスローされた業務処理例外をキャプチャできます。 詳細については、次を参照してください。 [ThrowActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65087)です。|
|**System.Workflow.Activities.TransactionScopeActivity**|トランザクションと例外処理のフレームワークを提供します。 詳細については、次を参照してください。 [TransactionScopeActivity アクティビティ](http://go.microsoft.com/fwlink?LinkID=65088)です。|
|<xref:System.Workflow.Activities.WebServiceFaultActivity>|Web サービスで発生するエラーをモデル化できます。 詳細については、次を参照してください。 [WebServiceFaultActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65089)です。|
|<xref:System.Workflow.Activities.WebServiceInputActivity>|Web サービスからデータを取得します。 詳細については、次を参照してください。 [WebServiceInputActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65090)です。|
|<xref:System.Workflow.Activities.WebServiceOutputActivity>|Web サービスからワークフローに対する要求に応答します。 詳細については、次を参照してください。 [WebServiceOutputActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65092)です。|
|<xref:System.Workflow.Activities.WhileActivity>|条件が満たされるまで、ワークフローをループさせることができます。 詳細については、次を参照してください。 [WhileActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65091)です。|

 カスタム アクティビティを作成する方法の詳細については、次を参照してください。[カスタム アクティビティの開発](http://go.microsoft.com/fwlink?LinkID=65023)と[従来のアクティビティ デザイナーを使用して](../workflow-designer/using-the-legacy-activity-designer.md)です。

## <a name="see-also"></a>関連項目

- [Windows Workflow Foundation アクティビティ](http://go.microsoft.com/fwlink?LinkID=65005)
- [ワークフローの開発](http://go.microsoft.com/fwlink?LinkID=65010)
- [ワークフロー活動の開発](http://go.microsoft.com/fwlink?LinkID=65023)