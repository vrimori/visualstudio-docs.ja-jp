---
title: テーブル デザイナーのフィルター文字列の作成 |Microsoft Docs
description: テーブル デザイナーのフィルター文字列の作成
author: ghogen
manager: douge
assetId: a1a10ea1-687a-4ee1-a952-6b24c2fe1a22
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: ff8c3dd927e81b9e131242a9a6631a8297046a6e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002872"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>テーブル デザイナーのフィルター文字列の作成
## <a name="overview"></a>概要
Visual Studio に表示される Azure テーブルにデータをフィルター処理する**テーブル デザイナー**、フィルター文字列を作成して、フィルター フィールドに入力します。 フィルター文字列の構文は、WCF Data Services によって定義され、SQL の WHERE 句に似ていますが、HTTP 要求を介して Table service に送信されます。 **テーブル デザイナー**エンコーディングを適切な処理を目的のプロパティの値をフィルター処理する必要がありますのみを入力する、プロパティ名、比較演算子、条件値、および必要に応じて、ブール値であるため、フィルター フィールドの演算子。 URL を使用してテーブルにクエリを作成する場合と同様に、$filter クエリ オプションを含める必要はありません、[ストレージ サービス REST API リファレンス](http://go.microsoft.com/fwlink/p/?LinkId=400447)します。

WCF Data Services がに基づいて、 [Open Data Protocol](http://go.microsoft.com/fwlink/p/?LinkId=214805) (OData)。 フィルター システム クエリ オプションの詳細 (**$filter**) を参照してください、 [OData URI 規則仕様](http://go.microsoft.com/fwlink/p/?LinkId=214806)。

## <a name="comparison-operators"></a>比較演算子
全種類のプロパティは、次の論理演算子がサポートされています。

| 論理演算子 | 説明 | フィルター文字列の例 |
| --- | --- | --- |
| eq |等しい |City eq 'Redmond' |
| gt |次の値より大きい |価格 gt 20 |
| ge |次の値以上 |価格 ge 10 |
| lt |より小さい |価格 lt 20 |
| le |以下 |価格 le 100 |
| ne |等しくない |市区町村 ne 'London' |
| と、呼び出し |および |価格 le 200 および価格 gt 3.5 |
| または |または |価格 le 3.5 または価格 gt 200 |
| not |Not |isAvailable されません。 |

フィルター文字列を構築するときに、次の規則が重要です。

* 論理演算子を使用すると、プロパティに値を比較できます。 動的な値のプロパティと比較することはできませんに注意してください。式の一方の側は、定数でなければなりません。
* フィルター文字列のすべての部分は大文字小文字を区別します。
* 有効な結果を返すフィルターの順序でプロパティと同じデータ型の定数値がある必要があります。 サポートされているプロパティの種類の詳細については、次を参照してください。 [Table サービス データ モデルについて](http://go.microsoft.com/fwlink/p/?LinkId=400448)します。

## <a name="filtering-on-string-properties"></a>文字列プロパティのフィルター処理
文字列プロパティでフィルター処理するときに、文字列定数を単一引用符で囲みます。

次の例では、フィルター、 **PartitionKey**と**RowKey**プロパティはキー以外の追加プロパティをフィルター文字列を追加することもできます。

    PartitionKey eq 'Partition1' and RowKey eq '00001'

必要ありません、かっこで囲まれた各フィルター式を囲むことができます。

    (PartitionKey eq 'Partition1') and (RowKey eq '00001')

Table service はワイルドカードのクエリをサポートしていないか、テーブル デザイナーでサポートするされていない、ことに注意してください。 ただし、目的のプレフィックスに対して比較演算子を使用して、一致するプレフィックスを行うことができます。 次の例では、文字 'A' で始まる LastName プロパティを持つエンティティが返されます。

    LastName ge 'A' and LastName lt 'B'

## <a name="filtering-on-numeric-properties"></a>数値プロパティのフィルター処理
整数または浮動小数点数をフィルターするには、引用符なしの数を指定します。

この例では、値が 30 より大きい Age プロパティを持つすべてのエンティティを返します。

    Age gt 30

この例では、値が 100.25 以下の AmountDue プロパティを持つすべてのエンティティが返されます。

    AmountDue le 100.25

## <a name="filtering-on-boolean-properties"></a>ブール型プロパティのフィルター処理
指定するブール値でフィルター処理、 **true**または**false**引用符なし。

次の例は、IsActive プロパティに設定されているすべてのエンティティを返す**true**:

    IsActive eq true

論理演算子を使用せずには、このフィルター式を記述することもできます。 次の例では、Table service も返しますのすべてのエンティティ、IsActive **true**:

    IsActive

IsActive が false のすべてのエンティティを返すには、not を使用できる演算子。

    not IsActive

## <a name="filtering-on-datetime-properties"></a>DateTime プロパティのフィルター処理
DateTime 値でフィルターするには、指定、 **datetime**キーワード、後ろに単一引用符で日付/時刻の定数。 日付/時刻の定数が結合 UTC 形式である必要があります」の説明に従って[DateTime プロパティ値の書式設定](http://go.microsoft.com/fwlink/p/?LinkId=400449)します。

次の例では、CustomerSince プロパティが 2008 年 7 月 10 日と等しいエンティティを返します。

    CustomerSince eq datetime'2008-07-10T00:00:00Z'
