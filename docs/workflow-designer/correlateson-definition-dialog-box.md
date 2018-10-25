---
title: ワークフロー デザイナー - [CorrelatesOn の定義] ダイアログ ボックス
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3cfd9d43a8152b629635103b399ef0d7566e4867
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933119"
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