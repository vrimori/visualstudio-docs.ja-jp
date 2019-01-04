---
title: ワークフロー デザイナー - AddToCollection<T>アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd8e92baa4192d0b40acdc1d51d01ea339b528c8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926751"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T > アクティビティ デザイナー

**AddToCollection\<T >** 作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.AddToCollection%601>アクティビティ。

## <a name="the-addtocollectiont-activity"></a>AddToCollection\<T > アクティビティ

<xref:System.Activities.Statements.AddToCollection%601> アクティビティでは、項目をコレクションに追加します。

### <a name="using-the-addtocollectiont-activity-designer"></a>AddToCollection を使用して\<T > アクティビティ デザイナー

**AddToCollection\<T >** アクティビティ デザイナーが記載されて、**コレクション**のカテゴリ、**ツールボックス**をクリックしてアクセスします。**ツールボックス**ワークフロー デザイナーのタブ。 または、選択**ツールボックス**から、**ビュー**メニューのまたはキーを押して**Ctrl**+**Alt** + **X**します。

**AddToCollection\<T >** からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**アクティビティを配置して、このような内で任意の場所は、ワークフローデザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>. 削除、 **AddToCollection\<T >** アクティビティ デザイナーを作成、 <xref:System.Activities.Statements.AddToCollection%601> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>AddToCollection の < Int32\>します。 (既定で、 *TypeArgument*は**Int32**します。 TypeArgument はプロパティ グリッドでします。)<xref:System.Activities.Activity.DisplayName%2A>のヘッダーに値を編集できる、 **AddToCollection < T\>** アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。 他のプロパティは、プロパティ グリッドで編集する必要があります。

### <a name="the-addtocollectiont-properties"></a>AddToCollection\<T > のプロパティ

次の表に、<xref:System.Activities.Statements.AddToCollection%601> のプロパティと、デザイナーでのその使用方法を示します。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.AddToCollection%601> アクティビティの表示名。 既定値は AddToCollection < Int32\>します。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|コレクションに追加する項目\<T >。 この項目の種類は*T*、型の*TypeArgument*します。 項目を指定するには、プロパティ グリッドで Visual Basic の式を入力します。|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|項目の追加先のコレクション。 このコレクションは、型の**ICollection < TypeArgument\>** します。 コレクションを指定するには、プロパティ グリッドで Visual Basic の式を入力します。|
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> に格納される項目の T 型。 既定では、この*TypeArgument*に設定されている型**Int32**します。 型を変更するには、値を変更、 *TypeArgument*プロパティ グリッドでコンボ ボックス。|

## <a name="see-also"></a>関連項目

- [コレクション](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T > アクティビティ デザイナー](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)