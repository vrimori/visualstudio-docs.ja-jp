---
title: "コンテンツの定義 ダイアログ ボックス |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: abbdf64494386b0c5dc61d4cfc1a37940c29f9a8
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="content-definition-dialog-box"></a>[コンテンツ定義] ダイアログ ボックス
**コンテンツ定義**を構成する ダイアログ ボックスが Windows ワークフロー デザイナーで使用される、**コンテンツ**のプロパティ、 <xref:System.ServiceModel.Activities.Send>、 <xref:System.ServiceModel.Activities.Receive>、 <xref:System.ServiceModel.Activities.SendReply>、および<xref:System.ServiceModel.Activities.ReceiveReply>アクティビティ。 詳細については、このボックスを使用するアクティビティ デザイナーは、次を参照してください、[送信](../workflow-designer/send-activity-designer.md)、[受信](../workflow-designer/receive-activity-designer.md)、 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)、および[SendAndReceiveReply。](../workflow-designer/sendandreceivereply-template-designer.md)トピックです。

 次の表は、ユーザー インターフェイス (UI) 要素の**関連付けの初期化** ダイアログ ボックス。

|UI 要素|説明|
|----------------|-----------------|
|**[メッセージ]**|メッセージの内容を指定します、**メッセージ データ**式テキスト ボックスと、型を使用して、**メッセージの種類**ドロップダウン リスト ボックス。 既定では、**コンテンツ定義**を使用して、 <xref:System.ServiceModel.Activities.ReceiveMessageContent>、これが必要ですが、<xref:System.ServiceModel.Channels.Message>またはメッセージ コントラクト型ワークフロー サービス定義内で。|
|**パラメーター**|クリックして、**パラメーター**ラジオ ボタンを使用する<xref:System.ServiceModel.Activities.ReceiveParametersContent>、データ コントラクトを受け取る。 <xref:System.Activities.OutArgument> キーおよび値のペアのジェネリック コレクションを設定するには、データ グリッドを使用します。これらの値は、現在のワークフローの変数パラメーターに割り当てられます。|

 **コンテンツ定義**でダイアログ ボックスを使用して、**送信**、**受信**、 **ReceiveAndSendReply**、および**SendAndReceiveReply**デザイナー。 デザイナーへのアクセス方法は、どの場合も同様です。ここでは、Receive デザイナーを使用する例で手順を説明します。

 **受信**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]サーフェス任意の場所のアクティビティを通常配置しています。 この操作により、Receive という既定の <xref:System.ServiceModel.Activities.Receive> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 選択、**受信**、省略記号が (コンテンツ) のテキストの横にあるボタンをクリックしてアクティビティ デザイナー、**コンテンツ**プロパティ、プロパティ グリッドで、**コンテンツ定義**ダイアログ ボックスを表示します。

 コンテンツ内に指定することができます、**メッセージ**については、「、<xref:System.ServiceModel.Activities.ReceiveMessageContent>アクティビティ内または、**パラメーター**については「、<xref:System.ServiceModel.Activities.ReceiveParametersContent>アクティビティ。

## <a name="see-also"></a>関連項目

- [ワークフロー デザイナーの UI ヘルプ](../workflow-designer/workflow-designer-ui-help.md)