---
title: ワークフロー デザイナー - スイッチ<T>アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37155d7a322b2421fc0c9828d22df8d625f8573a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31978285"
---
# <a name="switcht-activity-designer"></a>スイッチ\<T > アクティビティ デザイナー

<xref:System.Activities.Statements.Switch%601> アクティビティは、指定した式を評価します。そして、その評価から得られた値と一致する、関連付けられたキーを持つアクティビティを、アクティビティのコレクションから実行します。

**Switch < T\>** アクティビティ デザイナーを使用して作成および構成、 <xref:System.Activities.Statements.Switch%601> Windows ワークフロー デザイナーでアクティビティ。

## <a name="the-switchtactivity"></a>スイッチ\<T > アクティビティ

<xref:System.Activities.Statements.Switch%601> アクティビティには、<xref:System.Activities.Statements.Switch%601.Expression%2A> と、<xref:System.Activities.Statements.Switch%601.Cases%2A> のディクショナリが含まれます。 ディクショナリ内の各ケースを含む、ペアから成る、*キー*およびそれに対応する役割を果たすアクティビティ*値*です。 <xref:System.Activities.Statements.Switch%601> アクティビティは、<xref:System.Activities.Statements.Switch%601.Expression%2A> を評価し、それを各キーと比較します。 一致が見つかった場合は、対応するアクティビティが実行されます。 見つかる一致は 1 つのみです。これは、ディクショナリ キーは、ディクショナリの等値比較子により定義される等価性の型に従って一意である必要があるためです。 一致が検出されない場合は、<xref:System.Activities.Statements.Switch%601.Default%2A> アクティビティが実行されます。

## <a name="how-to-use-the-switcht-activity-designer"></a>スイッチを使用する方法\<T > アクティビティ デザイナー

**スイッチ\<T >** アクティビティ デザイナーは含まれて、**制御フロー**のカテゴリ、**ツールボックス**、 をクリックしてアクセスされる**ツールボックス**ワークフロー デザイナーのタブ (または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X です)。ワークフロー デザイナーにドロップすた後、表示、**タイプの選択**ユーザーが、ジェネリック型を指定できるようにするためのダイアログ*T*で使用される<xref:System.Activities.Statements.Switch%601>アクティビティ。 既定値は**Int32**です。 ジェネリック型*T*が選択されている、 **Switch < T\>** デザイナーがワークフロー デザイナーに追加します。

プロパティを次に示します**Switch < T\>** デザイナー。 これらのプロパティはすべて、プロパティ グリッドで編集できます。 一部のプロパティは、デザイナー画面で設定することもできます。

次の表に、最も役に立つ <xref:System.Activities.Statements.Switch%601> プロパティと、デザイナーでのその使用方法を示します。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Switch%601> アクティビティ デザイナーの表示名を指定します。 既定値は Switch < Int32\>です。 値を編集できます、**プロパティ**ウィンドウまたはデザイナーのヘッダーで直接です。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|cases コレクション内のキーを比較して、実行する case を決定するために使用される式を指定します。|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||一致が検出されなかった場合に実行するアクティビティを指定します。 をクリックして、**アクティビティを追加**を開くにはデザイナーでのボタン、**既定**ボックス、アクティビティをドロップできます。|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||評価する case を指定します。 Case を追加しても、**新しいケースを追加**の下部にあるボタン**スイッチ\<T >** デザイナー。 ボタンがテキスト ボックスに変わります (スイッチを追加するときに、ジェネリック型が選択されている場合は、コンボ ボックス\<T > が String または Enum)。 内のキーを追加した後、**場合値**ボックスで、case の領域を展開し、アクティビティをドロップできる、というヒント テキストが"Drop ここにアクティビティ"を case の実行ロジックを定義します。|

case キーが重複しない限り、複数の case を追加できます。 case キーが重複している場合は、エラー ダイアログが表示され、指定した case キーが既に存在しているために別のキーを選択する必要があることが示されます。 **スイッチ\<T >** デザイナーは、1 つだけの case の領域は、一度に拡張ビューに存在することができます。 折りたたまれたビューに case の領域が表示されている場合は、case の領域をクリックすると展開されます。 case が折りたたまれており、この case 内にアクティビティが存在する場合は、このアクティビティの表示名が右側に表示されます。 それ以外の場合を示しています、**アクティビティを追加**ボタンをクリックすると、case が展開をクリックして、アクティビティを追加することができます。

既存の case のキーをクリックすると、キーがラベルからテキスト ボックスに変わり、case キーを編集できます。

case を削除する方法には、次の 2 つがあります。

1.  case を選択して削除します。

2.  選択、ケース、して右クリック コンテキスト メニューを表示して選択**削除**です。

case を削除するには、case 自体を選択する必要があることに注意してください。 case 内のアクティビティを選択して削除すると、case ではなく、アクティビティのみが削除されます。

## <a name="see-also"></a>関連項目

- [制御フロー](../workflow-designer/control-flow-activity-designers.md)