---
title: "ReceiveAndSendReply テンプレート デザイナー |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4c1236f8c3f86362ba49aa4b985dcc601a66c476
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply テンプレート デザイナー

**ReceiveAndSendReply**のペアを作成するテンプレートが使用される事前構成済み<xref:System.ServiceModel.Activities.Receive>と<xref:System.ServiceModel.Activities.SendReply>内のアクティビティ、<xref:System.Activities.Statements.Sequence>要求/応答メッセージ交換の一部として関連付けられるアクティビティサーバーでのパターン。

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply テンプレート
 追加**ReceiveAndSendReply**テンプレートが作成されるほかの 3 つの処理、<xref:System.ServiceModel.Activities.Receive>と<xref:System.ServiceModel.Activities.SendReply>活動、<xref:System.Activities.Statements.Sequence>アクティビティ。

1.  <xref:System.ServiceModel.Activities.Receive.OperationName%2A> アクティビティの <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> プロパティと <xref:System.ServiceModel.Activities.Receive> プロパティを構成する。

2.  <xref:System.ServiceModel.Activities.SendReply.Request%2A> アクティビティの <xref:System.ServiceModel.Activities.Receive> プロパティを <xref:System.ServiceModel.Activities.Send> アクティビティにバインドする。

3.  親アクティビティに、変数として <xref:System.ServiceModel.Activities.CorrelationHandle> を作成する。

### <a name="using-the-receiveandsendreply-template-designer"></a>ReceiveAndSendReply テンプレート デザイナーの使用
 **ReceiveAndSendReply**アクティビティ デザイナーは含まれて、**メッセージング**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス** ] タブの [ [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X です)。

 **ReceiveAndSendReply**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]サーフェス任意の場所のアクティビティを通常配置しています。 これを作成、<xref:System.ServiceModel.Activities.Receive>で構成できます。 アクティビティ、**送信**アクティビティ デザイナーと、相関<xref:System.ServiceModel.Activities.SendReply>SendReplyToReceive デザイナーを構成できます。

 使用しての詳細については、**受信**を構成するデザイナー、<xref:System.ServiceModel.Activities.Receive>アクティビティを参照してください、[受信](../workflow-designer/receive-activity-designer.md)トピックです。

 使用しての詳細については、 **SendReplyToReceive**を構成するデザイナー、<xref:System.ServiceModel.Activities.SendReply>アクティビティを次のセクションを参照してください。

### <a name="properties-of-sendreply"></a>SendReply のプロパティ
 次の表に、<xref:System.ServiceModel.Activities.SendReply> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]のデザイナー画面で編集できます。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.SendReply> アクティビティの省略可能な表示名。 既定値は SendReplyToReceive です。<br /><br /> 既定値以外の <xref:System.Activities.Activity.DisplayName%2A> の使用は必須ではありませんが、使用することをお勧めします。|
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|True|この <xref:System.ServiceModel.Activities.Receive> アクティビティと関連付けられる <xref:System.ServiceModel.Activities.SendReply> アクティビティへの参照。 このプロパティがありますいない**null**です。 <xref:System.ServiceModel.Activities.Receive> アクティビティと <xref:System.ServiceModel.Activities.SendReply> アクティビティは、要求/応答メッセージ パターンをモデル化するためにサーバーで一緒に使用されます。 このプロパティでは、関連付ける <xref:System.ServiceModel.Activities.Send> アクティビティを指定します。 このプロパティは、<xref:System.ServiceModel.Activities.Send> アクティビティの作成元である <xref:System.ServiceModel.Activities.SendReply> アクティビティに自動的にバインドされるため、デザイナーでは編集できません。|
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|False|受信するメッセージまたはパラメーターの内容を指定します。 <xref:System.ServiceModel.Activities.ReceiveMessageContent> アクティビティまたは <xref:System.ServiceModel.Activities.ReceiveParametersContent> アクティビティを指定できます。 横にある省略記号ボタンをクリックしてこのプロパティを編集、**コンテンツ**フィールドで、プロパティ グリッドまたはをクリックすると、**定義しています.**ボタンの横にある、**コンテンツ**のラベルを**受信**アクティビティ デザイナー画面。 両方を表示、**コンテンツ定義**ダイアログ。 このボックスを使用する方法の詳細については、次を参照してください。、[コンテンツ定義 ダイアログ ボックス](../workflow-designer/content-definition-dialog-box.md)トピックです。|
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|False|ワークフロー内のこの <xref:System.ServiceModel.Activities.CorrelationInitializer> アクティビティを構成する複数の <xref:System.ServiceModel.Activities.CorrelationHandle> オブジェクトを初期化する <xref:System.ServiceModel.Activities.Receive> オブジェクトのコレクションを指定します。 次に省略記号ボタンをクリックして、<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>を開くにはプロパティ グリッド内のプロパティ、 **[関連付け初期化子**] ダイアログ ボックス。 詳細については、このボックスを使用して、次を参照してください。、 [CorrelationInitializers ダイアログ ボックスの追加](../workflow-designer/add-correlationinitializers-dialog-box.md)トピックです。|
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|False|メッセージのアクション ヘッダーを指定します。 これを明示的に設定しない場合は、次の既定値が設定されます。<br /><br /> **https://tempuri.org/{サービス コントラクトの名前空間}/{サービス コントラクト名}/{操作名}**|
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|応答メッセージを送信する前にワークフロー サービス インスタンスを永続化するかどうかを指定します。 既定値は **false** です。|

## <a name="see-also"></a>関連項目

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [受信](../workflow-designer/receive-activity-designer.md)
- [送信](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)