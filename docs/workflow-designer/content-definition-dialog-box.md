---
title: ワークフロー デザイナーの [コンテンツ定義] ダイアログ ボックス
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cae5fc2c8da95a803dba915c3fa4b2a63820ee93
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952973"
---
# <a name="content-definition-dialog-box"></a>[コンテンツ定義] ダイアログ ボックス

**コンテンツ定義**を構成する ダイアログ ボックスがワークフロー デザイナーで使用される、**コンテンツ**のプロパティ、 <xref:System.ServiceModel.Activities.Send>、 <xref:System.ServiceModel.Activities.Receive>、 <xref:System.ServiceModel.Activities.SendReply>、および<xref:System.ServiceModel.Activities.ReceiveReply>アクティビティ。 このボックスを使用するアクティビティ デザイナーの詳細については、次を参照してください、[送信](../workflow-designer/send-activity-designer.md)、[受信](../workflow-designer/receive-activity-designer.md)、 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)、および[SendAndReceiveReply。](../workflow-designer/sendandreceivereply-template-designer.md)トピック。

次の表に、ユーザー インターフェイス (UI) 要素の**関連付けの初期化** ダイアログ ボックス。

|UI 要素|説明|
|-|-----------------|
|**メッセージ**|メッセージの内容を指定します、**メッセージ データ**式テキスト ボックスと、型を使用して、**メッセージの種類**ドロップダウン リスト ボックス。 既定では、**コンテンツ定義**を使用して、 <xref:System.ServiceModel.Activities.ReceiveMessageContent>、要求、<xref:System.ServiceModel.Channels.Message>またはメッセージ コントラクト、ワークフロー サービス定義内の型。|
|**パラメーター**|をクリックして、**パラメーター**ラジオ ボタンを使用する<xref:System.ServiceModel.Activities.ReceiveParametersContent>、データ コントラクトを受け取る。 <xref:System.Activities.OutArgument> キーおよび値のペアのジェネリック コレクションを設定するには、データ グリッドを使用します。これらの値は、現在のワークフローの変数パラメーターに割り当てられます。|

**コンテンツ定義**ダイアログ ボックスを使用して、**送信**、**受信**、 **ReceiveAndSendReply**、および**SendAndReceiveReply**デザイナー。 デザイナーへのアクセス方法は、どの場合も同様です。ここでは、Receive デザイナーを使用する例で手順を説明します。

**受信**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**とアクティビティを通常配置して任意の場所は、ワークフロー デザイナー画面にドロップします。 この操作により、Receive という既定の <xref:System.ServiceModel.Activities.Receive> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 選択、**受信**アクティビティ デザイナーおよび (コンテンツ) のテキストの横にある省略記号のボタンをクリックし、**コンテンツ**プロパティ グリッドでプロパティ、**コンテンツ定義**ダイアログ ボックスを表示します。

内でコンテンツを指定することができます、**メッセージ**のセクションを<xref:System.ServiceModel.Activities.ReceiveMessageContent>アクティビティ内、または、**パラメーター**のセクションを<xref:System.ServiceModel.Activities.ReceiveParametersContent>アクティビティ。

## <a name="see-also"></a>関連項目

- [ワークフロー デザイナーの UI ヘルプ](../workflow-designer/workflow-designer-ui-help.md)