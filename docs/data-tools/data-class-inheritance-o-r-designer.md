---
title: データ クラスの継承 (O/R デザイナー)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6c6b17ad38e9aae78975e43797931a326955712d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756738"
---
# <a name="data-class-inheritance-or-designer"></a>データ クラスの継承 (O/R デザイナー)

他のオブジェクトと同様、LINQ to SQL クラスは継承を使用してし、他のクラスから派生できます。 コードでは、あるクラスが別のクラスから継承されていることを宣言することによって、オブジェクト間の継承関係を指定できます。 データベースでは、継承関係が複数の方法で作成されます。 **オブジェクト リレーショナル デザイナー** (**O/R デザイナー**) リレーショナル システムに実装されている多くの場合は、単一テーブル継承の概念をサポートしています。

単一テーブル継承では、基本クラスと派生クラスの両方の列が入った単一データベース テーブルが関係します。 リレーショナル データでは、識別子の列に、特定のレコードが属するクラスを決定する値が含まれます。 たとえば、`Persons`企業で採用されているすべてのユーザーを含むテーブル。 従業員の人もいれば、管理者の人もいます。 `Persons`テーブルには、という名前の列が含まれています。`Type`従業員のマネージャーと 2 の値の 1 の値を持ちます。 `Type`列は、識別子列です。 このシナリオで従業員のサブクラスを作成および設定を持つレコードだけを含むクラス、 `Type` 2 の値。

構成するときの継承エンティティ クラスを使用して、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]、2 回、デザイナーに、継承データを含む 1 つのテーブルをドラッグします。 継承階層内の各クラスに 1 回です。 デザイナーにテーブルを追加した後に接続から継承項目、**オブジェクト リレーショナル デザイナー**ツールボックスし、4 つのセットの継承プロパティで、**プロパティ**ウィンドウ。

## <a name="inheritance-properties"></a>継承プロパティ

継承プロパティとその説明については、次の表を参照してください。

|プロパティ|説明|
|--------------|-----------------|
|**識別子のプロパティ**|現在のレコードが属するクラスを判別するプロパティ (列にマップされる)。|
|**基底クラスの識別子の値**|値 (として指定された列で、**識別子プロパティ**) レコードが基本クラスのことを決定します。|
|**派生クラスの識別子の値**|値 (として指定されたプロパティで、**識別子プロパティ**) レコードが派生クラスのことを決定します。|
|**継承の既定値**|として指定されているプロパティの値が設定されたクラス、**識別子プロパティ**いずれかと一致しない、 **Base Class Discriminator Value**または**クラスの派生識別子の値**します。|

継承を使用し、リレーショナル データに対応するオブジェクト モデルの作成は、混乱しやすい場合があります。 このトピックでは、継承を構成する場合に必要な基本的な概念と個々のプロパティについて説明します。 次のトピックでの継承を構成する方法の詳しい説明についての説明、 **O/R デザイナー**します。

|トピック|説明|
|-----------|-----------------|
|[方法: O/R デザイナーを使用して継承を構成します。](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|使用して単一テーブル継承を使用してエンティティ クラスを構成する方法について説明します、 **O/R デザイナー**します。|
|[チュートリアル: 単一テーブル継承 (O/R デザイナー) を使用して SQL クラスを LINQ を作成します。](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|使用して単一テーブル継承を使用するエンティティ クラスを構成する方法の手順について説明します、 **O/R デザイナー**します。|

## <a name="see-also"></a>関連項目

- [Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成します。](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [チュートリアル: 単一テーブル継承 (O/R デザイナー) を使用して SQL クラスを LINQ を作成します。](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [はじめに](/dotnet/framework/data/adonet/sql/linq/getting-started)