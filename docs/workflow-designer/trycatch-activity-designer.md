---
title: ワークフロー デザイナー - TryCatch アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a4a62b660f2deb2b3ab3a092cdfd586a56b2bcb8
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269814"
---
# <a name="trycatch-activity-designer"></a>TryCatch アクティビティ デザイナー

**TryCatch**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.TryCatch>アクティビティ。

## <a name="the-trycatch-activity"></a>TryCatch アクティビティ
 <xref:System.Activities.Statements.TryCatch>アクティビティが含まれています、<xref:System.Activities.Statements.TryCatch.Try%2A>アクティビティ、一連の**キャッチ\<TException >** と<xref:System.Activities.Statements.TryCatch.Finally%2A>アクティビティ。 A<xref:System.Activities.Statements.Catch%601>型の**TException**が含まれています、<xref:System.Activities.Statements.Catch%601.ExceptionType%2A>と<xref:System.Activities.Statements.Catch%601.Action%2A>します。 これらの組み合わせによって、標準的な例外ベースのエラー処理機構が実装されます。 <xref:System.Activities.Statements.TryCatch> アクティビティは、対応する <xref:System.Activities.Statements.TryCatch.Try%2A> アクティビティの実行を試みます。 場合、<xref:System.Activities.Statements.TryCatch.Try%2A>アクティビティはすべての例外をスローします、<xref:System.Activities.Statements.TryCatch>アクティビティでその**キャッチ < TException\>** 例外と一致するコレクション。 一致がある場合、<xref:System.Activities.Statements.Catch%601.Action%2A>の対応する**キャッチ\<TException >** を実行すると、エラー処理ロジックを例外として機能します。 <xref:System.Activities.Statements.TryCatch.Try%2A> セクションのアクティビティまたは <xref:System.Activities.Statements.TryCatch.Catches%2A> のアクティビティが正常に完了した場合、<xref:System.Activities.Statements.TryCatch> アクティビティは <xref:System.Activities.Statements.TryCatch.Finally%2A> アクティビティを実行します。 詳細については、次を参照してください。 [Windows ワークフローの例外](/dotnet/framework/windows-workflow-foundation/exceptions)します。

### <a name="using-the-trycatch-activity-designer"></a>TryCatch アクティビティ デザイナーの使用

アクセス、 **TryCatch**内のアクティビティ デザイナー、**エラー処理**のカテゴリ、**ツールボックス**します。

**TryCatch**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**どこにも、アクティビティを通常配置など内に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>します。 この操作により、TryCatch の既定の <xref:System.Activities.Statements.TryCatch> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーに値を編集できる、 **TryCatch**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。 画面で、その他のプロパティを編集する必要があります、 **TryCatch**アクティビティ デザイナー。

上の右上隅にある展開ボタンをクリックします**TryCatch**デザイナーを参照してください、**お試しください**、**キャッチ**、と**最後に**ボックスで、。展開ビュー。 Catch を追加するには、クリックして、**新しいキャッチの追加**ボタン**TryCatch**デザイナー。 このボタンが、型のコンボ ボックスに変化します。 例外の型を選択し、Enter キーを押して catch を追加します。 追加した後、**キャッチ**catch の領域を展開および catch の実行ロジックを定義する catch にアクティビティをドロップできます。 展開された catch 領域の右側にはテキスト ボックスが表示されます。 このテキスト ボックスを使用して、例外変数に名前を付けることができます。 例外変数は、同じアクティビティにのみ使用できます**キャッチ**します。

**TryCatch**デザイナーが編集をサポートしていません**キャッチ**します。 例外の種類を変更する場合は、削除する必要が、**キャッチ**新しいアカウントを追加します。 A**キャッチ**を選択し、削除、または選択して削除できます**削除**を右クリックしてアクセスされるコンテキスト メニュー。

### <a name="the-trycatch-properties"></a>TryCatch のプロパティ

次の表は、<xref:System.Activities.Statements.TryCatch>プロパティと、デザイナーでの使用方法について説明します。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TryCatch> アクティビティの表示名を指定します (省略可能)。 既定値は TryCatch です。|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|<xref:System.Activities.Statements.TryCatch> を実行すると、このアクティビティが最初に実行されます。|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|コレクション**キャッチ**された場合にチェックする要素、<xref:System.Activities.Statements.TryCatch.Try%2A>アクティビティが例外をスローします。<br /><br /> <xref:System.Activities.Statements.TryCatch.Catches%2A> にアクティビティを少なくとも 1 つ追加するか、または、<xref:System.Activities.Statements.TryCatch.Finally%2A> ブロックにアクティビティを追加する必要があります。|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|<xref:System.Activities.Statements.TryCatch.Try%2A> および <xref:System.Activities.Statements.TryCatch.Catches%2A> コレクション内の必要なアクティビティがすべて完了した段階で実行されるアクティビティ。<br /><br /> <xref:System.Activities.Statements.TryCatch.Catches%2A> にアクティビティを少なくとも 1 つ追加するか、または、<xref:System.Activities.Statements.TryCatch.Finally%2A> ブロックにアクティビティを追加する必要があります。|

## <a name="see-also"></a>関連項目

- [コレクション](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)