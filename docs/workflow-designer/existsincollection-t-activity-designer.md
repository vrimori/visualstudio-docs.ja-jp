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
ms.openlocfilehash: 59ec7e9df4088c21820fa5fec319ab3e4ac10f78
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853260"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T > アクティビティ デザイナー

**ExistsInCollection\<T >** 作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.ExistsInCollection%601>アクティビティ。

## <a name="the-existsincollectiont-activity"></a>ExistsInCollection\<T > アクティビティ

<xref:System.Activities.Statements.ExistsInCollection%601> アクティビティでは、指定した項目が特定のコレクションに存在するかどうかを確認します。

### <a name="using-the-existsincollectiont-activity-designer"></a>ExistsInCollection を使用して\<T > アクティビティ デザイナー

**ExistsInCollection\<T >** アクティビティ デザイナーが記載されて、**コレクション**のカテゴリ、**ツールボックス**をクリックしてアクセスします。**ツールボックス**ワークフロー デザイナーのタブ。 または、選択**ツールボックス**から、**ビュー**メニューのまたはキーを押して**Ctrl**+**Alt** + **X**します。

**ExistsInCollection\<T >** からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**どこにも、アクティビティを通常配置など内に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>します。 これを作成します、 <xref:System.Activities.Statements.ExistsInCollection%601> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>の ExistsInCollection < Int32\>。 (既定で、 *TypeArgument*は**Int32**します。 プロパティ グリッドで変更できます)。<xref:System.Activities.Activity.DisplayName%2A>のヘッダーに値を編集できる、 **ExistsInCollection < T\>** アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。 他のプロパティは、プロパティ グリッドで編集する必要があります。

### <a name="the-existsincollectiont-properties"></a>ExistsInCollection\<T > のプロパティ

次の表は、<xref:System.Activities.Statements.ExistsInCollection%601>プロパティと、デザイナーでの使用方法について説明します。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ExistsInCollection%601> アクティビティの表示名。 既定値は、ExistsInCollection < Int32\>します。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|コレクション内で検索する項目\<T >。 この項目の種類は*T*、型の*TypeArgument*します。 項目を指定するには、プロパティ グリッドで Visual Basic の式を入力します。|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|項目の存在をチェックするためのコレクション。 このコレクションは、型の**ICollection < TypeArgument\>します。** コレクションを指定するには、プロパティ グリッドで Visual Basic の式を入力します。|
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> に格納される項目の T 型。 既定では、この*TypeArgument*に設定されている型**Int32**します。 型を変更するには、値を変更、 *TypeArgument*プロパティ グリッドでコンボ ボックス。|
|<xref:System.Activities.Activity%601.Result%2A>|False|指定した項目がコレクション内に存在するかどうかを示す値。 結果にバインドする変数を指定するには、プロパティ グリッドで Visual Basic 変数を入力します。|

## <a name="see-also"></a>関連項目

- [コレクション](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)