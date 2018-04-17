---
title: '[CorrelatesOn の定義] ダイアログ ボックス |Microsoft ドキュメント'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 930f291f68e62e70c4d2a03f490f84fd8d36f657
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="correlateson-definition-dialog-box"></a>[CorrelatesOn の定義] ダイアログ ボックス
**CorrelatesOn** Windows ワークフロー デザイナーで編集する ダイアログ ボックスが使用される、<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>のプロパティ、<xref:System.ServiceModel.Activities.Receive>アクティビティ。 詳細については、次を参照してください。、[受信](../workflow-designer/receive-activity-designer.md)トピックです。

 <xref:System.ServiceModel.Activities.Receive> アクティビティの間の相関関係によって、ワークフロー内でさまざまなサービス操作が相互に接続される方法が指定されます。

 次の表は、ユーザー インターフェイス (UI) 要素の**CorrelatesOn**  ダイアログ ボックス。

|UI 要素|説明|
|----------------|-----------------|
|**CorrelatesWith**|適切なワークフロー インスタンスにメッセージをルーティングするために使用される <xref:System.ServiceModel.Activities.CorrelationHandle>。|
|**XPath クエリ**|受信メッセージから相関関係データを抽出するためのクエリを含む、キーと値のペア。 これは、<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> プロパティに対応します。 XPath クエリは、<xref:System.ServiceModel.MessageQuerySet> オブジェクトに含まれます。|

## <a name="to-launch-the-correlateson-dialog-box"></a>[CorrelatesOn] ダイアログ ボックスを起動するには
 **受信**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]サーフェス任意の場所のアクティビティを通常配置しています。 この操作により、Receive という既定の <xref:System.ServiceModel.Activities.Receive> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 選択、**受信**、省略記号が (コレクション) テキストの横にあるボタンをクリックしてアクティビティ デザイナー、 **CorrelatesOn**プロパティ、プロパティ グリッドで、 **CorrelatesOn の定義**ダイアログ ボックスを表示します。

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Activities.Receive>
- [[関連付け初期化子の追加] ダイアログ ボックス](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [追加の相関関係 ダイアログ ボックス](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [[関連付け初期化] ダイアログ ボックス](../workflow-designer/initialize-correlation-dialog-box.md)