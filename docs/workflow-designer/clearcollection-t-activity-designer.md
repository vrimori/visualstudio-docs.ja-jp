---
title: ワークフロー デザイナーの操作により、ClearCollection<T>アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 026745a95f4f2a33d0647ff340eb7b1d3a0a92d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866702"
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection\<T > アクティビティ デザイナー

**ClearCollection\<T >** 作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.ClearCollection%601>アクティビティ。

## <a name="the-clearcollectiont-activity"></a>ClearCollection\<T > アクティビティ

<xref:System.Activities.Statements.ClearCollection%601> アクティビティで、指定したすべての項目のコレクションをクリアします。

### <a name="using-the-clearcollectiont-activity-designer"></a>ClearCollection を使用して\<T > アクティビティ デザイナー

**ClearCollection\<T >** アクティビティ デザイナーが記載されて、**コレクション**のカテゴリ、**ツールボックス**をクリックしてアクセスします。**ツールボックス**ワークフロー デザイナーのタブ。 または、選択**ツールボックス**から、**ビュー**メニューのまたはキーを押して**Ctrl**+**Alt** + **X**します。

**ClearCollection\<T >** からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**アクティビティを配置して、このような内で任意の場所は、ワークフローデザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>. アクティビティ デザイナーをドロップする作成されます、 <xref:System.Activities.Statements.ClearCollection%601> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>の ClearCollection < Int32\>。 (既定で、 *TypeArgument*は**Int32**します。 TypeArgument はプロパティ グリッドでします。)<xref:System.Activities.Activity.DisplayName%2A>のヘッダーに値を編集できる、 **ClearCollection < T\>** アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。 他のプロパティは、プロパティ グリッドで編集する必要があります。

### <a name="the-clearcollectiont-properties"></a>ClearCollection\<T > のプロパティ

次の表に、<xref:System.Activities.Statements.ClearCollection%601> のプロパティと、デザイナーでのその使用方法を示します。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ClearCollection%601> アクティビティの表示名を指定します (省略可能)。 既定値は ClearCollection < Int32\>します。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|クリアする項目のコレクションを指定します。 このコレクションは、型の**ICollection\<TypeArgument >。** コレクションを指定するには、プロパティ グリッドで Visual Basic の式を入力します。|
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> に格納される項目の T 型を指定します。 既定では、この*TypeArgument*に設定されている型**Int32**します。 型を変更するには、値を変更、 *TypeArgument*プロパティ グリッドでコンボ ボックス。|

## <a name="see-also"></a>関連項目

- [コレクション](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)