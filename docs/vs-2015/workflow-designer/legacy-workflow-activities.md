---
title: 従来のワークフロー アクティビティ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6ff21a431e380a281ce1261215367b89c4ecf1a3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205413"
---
# <a name="legacy-workflow-activities"></a>従来のワークフロー アクティビティ
[!INCLUDE[wf](../includes/wf-md.md)] に含まれる既定のアクティビティ セットは、制御フロー、条件、イベント処理、状態管理、アプリケーションやサービスとの通信などの機能を提供します。 ワークフローを設計するとき、[!INCLUDE[wfd1](../includes/wfd1-md.md)]に付属しているシステム標準のアクティビティを使用することも、独自のカスタム アクティビティを作成することもできます。  
  
 次の表は、[!INCLUDE[wf2](../includes/wf2-md.md)] フレームワークに付属ですぐに使用できるアクティビティ セットの一覧です。 すべてではなく、多くの場合、これらのアクティビティがアクティビティ デザイナーからアクセスできるによって表される、**ツールボックス**の[!INCLUDE[wfd2](../includes/wfd2-md.md)]します。 アクティビティを作成するからデザイナーをドラッグ、**ツールボックス**し、デザイン画面にドロップします。  
  
|アクティビティ|説明|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|使用される、 **HandleExternalEventActivity**ローカル サービスとの通信の入力と出力のアクティビティ。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][CallExternalMethodActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65060)します。|  
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|複合アクティビティのすべての子の実行が完了する前に取り消された複合アクティビティのクリーンアップ ロジックを格納するために使用されます。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][CancellationHandlerActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65061)します。|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Visual Basic または C# のコードをワークフローに追加できます。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][CodeActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65062)します。|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|補正可能バージョン[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][CompensatableSequenceActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65002)します。|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|補正可能バージョン**TransactionScopeActivity**します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][CompensatableTransactionScopeActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65063)します。|  
|[CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|エラー発生時に、ワークフローによって実行された操作を取り消すか補正するコードを呼び出すことができます。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][CompensateActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65064)します。|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|完了した TransactionScopeActivity アクティビティの補正を実行する 1 つまたは複数のアクティビティのラッパー [!INCLUDE[crdefault](../includes/crdefault-md.md)] [CompensationHandlerActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65065)します。|  
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|適用する条件に基づいて子アクティビティの実行、 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)アクティビティ自体とそれぞれの子に個別に適用される条件に基づいて。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][ConditionedActivityGroup アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65066)します。|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|タイムアウト期間に基づいて、ワークフロー内に遅延を作成できます。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][DelayActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65067)します。|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|指定されたイベントが発生すると実行される 1 つまたは複数のアクティビティをラップします。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][EventDrivenActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65068)します。|  
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|イベントをアクティビティに関連付けるフレームワークを提供します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][EventHandlersActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65069)します。|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|同時に、主要な子アクティビティの実行、 [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][EventHandlingScopeActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65070)します。|  
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|指定した種類の例外を処理するために使用します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][FaultHandlerActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65071)します。|  
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|型の子アクティビティの順序付きリストを含む複合アクティビティを表す[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][FaultHandlersActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65072)します。|  
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|組み合わせて使用、 [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)ローカル サービスとの通信の入力と出力のアクティビティ。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][HandleExternalEventActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65073)します。|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|各分岐の条件をテストし、アクティビティの条件と等しい最初の分岐を実行します**true**します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][IfElseActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65074)します。|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|分岐を表します、 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][IfElseBranchActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65075)します。|  
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|ワークフローから Web サービスを呼び出すことができます。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][InvokeWebServiceActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65076)します。|  
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|ワークフローから別のワークフローを呼び出すことができます。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][InvokeWorkflowActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65077)します。|  
|[ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|だけを含む複合アクティビティ[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)子アクティビティ。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][ListenActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65078)します。|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|2 つまたは複数の子のスケジュールを設定する方法を提供**SequenceActivity**アクティビティ分岐を同時に処理します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][ParallelActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65079)します。|  
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|ルールのコレクションを表すために使用されます。 ルールは、条件とその結果としてのアクションから構成されます。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][PolicyActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65004)します。|  
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|1 つの子アクティビティから複数のインスタンスを作成します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][ReplicatorActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65080)します。|  
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|複数のアクティビティをまとめて順次実行するための簡単な方法を提供します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][SequenceActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65081)します。|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|新しいステート (状態) への移行を指定します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][SetStateActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65082)します。|  
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|ステート マシン ワークフローにおける状態を表します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][StateActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65083)します。|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|使用される、 [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)アクティビティを終了するときに実行される子アクティビティのコンテナーとして、 **StateActivity**アクティビティ。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][StateFinalizationActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65008)します。|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|使用される、 [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)アクティビティの入力時に実行される子アクティビティのコンテナーとして、 **StateActivity**アクティビティ。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][StateInitializationActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65006)します。|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|特に注意が必要なエラー条件が発生したとき、ワークフローの実行を保留して介入できるようにします。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][SuspendActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65084)します。|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|同期されたドメイン内に含まれるアクティビティを順次実行します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][SynchronizationScopeActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65085)します。|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|エラー条件が発生したとき、ワークフローの実行を即座に終了できます。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][TerminateActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65086)します。|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|ワークフローのプロセス メタデータの一部としてスローされた業務処理例外をキャプチャできます。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][ThrowActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65087)します。|  
|[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|トランザクションと例外処理のフレームワークを提供します。 詳細については、次を参照してください。 [TransactionScopeActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65088)します。|  
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Web サービスで発生するエラーをモデル化できます。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][WebServiceFaultActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65089)します。|  
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Web サービスからデータを取得します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][WebServiceInputActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65090)します。|  
|[WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Web サービスからワークフローに対する要求に応答します。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][WebServiceOutputActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65092)します。|  
|[WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|条件が満たされるまで、ワークフローをループさせることができます。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][WhileActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65091)します。|  
  
 [!INCLUDE[crabout](../includes/crabout-md.md)] カスタム アクティビティを作成する方法[カスタム アクティビティの開発](http://go.microsoft.com/fwlink?LinkID=65023)と[従来のアクティビティ デザイナーを使用して](../workflow-designer/using-the-legacy-activity-designer.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [アクティビティ ビュー (レガシ)](../workflow-designer/activity-views-legacy.md)  
 アクティビティのさまざまなデザイン ビューについて説明します。  
  
 [方法: ツールボックスにアクティビティを追加する (レガシ)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 ツール ボックスにアクティビティを追加する方法を示します。  
  
 [方法: 宣言的ルール条件を作成する (レガシ)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 宣言的ルール条件を作成する手順を示します。  
  
 [方法: PolicyActivity ルール セットを作成する (レガシ)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 PolicyActivity ルール セットを作成する手順を示します。  
  
 [方法: WCF コントラクト操作を実装する (レガシ)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 [!INCLUDE[indigo2](../includes/indigo2-md.md)] コントラクト操作を実装する手順を示します。  
  
 [方法: WCF コントラクト操作を呼び出す (レガシ)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 [!INCLUDE[indigo2](../includes/indigo2-md.md)] コントラクト操作を呼び出す手順を示します。  
  
## <a name="see-also"></a>関連項目  
 [Windows Workflow Foundation アクティビティ](http://go.microsoft.com/fwlink?LinkID=65005)   
 [ワークフローの開発](http://go.microsoft.com/fwlink?LinkID=65010)   
 [ワークフロー アクティビティの開発](http://go.microsoft.com/fwlink?LinkID=65023)