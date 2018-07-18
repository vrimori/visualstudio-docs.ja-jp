---
title: ワークフロー デザイナー - AddToCollection<T>アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b32df48f79d60500cb23a40c5273ceeedfc9c56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976703"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T > アクティビティ デザイナー

**AddToCollection\<T >** アクティビティ デザイナーを使用して作成し、構成、<xref:System.Activities.Statements.AddToCollection%601>アクティビティ。

## <a name="the-addtocollectiont-activity"></a>AddToCollection\<T > アクティビティ

<xref:System.Activities.Statements.AddToCollection%601> アクティビティでは、項目をコレクションに追加します。

### <a name="using-the-addtocollectiont-activity-designer"></a>使用して、AddToCollection\<T > アクティビティ デザイナー

**AddToCollection\<T >** アクティビティ デザイナーは含まれて、**コレクション**のカテゴリ、**ツールボックス**、 をクリックしてアクセスします。**ツールボックス**、ワークフロー デザイナーのタブ (または、選択**ツールバー**から、**ビュー**メニューまたは CTRL + ALT + X です)。

**AddToCollection\<T >** からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**アクティビティを配置しているなど、内に限り、ワークフローデザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>. 削除する、 **AddToCollection\<T >** アクティビティ デザイナーを作成、 <xref:System.Activities.Statements.AddToCollection%601> 、既定値を持つアクティビティ<xref:System.Activities.Activity.DisplayName%2A>の AddToCollection < Int32\>です。 (既定では、 *TypeArgument*は**Int32**です。 TypeArgument は、プロパティ グリッドでします。)<xref:System.Activities.Activity.DisplayName%2A>ヘッダーの値を編集できます、 **AddToCollection < T\>** アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。 他のプロパティは、プロパティ グリッドで編集する必要があります。

### <a name="the-addtocollectiont-properties"></a>AddToCollection\<T > のプロパティ

次の表に、<xref:System.Activities.Statements.AddToCollection%601> のプロパティと、デザイナーでのその使用方法を示します。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.AddToCollection%601> アクティビティの表示名。 既定値は AddToCollection < Int32\>です。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|コレクションに追加する項目\<T > です。 この項目の型は*T*、種類がある*TypeArgument*です。 項目を指定するには、プロパティ グリッドで Visual Basic の式を入力します。|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|項目の追加先のコレクション。 このコレクションの型は**ICollection < TypeArgument\>** です。 コレクションを指定するには、プロパティ グリッドで Visual Basic の式を入力します。|
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> に格納される項目の T 型。 既定では、この*TypeArgument*に設定されている型**Int32**です。 型を変更するには、値を変更、 *TypeArgument*プロパティ グリッドのコンボ ボックスにします。|

## <a name="see-also"></a>関連項目

- [コレクション](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T > アクティビティ デザイナー](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)