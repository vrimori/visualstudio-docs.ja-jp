---
title: ワークフロー デザイナーの ReceiveAndSendReply テンプレート デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b62da812773795ff89e1beb87af6364c8baee14
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915047"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply テンプレート デザイナー

**ReceiveAndSendReply**のペアを作成するテンプレートが使用される事前構成済み<xref:System.ServiceModel.Activities.Receive>と<xref:System.ServiceModel.Activities.SendReply>アクティビティ。 アクティビティの一部である、<xref:System.Activities.Statements.Sequence>アクティビティ、およびが、サーバーで要求/応答メッセージ交換パターンの一部として関連付けします。

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply テンプレート

追加、 **ReceiveAndSendReply**テンプレートは次の 3 つ作成されるほか、<xref:System.ServiceModel.Activities.Receive>と<xref:System.ServiceModel.Activities.SendReply>でアクティビティを<xref:System.Activities.Statements.Sequence>アクティビティ。

- 構成、<xref:System.ServiceModel.Activities.Receive.OperationName%2A>と<xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>のプロパティ、<xref:System.ServiceModel.Activities.Receive>アクティビティ。

- <xref:System.ServiceModel.Activities.SendReply.Request%2A> アクティビティの <xref:System.ServiceModel.Activities.Receive> プロパティを <xref:System.ServiceModel.Activities.Send> アクティビティにバインドする。

- 親アクティビティに、変数として <xref:System.ServiceModel.Activities.CorrelationHandle> を作成する。

### <a name="use-the-receiveandsendreply-template-designer"></a>ReceiveAndSendReply テンプレート デザイナーを使用します。

アクセス、 **ReceiveAndSendReply**内のアクティビティ デザイナー、**メッセージング**のカテゴリ、**ツールボックス**します。 **ReceiveAndSendReply**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**とアクティビティを通常配置して任意の場所は、ワークフロー デザイナー画面にドロップします。 アクティビティ デザイナーをドロップを作成、<xref:System.ServiceModel.Activities.Receive>アクティビティで構成できる、**送信**アクティビティ デザイナーと、相関<xref:System.ServiceModel.Activities.SendReply>SendReplyToReceive デザイナーで構成できます。

使用しての詳細については、**受信**を構成するデザイナー、<xref:System.ServiceModel.Activities.Receive>アクティビティを参照してください[アクティビティ デザイナーの受信](../workflow-designer/receive-activity-designer.md)します。

### <a name="properties-of-sendreply"></a>SendReply のプロパティ

次の表に、<xref:System.ServiceModel.Activities.SendReply> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集でき、一部は、ワークフロー デザイナー画面で編集できます。


| プロパティ名 | 必須 | 使用方法 |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | <xref:System.ServiceModel.Activities.SendReply> アクティビティの省略可能な表示名。 既定値は SendReplyToReceive です。<br /><br /> わかりやすい既定以外の値の使用<xref:System.Activities.Activity.DisplayName%2A>は必須ではありません、このような値を使用することをお勧めします。 |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | この <xref:System.ServiceModel.Activities.Receive> アクティビティと関連付けられる <xref:System.ServiceModel.Activities.SendReply> アクティビティへの参照。 このプロパティがある必要がありますいない**null**します。 <xref:System.ServiceModel.Activities.Receive> アクティビティと <xref:System.ServiceModel.Activities.SendReply> アクティビティは、要求/応答メッセージ パターンをモデル化するためにサーバーで一緒に使用されます。 このプロパティでは、関連付ける <xref:System.ServiceModel.Activities.Send> アクティビティを指定します。 自動的にバインドされているため、デザイナーでこのプロパティを編集することはできません、<xref:System.ServiceModel.Activities.Send>作成元のアクティビティ、<xref:System.ServiceModel.Activities.SendReply>アクティビティ。 |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | 受信するメッセージまたはパラメーターの内容を指定します。 <xref:System.ServiceModel.Activities.ReceiveMessageContent> アクティビティまたは <xref:System.ServiceModel.Activities.ReceiveParametersContent> アクティビティを指定できます。 このプロパティの横にある省略記号ボタンをクリックして編集、**コンテンツ**プロパティ グリッドで、またはをクリックして、フィールド、**を定義する**横に、**コンテンツ**上のラベル**受信**アクティビティ デザイナー画面。 両方を表示、**コンテンツ定義**ダイアログ。 このボックスを使用する方法の詳細については、次を参照してください。、[コンテンツ定義 ダイアログ ボックス](../workflow-designer/content-definition-dialog-box.md)トピック。 |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | ワークフロー内のこの <xref:System.ServiceModel.Activities.CorrelationInitializer> アクティビティを構成する複数の <xref:System.ServiceModel.Activities.CorrelationHandle> オブジェクトを初期化する <xref:System.ServiceModel.Activities.Receive> オブジェクトのコレクションを指定します。 横にある省略記号ボタンをクリックして、<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>プロパティを開く [プロパティ] グリッドで、 **[関連付け初期化子**] ダイアログ ボックス。 詳細については、このボックスを使用して、次を参照してください。、[関連付け初期化子の追加 ダイアログ ボックス](../workflow-designer/add-correlationinitializers-dialog-box.md)トピック。 |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | メッセージのアクション ヘッダーを指定します。 明示的に設定されている場合にその値の既定値します。<br /><br /> <strong>https://tempuri.org/{service コントラクトの名前空間}/{サービス コントラクト名}/操作 {name}</strong> |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | 応答メッセージを送信する前にワークフロー サービス インスタンスを永続化するかどうかを指定します。 既定値は **false** です。 |

## <a name="see-also"></a>関連項目

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)