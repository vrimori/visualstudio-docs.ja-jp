---
title: 変更内容への対応および変更内容の反映
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 696a874df8050d9a79f7cd07b9fc168acdc6b717
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897980"
---
# <a name="responding-to-and-propagating-changes"></a>変更内容への対応および変更内容の反映
要素は、作成または削除、更新、ときに、モデルの他の部分やファイル、データベース、またはその他のコンポーネントなどの外部のリソースへの変更を反映するコードを記述できます。

## <a name="in-this-section"></a>このセクションの内容
 ガイドラインとしては、次の順序でこれらの手法を検討してください。

|手法|シナリオ|詳細情報|
|-|-|-|
|計算ドメインのプロパティを定義します。|ドメイン プロパティ、モデル内の他のプロパティからその値が計算されます。 たとえば、価格の価格の和である関連の要素。|[計算プロパティおよびカスタム格納プロパティ](../modeling/calculated-and-custom-storage-properties.md)|
|カスタム ストレージ ドメイン プロパティを定義します。|他の部分は、モデルまたは外部に格納されているドメインのプロパティ。 たとえば、モデル内のツリーに式の文字列を解析でした。|[計算プロパティおよびカスタム格納プロパティ](../modeling/calculated-and-custom-storage-properties.md)|
|OnDeleting OnValueChanging など変更ハンドラーをオーバーライドします。|さまざまな要素の同期を維持し、外部の値と、モデルの同期を維持します。<br /><br /> 定義された範囲に値を制限します。<br /><br /> プロパティの値とその他の変更の前後の直前に呼び出されます。 変更を終了するには、例外をスローします。|[ドメイン プロパティ値変更ハンドラー](../modeling/domain-property-value-change-handlers.md)|
|ルール|変更が発生したトランザクションの終了直前に実行をキューに入れられたルールを定義することができます。 Undo または Redo では実行されません。 ストアの 1 つの一部を別の同期には、それらを使用します。|[規則によって変更内容がモデル内に反映される](../modeling/rules-propagate-changes-within-the-model.md)|
|ストア イベント|モデリングのストアは、追加、要素またはリンクの削除やプロパティの値を変更するなどのイベントの通知を提供します。 イベントは、Undo および Redo でも実行されます。 ストア イベントを使用すると、ストアにない値を更新します。|[イベント ハンドラーによって変更内容がモデル外に反映される](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|.NET イベント|図形には、マウスのクリックやその他のジェスチャに応答するイベント ハンドラーがあります。 オブジェクトごとにこれらのイベントを登録する必要があります。 登録は、InitializeInstanceResources のオーバーライドでは、普通し、各要素に対して行う必要があります。<br /><br /> これらのイベントは、トランザクションの外部の通常発生します。|[方法: シェイプまたはデコレーターに対するクリック操作を受け取る](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|境界ルール|境界ルールは、図形の境界を制限するには、具体的には使用されます。|[BoundsRules によってシェイプの位置とサイズが制限される](../modeling/boundsrules-constrain-shape-location-and-size.md)|
|選択ルール|選択ルールは、ユーザーが選択できる具体的に制限します。|[方法: 現在の選択項目を表示および制限する](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|シェイプおよびコネクタ シャドウ、線、色、線の幅、スタイルなどの機能を使用してモデル要素の状態を示します。|[シェイプおよびコネクタの更新とモデルへの反映](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="comparing-rules-and-store-events"></a>**ルールとストア イベントを比較します。**
 変更通知、ルール、およびイベントは、モデルが変更された場合に実行されます。

 ルールは、通常、これで、変更が発生しました、エンド トランザクションで適用され、イベントが、トランザクションでの変更がコミットされた後に適用されます。

 ストア イベントを使用して、ストア内の一貫性を維持するためには、ストア、および規則外のオブジェクトと、モデルを同期します。

-   **カスタム ルールを作成する**抽象ルールからの派生クラスとしてカスタムの規則を作成します。 カスタム ルールに関する、フレームワークにも通知する必要があります。 詳細については、次を参照してください。[ルール反映されるまで変更内で、モデル](../modeling/rules-propagate-changes-within-the-model.md)します。

-   **イベントにサブスクライブする**前に、イベントをサブスクライブすることができますが、イベント ハンドラーおよびデリゲートを作成します。 使用して、<xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>プロパティ、イベントをサブスクライブします。 詳細については、次を参照してください。[イベント ハンドラー反映されるまで変更 Outside the モデル](../modeling/event-handlers-propagate-changes-outside-the-model.md)します。

-   **変更の取り消し**トランザクションを元に戻すと、イベントが発生しますが、規則は適用されません。 ルールは、値を変更します。 その変更を元に戻す場合は、値は、元に戻す操作中に、元の値にリセットされます。 イベントが発生したときに、元の値に戻す値を手動で変更する必要があります。 Transactons と元に戻すの詳細については、次を参照してください。[方法: モデルを更新するトランザクションを使用して](../modeling/how-to-use-transactions-to-update-the-model.md)します。

-   **ルールとイベントにイベント引数を渡す**両方のイベント ルールが渡されると、`EventArgs`方法に関する情報を持つパラメーター、モデルを変更します。

## <a name="see-also"></a>関連項目

- [方法: シェイプまたはデコレーターに対するクリック操作を受け取る](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)