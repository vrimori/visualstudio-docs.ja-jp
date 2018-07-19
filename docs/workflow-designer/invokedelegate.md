---
title: ワークフロー デザイナー - InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e3d802000bede1a654b088fb80b134a36a0185be
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758528"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate**を作成および構成デザイナーを使用する<xref:System.Activities.Statements.InvokeDelegate>アクティビティ。

## <a name="the-invokedelegate-activity"></a>InvokeDelegate アクティビティ

<xref:System.Activities.Statements.InvokeDelegate> はパブリック デリゲートを呼び出します。

### <a name="use-the-invokedelegate-activity-designer"></a>InvokeDelegate アクティビティ デザイナーを使用します。

アクセス、 **InvokeDelegate**内のアクティビティ デザイナー、**プリミティブ**のカテゴリ、**ツールボックス**します。 **InvokeDelegate**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**がずっと、アクティビティを通常配置など内に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>します。 アクティビティ デザイナーをドロップを作成、 <xref:System.Activities.Statements.InvokeDelegate> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>InvokeDelegate の。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、 **InvokeDelegate**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-invokedelegate-properties"></a>InvokeDelegate プロパティ

次の表に、<xref:System.Activities.Statements.InvokeDelegate> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集できるし、一部は、ワークフロー デザイナー画面で編集できます。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeDelegate> アクティビティの表示名。 既定値は InvokeDelegate です。<br /><br /> ただし、<xref:System.Activities.Activity.DisplayName%2A>必須ではありませんいずれかを使用することをお勧めします。|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|アクティビティの実行時に呼び出す <xref:System.Activities.ActivityDelegate> の名前。 このプロパティは、デザイナー画面で編集でき、必須です。|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|呼び出されたデリゲートの引数コレクション。 キーがパラメーター オブジェクトの名前、<xref:System.Activities.ActivityDelegate>式を持つが評価され、対応するパラメーター オブジェクトに割り当てられている引数を値とします。 表示する、 **DelegateArguments** 、このプロパティを設定するダイアログで、省略記号ボタンをクリックして、 **DelegateArguments**プロパティ グリッドのフィールド。 をクリックして、**引数の作成**引数を追加するフィールド。|

## <a name="see-also"></a>関連項目

- [方法: ワークフロー デザイナーでアクティビティ デリゲートを定義および使用する](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)