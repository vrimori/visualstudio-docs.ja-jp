---
title: ワークフロー デザイナーの関連付け初期化子のダイアログ ボックスを追加します。
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
ms.openlocfilehash: 724c4e3ac911e5fda62304a08565937f38425368
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948955"
---
# <a name="add-correlationinitializers-dialog-box"></a>[関連付け初期化子の追加] ダイアログ ボックス

**[関連付け初期化子**を構成する] ダイアログ ボックスがワークフロー デザイナーで使用される、 **CorrelationInitializers**のプロパティ、 <xref:System.ServiceModel.Activities.Send>、 <xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.SendReply>と<xref:System.ServiceModel.Activities.ReceiveReply>アクティビティ。 このボックスを使用するアクティビティ デザイナーの詳細については、次を参照してください、[送信](../workflow-designer/send-activity-designer.md)、[受信](../workflow-designer/receive-activity-designer.md)、 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)、および[SendAndReceiveReply。](../workflow-designer/sendandreceivereply-template-designer.md)トピック。

このダイアログ ボックスで指定されたコレクションに関連付け初期化子は、メッセージング アクティビティ間の次の相関関係を初期化できます。

- クエリ ベース
- コンテキスト
- コールバック コンテキスト
- 要求/応答

次の表に、ユーザー インターフェイス (UI) 要素の **[関連付け初期化子**] ダイアログ ボックス。

|UI 要素|説明|
|-|-----------------|
|**初期化子を追加します。**|をクリックして、**追加初期化**ボックス、コレクションに追加の初期化子を追加します。|
|**関連付けの種類**|関連付け初期化子の種類を指定します。 次の 4 種類から選択できます。<br /><br /> 1.<xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> を指定するためのコールバック関連付け初期化子。<br />2.<xref:System.ServiceModel.Activities.CorrelationInitializer> を指定するためのコンテキスト関連付け初期化子。<br />3.<xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> を指定するための要求/応答関連付け初期化子。<br />4.<xref:System.ServiceModel.Activities.QueryCorrelationInitializer> を指定するためのクエリ関連付け初期化子。<br /><br /> 編集する、 **CorrelationType**<br /><br /> 1.特定の行にタブ、**初期化子の追加**DataGrid します。<br />2.フォーカスを設定する**CorrelationTypeComboBox**、キーを押して**Ctrl**+**タブ**します。<br />3.ポップアップ表示するには、Alt + Down キーを押して、 **ComboBox**して編集できます。|
|**XPath クエリ**|送受信メッセージから相関関係データを抽出するためのクエリを含む、キーと値のペア。 このリストは、<xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 型を使用している場合にのみ有効です。|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>[関連付け初期化子の追加] ダイアログ ボックスを開くには

 **関連付け初期化子**ダイアログ ボックスを使用して、**送信**、**受信**、 **ReceiveAndSendReply**、および**SendAndReceiveReply**デザイナー。 各ケースとを含むケースと似ていますそれらにアクセスする、**受信**デザイナーは、手順を説明するためにここで使用します。

 **受信**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**とアクティビティを配置して任意の場所は、ワークフロー デザイナー画面にドロップします。 削除、**受信**アクティビティ デザイナーを作成、 <xref:System.ServiceModel.Activities.Receive> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>の受信。 選択、**受信**アクティビティ デザイナーおよび (コレクション) のテキストを横にある省略記号のボタンをクリックし、 **CorrelationInitializers**プロパティ グリッドでプロパティ、**追加関連付け初期化子の**ダイアログ ボックスを表示します。

## <a name="see-also"></a>関連項目

- [[関連付け] ダイアログ ボックスを追加します。](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [[関連付け初期化] ダイアログ ボックス](../workflow-designer/initialize-correlation-dialog-box.md)