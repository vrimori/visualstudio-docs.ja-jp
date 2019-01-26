---
title: ワークフロー デザイナー - RemoveFromCollection&lt;T&gt;アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6105668b8511d340200e13c191c532c8743a0b0d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940090"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection\<T > アクティビティ デザイナー

**RemoveFromCollection\<T >** 作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.RemoveFromCollection%601>アクティビティ。

## <a name="the-removefromcollectiontactivity"></a>RemoveFromCollection\<T > アクティビティ

<xref:System.Activities.Statements.RemoveFromCollection%601> アクティビティは、指定した項目を特定のコレクションから削除します。

### <a name="using-the-removefromcollectiont-activity-designer"></a>RemoveFromCollection を使用して\<T > アクティビティ デザイナー

アクセス、 **RemoveFromCollection\<T >** 内のアクティビティ デザイナー、**コレクション**のカテゴリ、**ツールボックス**します。
**RemoveFromCollection\<T >** からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**アクティビティを通常配置など、任意の場所は、ワークフロー デザイナー画面にドロップし、内で、<xref:System.Activities.Statements.Sequence>します。 これを作成します、 <xref:System.Activities.Statements.RemoveFromCollection%601> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>の RemoveFromCollection < Int32\>。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーに値を編集できる、 **RemoveFromCollection < T\>** アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。 他のプロパティは、プロパティ グリッドで編集する必要があります。

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection < T\>プロパティ

次の表は、<xref:System.Activities.Statements.RemoveFromCollection%601>プロパティと、デザイナーでの使用方法について説明します。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.RemoveFromCollection%601> アクティビティの省略可能な表示名。 既定値は、RemoveFromCollection < Int32\>します。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|削除する項目、**コレクション\<T >** します。 この項目の種類は*T*、型の*TypeArgument*します。 項目を指定するには、プロパティ グリッドで Visual Basic の式を入力します。|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|項目を削除する対象のコレクション。 このコレクションは、型の**ICollection < TypeArgument\>します。** コレクションを指定するには、プロパティ グリッドで Visual Basic の式に入力します。|
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> に格納される項目の T 型。 既定では、この*TypeArgument*に設定されている型**Int32**します。 型を変更するには、値を変更、 *TypeArgument*プロパティ グリッドでコンボ ボックス。|
|<xref:System.Activities.Activity%601.Result%2A>|False|指定した項目がコレクションから削除されたかどうかを示す値。 結果にバインドする変数を指定するには、プロパティ グリッドで変数を入力します。|

## <a name="see-also"></a>関連項目

- [コレクション](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)