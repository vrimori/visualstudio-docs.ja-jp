---
title: O/R デザイナーの概要
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 0c4b3c752a2ca28c4cfb4b08b2f51f8b8fc6ac23
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "53894156"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Visual Studio の LINQ to SQL ツール

LINQ to SQL では、Microsoft によってリリースされた最初のオブジェクト リレーショナル マッピング テクノロジをしました。 基本的なシナリオに適していますし、引き続き Visual Studio でサポートされますが、アクティブな開発されていません。 LINQ to SQL、既に使用しているレガシ アプリケーションを保守する際に、または SQL Server を使用して、複数のテーブルのマッピングを必要としない単純なアプリケーションで使用します。 一般に、新しいアプリケーションは、オブジェクト リレーショナル マッパー層が必要な場合、Entity Framework を使用する必要があります。

Visual Studio で、to SQL クラスを使用して SQL テーブルを表す LINQ を作成する、**オブジェクト リレーショナル デザイナー** (**O/R デザイナー**)。

**O/R デザイナー**デザイン サーフェイスに 2 つの領域を持つ: エンティティ ペインで、左側と右側のメソッド ペインです。 エンティティ ペインは、エンティティ クラス、関連付け、および継承階層を表示するメインのデザイン サーフェイスです。 メソッド ペインは、ストアド プロシージャと関数にマッピングされる <xref:System.Data.Linq.DataContext> のメソッドを表示するデザイン サーフェイスです。

**O/R デザイナー**を作成するためのビジュアル デ ザイン サーフェイスを提供します[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)エンティティ クラスと、データベース内のオブジェクトに基づく関連付け (リレーションシップ)。 つまり、 **O/R デザイナー**データベース内のオブジェクトにマップされるアプリケーションでオブジェクト モデルを作成します。 厳密に型も生成<xref:System.Data.Linq.DataContext>エンティティ クラスとデータベース間でデータを送受信します。 **O/R デザイナー**ストアド プロシージャをマップする機能を提供して、関数をも<xref:System.Data.Linq.DataContext>データを返すことをエンティティ クラスを設定するためのメソッド。 最後に、 **O/R デザイナー**エンティティ クラス間の継承関係をデザインする機能を提供します。

## <a name="open-the-or-designer"></a>O/R デザイナーを開く

LINQ to SQL エンティティのモデルをプロジェクトを追加する選択**プロジェクト** > **新しい項目の追加**、し、 **LINQ to SQL クラス**プロジェクト項目の一覧から。

![LINQ to SQL クラス](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio によって作成、 *.dbml*ファイルを開き、ソリューションに追加します。 これは、XML マッピング ファイルとその関連するコード ファイル。

![LINQ to SQL クラスのソリューション エクスプ ローラー](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

選択すると、 *.dbml*ファイルを Visual Studio では、 **O/R デザイナー**画面視覚的にモデルを作成することができます。 次の図は、Northwind の後に、デザイナーを示します`Customers`と`Orders`テーブルからドラッグされた**サーバー エクスプ ローラー**します。 テーブル間のリレーションシップに注意してください。

![LINQ to SQL デザイナー](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> **O/R デザイナー**簡単なオブジェクト リレーショナル マッパーは、1 対 1 のマッピング関係のみをサポートしているためです。 つまり、エンティティ クラスには、データベース テーブルまたはビューとの 1:1 のマッピング関係しか持たせることができません。 参加しているテーブルにエンティティ クラスのマッピングなどの複雑なマッピングはサポートされていません。複雑なマッピングの Entity Framework を使用します。 また、デザイナーは一方向のコード ジェネレーターです。 つまり、デザイナー サーフェイスに加えた変更だけがコード ファイルに反映されます。 コード ファイルを手動で変更は反映されません、 **O/R デザイナー**します。 コード ファイルに手動で加えた変更は、デザイナーを保存してコードを再生成するときに上書きされます。 ユーザー コードを追加し、によって生成されたクラスを拡張する方法については、 **O/R デザイナー**を参照してください[方法。O/R デザイナーで生成されたコードを拡張する

## <a name="create-and-configure-the-datacontext"></a>作成し、DataContext の構成

追加した後、 **LINQ to SQL クラス**項目プロジェクトを開き、 **O/R デザイナー**、空のデザイン サーフェイスは、空を表します<xref:System.Data.Linq.DataContext>構成可能になります。 <xref:System.Data.Linq.DataContext> は、デザイン サーフェイスにドラッグされた最初の項目から提供される接続情報で構成されます。 したがって、<xref:System.Data.Linq.DataContext> は、デザイン サーフェイスにドロップされた最初の項目の接続情報によって構成されます。 詳細については、<xref:System.Data.Linq.DataContext>クラス」を参照して[DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)します。

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>データベース テーブルおよびビューにマップされるエンティティ クラスを作成します。

データベース テーブルおよびビューからドラッグすることにより、テーブルとビューにマッピングされたエンティティ クラスを作成する**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、 **O/R デザイナー**します。 前のセクションで示したように、<xref:System.Data.Linq.DataContext> は、デザイン サーフェイスにドラッグされる最初の項目が提供する接続情報で構成されます。 別の接続を使用する後続の項目を追加するかどうか、 **O/R デザイナー**、用の接続を変更することができます、<xref:System.Data.Linq.DataContext>します。 詳細については、「[方法 :テーブルとビューにマップされた LINQ to SQL クラスを作成する (O/R デザイナー)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)」を参照してください。

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>ストアド プロシージャと関数を呼び出す DataContext メソッドを作成します。

作成することができます<xref:System.Data.Linq.DataContext>メソッドを呼び出す (にマップされる) ストアド プロシージャと関数をドラッグしてから**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、 **O/R デザイナー**. ストアド プロシージャと関数に追加されます、 **O/R デザイナー**のメソッドとして、<xref:System.Data.Linq.DataContext>します。

> [!NOTE]
> ストアド プロシージャおよび関数からのドラッグと**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、 **O/R デザイナー**、戻り値の型を生成された<xref:System.Data.Linq.DataContext>メソッドは、項目をドロップする場所によって異なります。 詳細については、次を参照してください。 [DataContext メソッド (O/r デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)します。

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>ストアド プロシージャを使用してエンティティ クラスとデータベース間でデータを保存する DataContext を構成します。

前に述べたように、ストアド プロシージャと関数を呼び出す <xref:System.Data.Linq.DataContext> のメソッドを作成できます。 さらに、既定の LINQ to SQL のランタイム動作を実行する挿入、更新、および削除に使用されるストアド プロシージャも割り当てることができます。 詳細については、「[方法 :更新、挿入、および削除を実行するストアド プロシージャを割り当てる (O/R デザイナー)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)」を参照してください。

## <a name="inheritance-and-the-or-designer"></a>継承と O/R デザイナー

他のオブジェクトと同様、LINQ to SQL クラスは継承を使用してし、他のクラスから派生できます。 データベースでは、継承関係が複数の方法で作成されます。 **O/R デザイナー**リレーショナル システムに実装されている多くの場合は、単一テーブル継承の概念をサポートしています。 詳細については、「[方法 :O/R デザイナーを使用して継承を構成する](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)」を参照してください。

## <a name="linq-to-sql-queries"></a>LINQ to SQL クエリ

によって作成されたエンティティ クラス、 **O/R デザイナー**で使用できるように設計された[統合言語クエリ (LINQ)](/dotnet/csharp/linq/)します。 詳細については、「[方法 :情報の照会](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information)します。

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>生成された DataContext とエンティティ クラスのコードを異なる名前空間に分割します。

**O/R デザイナー**提供、**コンテキスト Namespace**と**Entity Namespace**プロパティを<xref:System.Data.Linq.DataContext>します。 これらのプロパティは、<xref:System.Data.Linq.DataContext> およびエンティティ クラスのコードが生成される名前空間を決定します。 既定では、これらのプロパティは空であり、<xref:System.Data.Linq.DataContext> およびエンティティ クラスはアプリケーションの名前空間に生成されます。 アプリケーションの名前空間以外の名前空間にコードを生成するには、**[Context Namespace]** プロパティ、**[Entity Namespace]** プロパティ、またはその両方に値を入力します。

## <a name="reference-content"></a>リファレンス コンテンツ

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>関連項目

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [よく寄せられる質問 (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)