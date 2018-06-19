---
title: ワークフロー デザイナーの [コンテンツ定義] ダイアログ ボックス
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f20a17cf7e01eafc75263bd2753d686908574752
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971668"
---
# <a name="content-definition-dialog-box"></a>[コンテンツ定義] ダイアログ ボックス

**コンテンツ定義**を構成する ダイアログ ボックスが Windows ワークフロー デザイナーで使用される、**コンテンツ**のプロパティ、 <xref:System.ServiceModel.Activities.Send>、 <xref:System.ServiceModel.Activities.Receive>、 <xref:System.ServiceModel.Activities.SendReply>、および<xref:System.ServiceModel.Activities.ReceiveReply>アクティビティ。 詳細については、このボックスを使用するアクティビティ デザイナーは、次を参照してください、[送信](../workflow-designer/send-activity-designer.md)、[受信](../workflow-designer/receive-activity-designer.md)、 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)、および[SendAndReceiveReply。](../workflow-designer/sendandreceivereply-template-designer.md)トピックです。

次の表は、ユーザー インターフェイス (UI) 要素の**関連付けの初期化** ダイアログ ボックス。

|UI 要素|説明|
|----------------|-----------------|
|**[メッセージ]**|メッセージの内容を指定します、**メッセージ データ**式テキスト ボックスと、型を使用して、**メッセージの種類**ドロップダウン リスト ボックス。 既定では、**コンテンツ定義**を使用して、 <xref:System.ServiceModel.Activities.ReceiveMessageContent>、これが必要ですが、<xref:System.ServiceModel.Channels.Message>またはメッセージ コントラクト型ワークフロー サービス定義内で。|
|**パラメーター**|クリックして、**パラメーター**ラジオ ボタンを使用する<xref:System.ServiceModel.Activities.ReceiveParametersContent>、データ コントラクトを受け取る。 <xref:System.Activities.OutArgument> キーおよび値のペアのジェネリック コレクションを設定するには、データ グリッドを使用します。これらの値は、現在のワークフローの変数パラメーターに割り当てられます。|

**コンテンツ定義**でダイアログ ボックスを使用して、**送信**、**受信**、 **ReceiveAndSendReply**、および**SendAndReceiveReply**デザイナー。 デザイナーへのアクセス方法は、どの場合も同様です。ここでは、Receive デザイナーを使用する例で手順を説明します。

**受信**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**し、アクティビティを通常配置している場所に、ワークフロー デザイナー画面にドロップします。 この操作により、Receive という既定の <xref:System.ServiceModel.Activities.Receive> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 選択、**受信**、省略記号が (コンテンツ) のテキストの横にあるボタンをクリックしてアクティビティ デザイナー、**コンテンツ**プロパティ、プロパティ グリッドで、**コンテンツ定義**ダイアログ ボックスを表示します。

コンテンツ内に指定することができます、**メッセージ**については、「、<xref:System.ServiceModel.Activities.ReceiveMessageContent>アクティビティ内または、**パラメーター**については「、<xref:System.ServiceModel.Activities.ReceiveParametersContent>アクティビティ。

## <a name="see-also"></a>関連項目

- [ワークフロー デザイナーの UI ヘルプ](../workflow-designer/workflow-designer-ui-help.md)