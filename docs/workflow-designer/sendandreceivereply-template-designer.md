---
title: ワークフロー デザイナー - SendAndReceiveReply テンプレート デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 282ba94c026b885cb6f8250b33beb98616376e8d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755812"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply テンプレート デザイナー

**SendAndReceiveReply**のペアを作成するテンプレートが使用される事前構成済み<xref:System.ServiceModel.Activities.Send>と<xref:System.ServiceModel.Activities.ReceiveReply>アクティビティ。 アクティビティの一部である、<xref:System.Activities.Statements.Sequence>アクティビティとは、クライアントの要求/応答メッセージ交換パターンの一部として相関します。

## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply テンプレート

追加、 **SendAndReceiveReply**テンプレートは次の 3 つ作成されるほか、<xref:System.ServiceModel.Activities.Send>と<xref:System.ServiceModel.Activities.ReceiveReply>内のアクティビティを<xref:System.Activities.Statements.Sequence>アクティビティ。

- 構成、<xref:System.ServiceModel.Activities.Send.OperationName%2A>と<xref:System.ServiceModel.Activities.Send.ServiceContractName%2A>のプロパティ、<xref:System.ServiceModel.Activities.Send>アクティビティ。

- <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> アクティビティの <xref:System.ServiceModel.Activities.ReceiveReply> プロパティを <xref:System.ServiceModel.Activities.Send> アクティビティにバインドする。

- 親アクティビティに、変数として <xref:System.ServiceModel.Activities.CorrelationHandle> を作成する。

### <a name="use-the-sendandreceivereply-template-designer"></a>SendAndReceiveReply テンプレート デザイナーを使用してください。

アクセス、 **SendAndReceiveReply**内のアクティビティ デザイナー、**メッセージング**のカテゴリ、**ツールボックス**します。 **SendAndReceiveReply**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**とアクティビティを通常配置して任意の場所は、ワークフロー デザイナー画面にドロップします。 アクティビティ デザイナーをドロップを作成、<xref:System.ServiceModel.Activities.Send>アクティビティで構成できる、**送信**アクティビティ デザイナーと、相関<xref:System.ServiceModel.Activities.ReceiveReply>で構成できる、 **ReceiveReplyForSend**デザイナー。

使用しての詳細については、**送信**を構成するデザイナー、<xref:System.ServiceModel.Activities.Send>アクティビティを参照してください[送信](../workflow-designer/send-activity-designer.md)します。

### <a name="properties-of-receivereply"></a>ReceiveReply のプロパティ

次の表は、<xref:System.ServiceModel.Activities.ReceiveReply>プロパティと、デザイナーでの使用方法について説明します。 これらのプロパティは、[プロパティ] グリッドで編集でき、一部は、ワークフロー デザイナー画面で編集できます。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.ReceiveReply> アクティビティの省略可能な表示名。 既定値は、ReceiveReplyForSend です。<br /><br /> わかりやすい既定以外の値の使用<xref:System.Activities.Activity.DisplayName%2A>は必須ではありません、このような値を使用することをお勧めします。|
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|True|この <xref:System.ServiceModel.Activities.Send> アクティビティと関連付けられる <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティへの参照。 このプロパティがある必要がありますいない**null**します。 <xref:System.ServiceModel.Activities.Send> アクティビティと <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティは、要求/応答メッセージ パターンをモデル化するためにクライアントで一緒に使用されます。 このプロパティでは、関連付ける <xref:System.ServiceModel.Activities.Send> アクティビティを指定します。 自動的にバインドされているため、デザイナーでこのプロパティを編集することはできません、<xref:System.ServiceModel.Activities.Send>作成元のアクティビティ、<xref:System.ServiceModel.Activities.ReceiveReply>アクティビティ。|
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|受信するメッセージまたはパラメーターの内容を指定します。 <xref:System.ServiceModel.Activities.ReceiveMessageContent> アクティビティまたは <xref:System.ServiceModel.Activities.ReceiveParametersContent> アクティビティを指定できます。 このプロパティの横にある省略記号ボタンをクリックして編集、**コンテンツ**かをクリックして、プロパティ グリッドでフィールド、**定義**横に、**コンテンツ**のラベルを**受信**アクティビティ デザイナー画面。 両方を表示、**コンテンツ定義**ダイアログ。 このボックスを使用する方法の詳細については、次を参照してください。[コンテンツ定義 ダイアログ ボックス](../workflow-designer/content-definition-dialog-box.md)します。|
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|ワークフロー内のこの <xref:System.ServiceModel.Activities.CorrelationInitializer> アクティビティを構成する複数の <xref:System.ServiceModel.Activities.CorrelationHandle> オブジェクトを初期化する <xref:System.ServiceModel.Activities.Receive> オブジェクトのコレクションを指定します。 横にある省略記号ボタンをクリックして、<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>プロパティを開く [プロパティ] グリッドで、 **[関連付け初期化子**] ダイアログ ボックス。 詳細については、このボックスを使用して、次を参照してください。[関連付け初期化子の追加 ダイアログ ボックス](../workflow-designer/add-correlationinitializers-dialog-box.md)します。|
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|メッセージのアクション ヘッダーを指定します。 明示的に設定されている場合にその値の既定値します。<br /><br /> **https://tempuri.org/{service コントラクトの名前空間}/{サービス コントラクト名}/操作 {name} です。**|

## <a name="see-also"></a>関連項目

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [受信](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [送信](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)