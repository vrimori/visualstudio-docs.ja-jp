---
title: ワークフロー デザイナー - [CorrelatesOn の定義] ダイアログ ボックス
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0af61161009cd9bbd2242db6fc8652b3f29c8f3b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55003292"
---
# <a name="correlateson-definition-dialog-box"></a>[CorrelatesOn の定義] ダイアログ ボックス

**CorrelatesOn**  ダイアログ ボックスは、ワークフロー デザイナーで編集に使用される、<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>のプロパティを<xref:System.ServiceModel.Activities.Receive>アクティビティ。 詳細については、次を参照してください。[アクティビティ デザイナーの受信](../workflow-designer/receive-activity-designer.md)します。

<xref:System.ServiceModel.Activities.Receive> アクティビティの間の相関関係によって、ワークフロー内でさまざまなサービス操作が相互に接続される方法が指定されます。

次の表に、ユーザー インターフェイス (UI) 要素の**CorrelatesOn**  ダイアログ ボックス。

|UI 要素|説明|
|-|-----------------|
|**CorrelatesWith**|適切なワークフロー インスタンスにメッセージをルーティングするために使用される <xref:System.ServiceModel.Activities.CorrelationHandle>。|
|**XPath クエリ**|受信メッセージから相関関係データを抽出するためのクエリを含む、キーと値のペア。 この値に対応、<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>プロパティ。 XPath クエリは、<xref:System.ServiceModel.MessageQuerySet> オブジェクトに含まれます。|

## <a name="to-launch-the-correlateson-dialog-box"></a>[CorrelatesOn] ダイアログ ボックスを起動するには

**受信**からアクティビティ デザイナーをドラッグできる**ツールボックス**とアクティビティを通常配置して任意の場所に、ワークフロー デザイナー画面にドロップします。 アクティビティ デザイナーをドロップを作成、 <xref:System.ServiceModel.Activities.Receive> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>の受信。 開くには、 **CorrelatesOn の定義**ダイアログ ボックスで、**受信**アクティビティ デザイナーであると、プロパティ グリッドのコレクションのテキストの横にある省略記号ボタンを選択して、 **CorrelatesOn**プロパティ。

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Activities.Receive>
- [[関連付け初期化子の追加] ダイアログ ボックス](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [[関連付け] ダイアログ ボックスを追加します。](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [[関連付け初期化] ダイアログ ボックス](../workflow-designer/initialize-correlation-dialog-box.md)