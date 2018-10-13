---
title: InvokeDelegate |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3b47a975c12cfcfd02b01925685b47cba47cc1fc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228853"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate**を作成および構成デザイナーを使用する<xref:System.Activities.Statements.InvokeDelegate>アクティビティ。

## <a name="the-invokedelegate-activity"></a>InvokeDelegate アクティビティ

<xref:System.Activities.Statements.InvokeDelegate> はパブリック デリゲートを呼び出します。

### <a name="using-the-invokedelegate-activity-designer"></a>InvokeDelegate アクティビティ デザイナーの使用

**InvokeDelegate**アクティビティ デザイナーが記載されて、**プリミティブ**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**タブ[!INCLUDE[wfd2](../includes/wfd2-md.md)](または、選択**ツールバー**から、**ビュー**メニューのまたは CRTL + ALT + X)。

**InvokeDelegate**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス場所、アクティビティを通常配置など内、<xref:System.Activities.Statements.Sequence>します。 この操作により、InvokeDelegate という既定の <xref:System.Activities.Statements.InvokeDelegate> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、 **InvokeDelegate**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-invokedelegate-properties"></a>InvokeDelegate プロパティ

次の表に、<xref:System.Activities.Statements.InvokeDelegate> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../includes/wfd2-md.md)]のデザイナー画面で編集できます。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeDelegate> アクティビティの表示名。 既定値は InvokeDelegate です。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|アクティビティの実行時に呼び出す <xref:System.Activities.ActivityDelegate> の名前。 このプロパティは、デザイナー画面で設定することもできます。 これは必須プロパティです。|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|呼び出されたデリゲートの引数コレクション。 キーは <xref:System.Activities.ActivityDelegate> の <xref:System.Activities.DelegateArgument> オブジェクトの名前であり、値は、式が評価され対応する <xref:System.Activities.DelegateArgument> オブジェクトに割り当てられる引数です。 プロパティ グリッドで、省略記号ボタンをクリックします。、 **DelegateArguments**フィールドが表示されます、 **DelegateArguments**ダイアログ ボックスを使用するこのプロパティを設定できます。 をクリックして、**引数の作成**引数を追加するフィールド。|

## <a name="see-also"></a>関連項目

- [方法: ワークフロー デザイナーでアクティビティ デリゲートを定義および使用する](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)