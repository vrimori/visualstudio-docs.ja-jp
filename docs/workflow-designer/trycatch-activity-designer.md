---
title: ワークフロー デザイナー - TryCatch アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2983dd9aa53443c616504672ef76f76ac9bd9add
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="trycatch-activity-designer"></a>TryCatch アクティビティ デザイナー

**TryCatch**アクティビティ デザイナーを使用して作成し、構成、<xref:System.Activities.Statements.TryCatch>アクティビティ。

## <a name="the-trycatch-activity"></a>TryCatch アクティビティ
 <xref:System.Activities.Statements.TryCatch>アクティビティが含まれています、 <xref:System.Activities.Statements.TryCatch.Try%2A> activity、一連の**キャッチ\<TException >** と<xref:System.Activities.Statements.TryCatch.Finally%2A>アクティビティ。 A<xref:System.Activities.Statements.Catch%601>型の**TException**が含まれています、<xref:System.Activities.Statements.Catch%601.ExceptionType%2A>と<xref:System.Activities.Statements.Catch%601.Action%2A>です。 これらの組み合わせによって、標準的な例外ベースのエラー処理機構が実装されます。 <xref:System.Activities.Statements.TryCatch> アクティビティは、対応する <xref:System.Activities.Statements.TryCatch.Try%2A> アクティビティの実行を試みます。 場合、<xref:System.Activities.Statements.TryCatch.Try%2A>アクティビティは、任意の例外をスロー、<xref:System.Activities.Statements.TryCatch>アクティビティはその**キャッチ < TException\>** コレクション、例外を照合します。 、一致がある場合、<xref:System.Activities.Statements.Catch%601.Action%2A>の対応する**キャッチ\<TException >** を実行すると、処理例外のロジック エラーとして機能します。 <xref:System.Activities.Statements.TryCatch.Try%2A> セクションのアクティビティまたは <xref:System.Activities.Statements.TryCatch.Catches%2A> のアクティビティが正常に完了した場合、<xref:System.Activities.Statements.TryCatch> アクティビティは <xref:System.Activities.Statements.TryCatch.Finally%2A> アクティビティを実行します。 詳細については、次を参照してください。 [Windows ワークフローの例外](/dotnet/framework/windows-workflow-foundation/exceptions)です。

### <a name="using-the-trycatch-activity-designer"></a>TryCatch アクティビティ デザイナーの使用
 **TryCatch**アクティビティ デザイナーは含まれて、 **Error Handling**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**ワークフロー デザイナーの左側にあるタブ (または、選択**ツールバー**から、**ビュー**  メニューまたは ctlr 番号と alt キーを押しながら X です)。

 **TryCatch**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**アクティビティを通常配置しているような内の場所に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>です。 この操作により、TryCatch の既定の <xref:System.Activities.Statements.TryCatch> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 <xref:System.Activities.Activity.DisplayName%2A>ヘッダーの値を編集できます、 **TryCatch**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。 画面で、その他のプロパティを編集する必要があります、 **TryCatch**アクティビティ デザイナー。

 右上隅にある展開ボタンをクリックして**TryCatch**デザイナーを表示する、**を再試行してください**、**キャッチ**、および**最後に**ボックスが、展開されたビューを表示します。 Catch を追加する をクリックして、**新しいキャッチの追加**ボタン**TryCatch**デザイナー。 このボタンが、型のコンボ ボックスに変化します。 例外の型を選択し、Enter キーを押して catch を追加します。 追加した後、**キャッチ**catch の領域を展開、およびアクティビティは、catch の実行ロジックを定義する catch にドロップできます。 展開された catch 領域の右側にはテキスト ボックスが表示されます。 このテキスト ボックスを使用して、例外変数に名前を付けることができます。 この例外変数は、同じ内のアクティビティのみ使用できます**キャッチ**です。

 **TryCatch**デザイナーが編集をサポートしていません**キャッチ**です。 例外の種類を変更する場合は、削除する必要が、**キャッチ**し、新しいものを追加します。 A**キャッチ**を選択して削除するかを使用して削除することができます、**削除**[コンテキスト] メニューを右クリックしてアクセスします。

### <a name="the-trycatch-properties"></a>TryCatch のプロパティ
 次の表に、<xref:System.Activities.Statements.TryCatch>プロパティと、デザイナーでの使用方法について説明します。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TryCatch> アクティビティの表示名を指定します (省略可能)。 既定値は TryCatch です。|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|<xref:System.Activities.Statements.TryCatch> を実行すると、このアクティビティが最初に実行されます。|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|コレクション**キャッチ**場合にチェックされる要素、<xref:System.Activities.Statements.TryCatch.Try%2A>アクティビティが例外をスローします。<br /><br /> <xref:System.Activities.Statements.TryCatch.Catches%2A> にアクティビティを少なくとも 1 つ追加するか、または、<xref:System.Activities.Statements.TryCatch.Finally%2A> ブロックにアクティビティを追加する必要があります。|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|<xref:System.Activities.Statements.TryCatch.Try%2A> および <xref:System.Activities.Statements.TryCatch.Catches%2A> コレクション内の必要なアクティビティがすべて完了した段階で実行されるアクティビティ。<br /><br /> <xref:System.Activities.Statements.TryCatch.Catches%2A> にアクティビティを少なくとも 1 つ追加するか、または、<xref:System.Activities.Statements.TryCatch.Finally%2A> ブロックにアクティビティを追加する必要があります。|

## <a name="see-also"></a>関連項目

- [コレクション](../workflow-designer/collection-activity-designers.md)
- [rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)