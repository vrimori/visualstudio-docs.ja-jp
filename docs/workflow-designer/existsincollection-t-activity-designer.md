---
title: ワークフロー デザイナー - ExistsInCollection&lt;T&gt;アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c5625f42489752647da57fad9956cff8c64b8f5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T > アクティビティ デザイナー

**ExistsInCollection\<T >** アクティビティ デザイナーを使用して作成し、構成、<xref:System.Activities.Statements.ExistsInCollection%601>アクティビティ。

## <a name="the-existsincollectiont-activity"></a>ExistsInCollection\<T > アクティビティ
 <xref:System.Activities.Statements.ExistsInCollection%601> アクティビティでは、指定した項目が特定のコレクションに存在するかどうかを確認します。

### <a name="using-the-existsincollectiont-activity-designer"></a>使用して、ExistsInCollection\<T > アクティビティ デザイナー
 **ExistsInCollection\<T >** アクティビティ デザイナーは含まれて、**コレクション**のカテゴリ、**ツールボックス**、 をクリックしてアクセスします。**ツールボックス**ワークフロー デザイナーのタブ (または、選択**ツールバー**から、**ビュー**メニューまたは CTRL + ALT + X です)。

 **ExistsInCollection\<T >** からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**アクティビティを通常配置しているような内の場所に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>です。 これを作成、 <xref:System.Activities.Statements.ExistsInCollection%601> 、既定値を持つアクティビティ<xref:System.Activities.Activity.DisplayName%2A>の ExistsInCollection < Int32\>です。 (既定では、 *TypeArgument*は**Int32**です。 プロパティ グリッドで変更できます)。<xref:System.Activities.Activity.DisplayName%2A>ヘッダーの値を編集できます、 **ExistsInCollection < T\>** アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。 他のプロパティは、プロパティ グリッドで編集する必要があります。

### <a name="the-existsincollectiont-properties"></a>ExistsInCollection\<T > のプロパティ
 次の表に、<xref:System.Activities.Statements.ExistsInCollection%601> のプロパティと、デザイナーでのその使用方法を示します。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ExistsInCollection%601> アクティビティの表示名。 既定では、ExistsInCollection < Int32\>です。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|コレクションに追加する項目\<T > です。 この項目の型は*T*の種類は*TypeArgument*です。 項目を指定するには、プロパティ グリッドで Visual Basic の式を入力します。|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|項目の追加先のコレクション。 このコレクションの型は**ICollection < TypeArgument\>です。** コレクションを指定するには、プロパティ グリッドで Visual Basic の式を入力します。|
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> に格納される項目の T 型。 既定では、この*TypeArgument*に設定されている型**Int32**です。 型を変更するには、値を変更、 *TypeArgument*プロパティ グリッドのコンボ ボックスにします。|
|<xref:System.Activities.Activity%601.Result%2A>|False|指定した項目がコレクション内に存在するかどうかを示す値。 結果にバインドする変数を指定するには、プロパティ グリッドで Visual Basic 変数を入力します。|

## <a name="see-also"></a>関連項目

- [コレクション](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)