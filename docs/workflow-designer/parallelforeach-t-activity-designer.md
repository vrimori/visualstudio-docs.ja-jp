---
title: ParallelForEach&lt;T&gt;アクティビティ デザイナー |Microsoft ドキュメント
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62d86499296c72f48d1ffcad932e9f1ff4d2fef1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="parallelforeachlttgt-activity-designer"></a>ParallelForEach&lt;T&gt;アクティビティ デザイナー
<xref:System.Activities.Statements.ParallelForEach%601> アクティビティでは、コレクションの要素を列挙し、コレクションの各要素に対して埋め込みステートメントを並列的に (同じスレッドで非同期的に) 実行します。 このフロー制御アクティビティは、その子アクティビティがアイドル状態になると予想される場合に、<xref:System.Activities.Statements.Sequence> アクティビティの代わりに使用します。

 <xref:System.Activities.Statements.ParallelForEach%601> アクティビティには、ユーザーによって指定された <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> 式を保持する [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] プロパティがあります。 このプロパティは、各分岐の完了後に、<xref:System.Activities.Statements.ParallelForEach%601> アクティビティによって評価されます。 評価結果が場合**true**、<xref:System.Activities.Statements.ParallelForEach%601>アクティビティは他の分岐を実行せずに完了します。 場合、<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>に評価されない**true**、<xref:System.Activities.Statements.ParallelForEach%601>アクティビティのすべての子アクティビティが完了したときに完了します。

## <a name="the-parallelforeacht-activity"></a>ParallelForEach < T\>アクティビティ
 <xref:System.Activities.Statements.ParallelForEach%601> はそれ自体の値を列挙し、列挙した値ごとに <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> をスケジュールします。 スケジュールされるのは <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> のみです。 本文の実行方法は、<xref:System.Activities.Statements.ParallelForEach%601.Body%2A> がアイドル状態になるかどうかによって異なります。

 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> がアイドル状態にならない場合は、スケジュールされたアクティビティがスタックとして扱われるため、逆の順序で実行されます。つまり、最後にスケジュールされたアクティビティが最初に実行されます。 {1,2,3,4} 内のコレクションがある場合など、<xref:System.Activities.Statements.ParallelForEach%601>を使用して、 **WriteLine**値を書き出す本文として。この場合は、4、3、2、1 の順にコンソールに出力されます。 これは、ため**WriteLine** 4 の後にアイドル状態にならない**WriteLine**アクティビティがスケジュールされた、スタックの動作を使用して実行される (最初の最後の出し)。

 ただし、<xref:System.Activities.Statements.ParallelForEach%601.Body%2A> アクティビティや <xref:System.ServiceModel.Activities.Receive> アクティビティのように、アイドル状態になる可能性のあるアクティビティが <xref:System.Activities.Statements.Delay> に含まれている場合は、 それぞれのアクティビティが完了するまで待機する必要はありません。 <xref:System.Activities.Statements.ParallelForEach%601> は、スケジュールされている次の本文アクティビティに進み、実行を試みます。 そのアクティビティもアイドル状態になる場合は、<xref:System.Activities.Statements.ParallelForEach%601> が、さらに次の本文アクティビティに進みます。

### <a name="using-the-parallelforeacht-activity-designer"></a>使用して、ParallelForEach\<T > アクティビティ デザイナー
 **ParallelForEach\<T >**アクティビティ デザイナーは含まれて、**制御フロー**のカテゴリ、**ツールボックス**、 をクリックしてアクセスします。**ツールボックス** タブの左側にある、 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X です)。

 **ParallelForEach\<T >**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]アクティビティ デザイナーを通常配置している場所を画面のたとえば、内部の**シーケンス**アクティビティ デザイナー。 ドロップすた後、 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]、作成、<xref:System.Activities.Statements.ParallelForEach%601>アクティビティで、既定で含まれて、<xref:System.Activities.Activity.DisplayName%2A>の**ParallelForEach < Int32\>です。**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach < T\>ワークフロー デザイナーでのプロパティ
 次の表に、最も役に立つ <xref:System.Activities.Statements.ParallelForEach%601> アクティビティのプロパティと、デザイナーでのその使用方法を示します。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|ヘッダーのアクティビティ デザイナーの表示名を指定します。 既定値は**ParallelForEach\<Int32 >**です。 値を必要に応じて編集できます、**プロパティ**グリッド アクティビティ デザイナーのヘッダーで直接またはします。|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|コレクション内の各項目に対して実行するアクティビティ。 追加する、<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>アクティビティで、[ツールボックス] からアクティビティのドロップ、**本文**ボックスに、 **ParallelForEach\<T >**アクティビティ デザイナーのヒント テキストが「Drop ここにアクティビティ」です。|
|**TypeArgument**|True|内の項目の種類、<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>ジェネリック パラメーターで指定されたコレクション*T*です。既定では、 **TypeArgument**に設定されている**Int32**です。 型 T を変更する、 **ParallelForEach < T\>** アクティビティ デザイナーの値を変更、 **TypeArgument**プロパティ グリッドのコンボ ボックス。|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|反復処理を行う項目のコレクション。 設定する、 <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>、種類 a[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]内の式、**値**ボックスに、 **ForEach < T\>** というヒント テキストが「VB の式を入力してください」のか、ボックス内のアクティビティ デザイナー**値**ボックスに、**プロパティ**ウィンドウです。|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||各イテレーションの完了後に評価されます。 true であると評価する場合、スケジュールされた保留イテレーションはキャンセルされます。 このプロパティが設定されていない場合、スケジュールされたすべてのステートメントは、完了するまで実行されます。|

 既定では、ループ反復子には、item という名前が付けられます。 反復子変数の名前を変更することができます、 **ForEach**ボックス**ParallelForEach\<T >**アクティビティ デザイナー。 ループ反復子は、<xref:System.Activities.Statements.ParallelForEach%601> アクティビティの子の式で使用できます。

## <a name="see-also"></a>関連項目

- [シーケンス](../workflow-designer/sequence-activity-designer.md)
- [並列](../workflow-designer/parallel-activity-designer.md)
- [制御フロー](../workflow-designer/control-flow-activity-designers.md)