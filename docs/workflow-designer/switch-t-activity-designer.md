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
ms.openlocfilehash: afa5932ebfaea1e0a7f61997c26e95226ed51b1d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758017"
---
# <a name="switcht-activity-designer"></a>スイッチ\<T > アクティビティ デザイナー

<xref:System.Activities.Statements.Switch%601> アクティビティは、指定した式を評価します。そして、その評価から得られた値と一致する、関連付けられたキーを持つアクティビティを、アクティビティのコレクションから実行します。

**Switch < T\>** 作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.Switch%601>ワークフロー デザイナーでアクティビティ。

## <a name="the-switchtactivity"></a>スイッチ\<T > アクティビティ

<xref:System.Activities.Statements.Switch%601> アクティビティには、<xref:System.Activities.Statements.Switch%601.Expression%2A> と、<xref:System.Activities.Statements.Switch%601.Cases%2A> のディクショナリが含まれます。 ディクショナリ内の各ケースを含むペアで構成を*キー*とそれに対応するとして機能するアクティビティ*値*します。 <xref:System.Activities.Statements.Switch%601> アクティビティは、<xref:System.Activities.Statements.Switch%601.Expression%2A> を評価し、それを各キーと比較します。 一致が見つかった場合は、対応するアクティビティが実行されます。 見つかる一致は 1 つのみです。これは、ディクショナリ キーは、ディクショナリの等値比較子により定義される等価性の型に従って一意である必要があるためです。 一致が検出されない場合は、<xref:System.Activities.Statements.Switch%601.Default%2A> アクティビティが実行されます。

## <a name="how-to-use-the-switcht-activity-designer"></a>スイッチを使用する方法\<T > アクティビティ デザイナー

アクセス、**スイッチ\<T >** 内のアクティビティ デザイナー、**制御フロー**のカテゴリ、**ツールボックス**します。 ワークフロー デザイナーにドロップすると、それが表示されます、**の種類を選択**ジェネリック型を指定できるようにするためのダイアログ*T*で使用される<xref:System.Activities.Statements.Switch%601>アクティビティ。 既定値は**Int32**します。 ジェネリック型では 1 回*T*が選択されている、 **Switch < T\>** デザイナーがワークフロー デザイナーに追加されます。

プロパティは、 **Switch < T\>** デザイナー。 これらのプロパティはすべて、プロパティ グリッドで編集できます。 一部のプロパティは、デザイナー画面で設定することもできます。

次の表に、最も役に立つ <xref:System.Activities.Statements.Switch%601> プロパティと、デザイナーでのその使用方法を示します。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Switch%601> アクティビティ デザイナーの表示名を指定します。 既定値は Switch < Int32\>します。 値を編集できる、**プロパティ**ウィンドウまたはデザイナーのヘッダーで直接します。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|cases コレクション内のキーを比較して、実行する case を決定するために使用される式を指定します。|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||一致が検出されなかった場合に実行するアクティビティを指定します。 をクリックして、**アクティビティを追加** ボタンをデザイナーを開く、**既定**ボックスに、アクティビティを削除できます。|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||評価する case を指定します。 サポート案件を追加する をクリックして、**新しい案件を追加**の下部にあるボタン**スイッチ\<T >** デザイナー。 ボタンがテキスト ボックスに変わります (スイッチを追加するときに、ジェネリック型が選択されている場合に、コンボ ボックス\<T > が String または Enum)。 内のキーを追加した後、**場合値**ボックスで、case の領域を展開し、アクティビティを削除する、ケースの実行ロジックを定義する「アクティビティをドロップここで」ヒント テキスト。|

case キーが重複しない限り、複数の case を追加できます。 case キーが重複している場合は、エラー ダイアログが表示され、指定した case キーが既に存在しているために別のキーを選択する必要があることが示されます。 **スイッチ\<T >** デザイナー、case の領域を 1 つだけは、一度に展開されたビューに存在することができます。 折りたたまれたビューに case の領域が表示されている場合は、case の領域をクリックすると展開されます。 case が折りたたまれており、この case 内にアクティビティが存在する場合は、このアクティビティの表示名が右側に表示されます。 それ以外の場合、表示、**アクティビティを追加**ボタンをクリックした場合は、大文字と小文字を拡張し、アクティビティを追加することができます。

既存の case のキーをクリックすると、キーがラベルからテキスト ボックスに変わり、case キーを編集できます。

case を削除する方法には、次の 2 つがあります。

- case を選択して削除します。

- コンテキスト メニューを表示しを選択する場合は、右クリックして選択**削除**します。

case を削除するには、case 自体を選択する必要があることに注意してください。 case 内のアクティビティを選択して削除すると、case ではなく、アクティビティのみが削除されます。

## <a name="see-also"></a>関連項目

- [制御フロー](../workflow-designer/control-flow-activity-designers.md)