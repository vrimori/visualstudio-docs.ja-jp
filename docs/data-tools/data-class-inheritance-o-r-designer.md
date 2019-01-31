---
title: データ クラスの継承 (O/R デザイナー)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: f0e95466baa4e16e4620ff387a11d4e723399a38
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953394"
---
# <a name="data-class-inheritance-or-designer"></a>データ クラスの継承 (O/R デザイナー)

他のオブジェクトと同様、LINQ to SQL クラスは継承を使用してし、他のクラスから派生できます。 コードでは、あるクラスが別のクラスから継承されていることを宣言することによって、オブジェクト間の継承関係を指定できます。 データベースでは、継承関係が複数の方法で作成されます。 **オブジェクト リレーショナル デザイナー** (**O/R デザイナー**) リレーショナル システムに実装されている多くの場合は、単一テーブル継承の概念をサポートしています。

単一テーブル継承では、基本クラスと派生クラスの両方の列が入った単一データベース テーブルが関係します。 リレーショナル データでは、識別子の列に、特定のレコードが属するクラスを決定する値が含まれます。 たとえば、`Persons`企業で採用されているすべてのユーザーを含むテーブル。 従業員の人もいれば、管理者の人もいます。 `Persons`テーブルには、という名前の列が含まれています。`Type`従業員のマネージャーと 2 の値の 1 の値を持ちます。 `Type`列は、識別子列です。 このシナリオで従業員のサブクラスを作成および設定を持つレコードだけを含むクラス、 `Type` 2 の値。

[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] を使用してエンティティ クラスでの継承を構成する場合、継承データを含んだ単一テーブルをデザイナーに、継承階層のクラスごとに 1 回、計 2 回ドラッグします。 デザイナーにテーブルを追加した後、**[オブジェクト リレーショナル デザイナー]** ツールボックスでそれらのテーブルを継承項目に接続して、**[プロパティ]** ウィンドウで 4 つの継承プロパティを設定します。

## <a name="inheritance-properties"></a>継承プロパティ

継承プロパティとその説明については、次の表を参照してください。

|プロパティ|説明|
|--------------|-----------------|
|**識別子プロパティ**|現在のレコードが属するクラスを判別するプロパティ (列にマップされる)。|
|**基本クラスの識別子の値**|レコードが基本クラスに属することを決定する (**識別子プロパティ**として指定された列の) 値。|
|**派生クラスの識別子の値**|レコードが派生クラスに属することを決定する (**識別子プロパティ**として指定されたプロパティの) 値。|
|**継承の既定値**|として指定されているプロパティの値が設定されたクラス、**識別子プロパティ**いずれかと一致しない、 **Base Class Discriminator Value**または**クラスの派生識別子の値**します。|

継承を使用し、リレーショナル データに対応するオブジェクト モデルの作成は、混乱しやすい場合があります。 このトピックでは、継承を構成する場合に必要な基本的な概念と個々のプロパティについて説明します。 次のトピックでの継承を構成する方法の詳しい説明についての説明、 **O/R デザイナー**します。

|トピック|説明|
|-----------|-----------------|
|[方法: O/R デザイナーを使用して継承を構成する](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|使用して単一テーブル継承を使用してエンティティ クラスを構成する方法について説明します、 **O/R デザイナー**します。|
|[チュートリアル: 単一テーブル継承を使用した LINQ to SQL クラスの作成 (O/R デザイナー)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|使用して単一テーブル継承を使用するエンティティ クラスを構成する方法の手順について説明します、 **O/R デザイナー**します。|

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [チュートリアル: 単一テーブル継承を使用した LINQ to SQL クラスの作成 (O/R デザイナー)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [はじめに](/dotnet/framework/data/adonet/sql/linq/getting-started)