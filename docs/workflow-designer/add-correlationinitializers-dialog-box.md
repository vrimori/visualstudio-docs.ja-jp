---
title: ワークフロー デザイナー - 追加 CorrelationInitializers ダイアログ ボックス
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc122840607b62a966e5224662ec2d557e5c8ed5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975147"
---
# <a name="add-correlationinitializers-dialog-box"></a>[関連付け初期化子の追加] ダイアログ ボックス

**[関連付け初期化子**を構成する] ダイアログ ボックスが Windows ワークフロー デザイナーで使用される、 **CorrelationInitializers**のプロパティ、 <xref:System.ServiceModel.Activities.Send>、 <xref:System.ServiceModel.Activities.Receive>、 <xref:System.ServiceModel.Activities.SendReply>、および<xref:System.ServiceModel.Activities.ReceiveReply>アクティビティ。 詳細については、このボックスを使用するアクティビティ デザイナーは、次を参照してください、[送信](../workflow-designer/send-activity-designer.md)、[受信](../workflow-designer/receive-activity-designer.md)、 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)、および[SendAndReceiveReply。](../workflow-designer/sendandreceivereply-template-designer.md)トピックです。

このダイアログ ボックスで指定したコレクション内の関連付け初期化子は、メッセージング アクティビティ間の次の相関関係を初期化できます。

- クエリ ベース
- コンテキスト
- コールバック コンテキスト
- 要求/応答

次の表は、ユーザー インターフェイス (UI) 要素の **[関連付け初期化子**] ダイアログ ボックス。

|UI 要素|説明|
|----------------|-----------------|
|**初期化子を追加します。**|をクリックして、**追加初期化**コレクションに追加の初期化子を追加するボックスです。|
|**関連付けの種類**|関連付け初期化子の種類を指定します。 次の 4 種類から選択できます。<br /><br /> 1.<xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> を指定するためのコールバック関連付け初期化子。<br />2.<xref:System.ServiceModel.Activities.CorrelationInitializer> を指定するためのコンテキスト関連付け初期化子。<br />3.<xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> を指定するための要求/応答関連付け初期化子。<br />4.<xref:System.ServiceModel.Activities.QueryCorrelationInitializer> を指定するためのクエリ関連付け初期化子。<br /><br /> 編集する、 **CorrelationType**<br /><br /> 1.特定の行にタブ、**初期化子の追加**データ グリッドです。<br />2.フォーカスを設定する**CorrelationTypeComboBox**、キーを押して**Ctrl**+**タブ**です。<br />3.ポップアップ表示して Alt + Down を押して、 **ComboBox**し編集することです。|
|**XPath クエリ**|送受信メッセージから相関関係データを抽出するためのクエリを含む、キーと値のペア。 このリストは、<xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 型を使用している場合にのみ有効です。|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>[関連付け初期化子の追加] ダイアログ ボックスを開くには

 **関連付け初期化子**でダイアログ ボックスを使用して、**送信**、**受信**、 **ReceiveAndSendReply**、および**SendAndReceiveReply**デザイナー。 各ケースと関係する場合と似ていますそれらにアクセスする、**受信**デザイナーは、手順を説明するためにここで使用します。

 **受信**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**し、アクティビティを配置している場所に、ワークフロー デザイナー画面にドロップします。 削除する、**受信**アクティビティ デザイナーを作成、 <xref:System.ServiceModel.Activities.Receive> 、既定値を持つアクティビティ<xref:System.Activities.Activity.DisplayName%2A>の受信します。 選択、**受信**、省略記号が (コレクション) テキストの横にあるボタンをクリックしてアクティビティ デザイナー、 **CorrelationInitializers**プロパティ、プロパティ グリッドで、**追加関連付け初期化子の**ダイアログ ボックスを表示します。

## <a name="see-also"></a>関連項目

- [追加の相関関係 ダイアログ ボックス](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [[関連付け初期化] ダイアログ ボックス](../workflow-designer/initialize-correlation-dialog-box.md)