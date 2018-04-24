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
ms.technology: vs-ide-modeling
ms.openlocfilehash: a706f8cafcdc140752775909be7222d6720c1c92
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="responding-to-and-propagating-changes"></a>変更内容への対応および変更内容の反映
要素では、作成、削除、または更新は、ときに、モデルの他の部分、またはファイル、データベース、またはその他のコンポーネントなどの外部のリソースへの変更を伝達するコードを記述することができます。

## <a name="in-this-section"></a>このセクションの内容
 指針としては、次の順序でこれらの手法を検討してください。

|手法|シナリオ|詳細情報|
|---------------|---------------|--------------------------|
|計算ドメインのプロパティを定義します。|その値は、モデル内の他のプロパティから計算ドメインのプロパティです。 たとえば、価格に関連する要素の価格の合計です。|[計算プロパティおよびカスタム格納プロパティ](../modeling/calculated-and-custom-storage-properties.md)|
|記憶域のカスタム ドメインのプロパティを定義します。|他の部分のモデルまたは外部に格納されているドメインのプロパティです。 たとえば、モデルのツリーに式の文字列を解析する可能性があります。|[計算プロパティおよびカスタム格納プロパティ](../modeling/calculated-and-custom-storage-properties.md)|
|OnValueChanging OnDeleting など変更ハンドラーをオーバーライドします。|さまざまな要素の同期、および保存外部の値と、モデルを同期します。<br /><br /> 定義済みの範囲内に値を制限します。<br /><br /> プロパティの値とその他の変更の前後の直前に呼び出されます。 変更を終了するには、例外をスローします。|[ドメイン プロパティ値変更ハンドラー](../modeling/domain-property-value-change-handlers.md)|
|ルール|変更が発生したトランザクションが終了する直前に実行するためキューに入っている規則を定義できます。 元に戻すかやり直すには実行されません。 ストアの 1 つの部分を別の同期を保持するのにには、それらを使用します。|[規則によって変更内容がモデル内に反映される](../modeling/rules-propagate-changes-within-the-model.md)|
|イベントを保存します。|モデル ストアは、追加、要素またはリンクの削除やプロパティの値を変更するなどのイベント通知を提供します。 イベントは元に戻すおよびやり直しでも実行されます。 ストアに含まれていない値を更新するのにには、ストアのイベントを使用します。|[イベント ハンドラーによって変更内容がモデル外に反映される](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|.NET イベント|図形には、マウスのクリックやその他のジェスチャに応答するイベント ハンドラーがあります。 オブジェクトごとにこれらのイベントを登録する必要があります。 登録は、通常、InitializeInstanceResources のオーバーライドで実行し、各要素に対して行う必要があります。<br /><br /> これらのイベントは、トランザクションの外部の通常発生します。|[方法: シェイプまたはデコレーターに対するクリック操作を受け取る](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|境界の規則|範囲ルールについては、図形の境界を制限するには、具体的に使用します。|[BoundsRules によってシェイプの位置とサイズが制限される](../modeling/boundsrules-constrain-shape-location-and-size.md)|
|選択ルール|選択ルールは、具体的には、ユーザーが選択できる新機能を制限します。|[方法: 現在の選択項目を表示および制限する](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|図形とコネクタ シャドウ、矢印、色、線の幅、スタイルなどの機能を使用して、モデル要素の状態を示してください。|[シェイプおよびコネクタの更新とモデルへの反映](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="comparing-rules-and-store-events"></a>**比較するルールとストア イベント**
 変更通知、ルール、およびイベントは、モデルが変更された場合に実行されます。

 ルールは通常が、変更が発生した、最後のトランザクションで適用され、イベントが、トランザクションでの変更がコミットされた後に適用されます。

 ストア、およびルールは、ストア内の一貫性を保つための外部オブジェクトと、モデルを同期するために、ストアのイベントを使用します。

-   **カスタム規則を作成する**抽象規則からの派生クラスとしてカスタム ルールを作成します。 カスタム ルールに関するフレームワークも通知する必要があります。 詳細については、次を参照してください。[ルール反映されるまで変更内で、モデル](../modeling/rules-propagate-changes-within-the-model.md)です。

-   **イベントにサブスクライブする**イベントにサブスクライブすることができます、前に、イベント ハンドラー、デリゲートを作成します。 使用して、<xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>イベントをサブスクライブするプロパティです。 詳細については、次を参照してください。[イベント ハンドラー反映されるまで変更 Outside the モデル](../modeling/event-handlers-propagate-changes-outside-the-model.md)です。

-   **変更の取り消し**トランザクションを元に戻すと、イベントが発生するが、規則は適用されません。 ルールは、値を変更します。 その変更を元に戻す場合は、値は元に戻す操作中に元の値にリセットされます。 イベントが発生したときに、元の値に戻す値を手動で変更する必要があります。 Transactons と取り消しの詳細については、次を参照してください。[する方法: モデルを更新するトランザクションを使用して](../modeling/how-to-use-transactions-to-update-the-model.md)です。

-   **ルールとイベントにイベント引数を渡す**両方のイベント ルールが渡されると、`EventArgs`方法に関する情報を持つパラメーター、モデルを変更します。

## <a name="see-also"></a>関連項目

- [方法: シェイプまたはデコレーターに対するクリック操作を受け取る](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)