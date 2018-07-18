---
title: データ クラスの継承 (O R デザイナー)
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
ms.openlocfilehash: c1ed71ad820e6e55d05bc7cc6c7bf62b45f58f55
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921738"
---
# <a name="data-class-inheritance-or-designer"></a>データ クラスの継承 (O/R デザイナー)

[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] クラスは、他のオブジェクトと同様に、継承を使用して他のクラスから派生できます。 コードでは、あるクラスが別のクラスから継承されていることを宣言することによって、オブジェクト間の継承関係を指定できます。 データベースでは、継承関係が複数の方法で作成されます。 [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) では、一般にリレーショナル システムで実装されている単一テーブル継承の概念がサポートされます。

単一テーブル継承では、基本クラスと派生クラスの両方の列が入った単一データベース テーブルが関係します。 リレーショナル データでは、識別子の列に、特定のレコードが属するクラスを決定する値が含まれます。 たとえば、会社に採用されたすべての人を含む Persons テーブルについて考えます。 従業員の人もいれば、管理者の人もいます。 Persons テーブルには、Type という列があり、この列の値は管理者は 1、従業員は 2 です。 Type 列は識別子の列です。 このシナリオでは、従業員のサブクラスを作成して、そのクラスには Type の値が 2 であるレコードだけを入れるようにすることができます。

構成するときの継承エンティティ クラスを使用して、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]、2 回、デザイナーに、継承データを含む 1 つのテーブルをドラッグして: 継承階層内のクラスごとに 1 回です。 デザイナーにテーブルを追加した後に接続を継承項目に、**オブジェクト リレーショナル デザイナー**ツールボックスしの継承プロパティを設定、4、**プロパティ**ウィンドウです。

## <a name="inheritance-properties"></a>継承プロパティ

継承プロパティとその説明については、次の表を参照してください。

|プロパティ|説明|
|--------------|-----------------|
|識別子プロパティ|現在のレコードが属するクラスを判別するプロパティ (列にマップされる)。|
|基本クラスの識別子の値|レコードが基本クラスに属することを決定する、識別子プロパティとして指定された列の値。|
|派生クラスの識別子の値|レコードが派生クラスに属することを決定する、識別子プロパティとして指定されたプロパティの値。|
|継承の既定値|として指定されているプロパティの値を代入するか、クラス、**識別子プロパティ**いずれと一致しない、 **Base Class Discriminator Value**または**派生クラス識別子の値**です。|

継承を使用し、リレーショナル データに対応するオブジェクト モデルの作成は、混乱しやすい場合があります。 このトピックでは、継承を構成する場合に必要な基本的な概念と個々のプロパティについて説明します。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] による継承の構成方法についての詳しい説明については、以下のトピックを参照してください。

|トピック|説明|
|-----------|-----------------|
|[方法: O/R デザイナーを使用して継承を構成します。](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]を使用して単一テーブル継承を使用するエンティティ クラスを構成する方法について説明します。|
|[チュートリアル: 単一テーブル継承 (O/R デザイナー) を使用して LINQ to SQL クラスを作成します。](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]を使用して単一テーブル継承を使用するエンティティ クラスを構成するための詳細な手順を説明します。|

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [チュートリアル: LINQ to SQL クラス (O R デザイナー) を作成します。](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [チュートリアル: 単一テーブル継承 (O/R デザイナー) を使用して LINQ to SQL クラスを作成します。](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [はじめに](/dotnet/framework/data/adonet/sql/linq/getting-started)