---
title: Visual Studio O/R デザイナーの概要
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: acb279780db1291d62cde8202268e0990a56ea64
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924081"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Visual Studio での LINQ to SQL ツールします。

LINQ to SQL では、マイクロソフトによってリリースされた最初のオブジェクト リレーショナル マッピング テクノロジをでした。 基本的なシナリオに適していますし、引き続き Visual Studio でサポートされますが、アクティブな開発ではありません。 LINQ to SQL は既に使用して、従来のアプリケーションを保持する場合または SQL Server を使用して複数のテーブルのマッピングを必要としない単純なアプリケーションを使用します。 一般に、新しいアプリケーションは、オブジェクト リレーショナル マッパー レイヤーが必要な場合、Entity Framework を使用する必要があります。

Visual Studio では、オブジェクト リレーショナル デザイナー (O/R デザイナー) を使用して、SQL テーブルを表す SQL クラスを LINQ を作成します。

O/R デザイナーがデザイン サーフェイス上の 2 つの領域: エンティティ ペインで、左側と右側にメソッド ペインです。 エンティティ ペインは、エンティティ クラス、関連付け、および継承階層を表示するメインのデザイン サーフェイスです。 メソッド ペインは表示するデザイン サーフェイス、<xref:System.Data.Linq.DataContext>ストアド プロシージャおよび関数にマップされているメソッド。

O/R デザイナーを作成するため、ビジュアル デザイン画面を提供する[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)エンティティ クラスとデータベース内のオブジェクトに基づいた関連付け (リレーションシップ)。 つまり、O/R デザイナーを使用して、データベース内のオブジェクトにマップされるアプリケーションのオブジェクト モデルを作成します。 また、エンティティ クラスとデータベース間でデータを送受信するために使用する、厳密に型指定された <xref:System.Data.Linq.DataContext> も生成します。 O/R デザイナーもストアド プロシージャにマップする機能を提供し、関数を<xref:System.Data.Linq.DataContext>データを返し、エンティティ クラスを設定するためのメソッドです。 最後に、O/R デザイナーは、エンティティ クラス間の継承関係をデザインする機能を提供します。

## <a name="open-the-or-designer"></a>O/R デザイナーを開く

LINQ to SQL エンティティ モデルをプロジェクトを追加する選択**プロジェクト** > **新しい項目の追加**、し、 **LINQ to SQL クラス**プロジェクト項目の一覧から。

![LINQ to SQL クラス](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio では、.dbml ファイルを作成し、ソリューションに追加します。 これは、XML マッピング ファイルとその関連するコード ファイルです。

![LINQ to SQL クラス ソリューション エクスプ ローラー](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

.Dbml ファイルを選択すると、Visual Studio は視覚的にモデルを作成することができます、O/R デザイナー画面を表示します。 サーバー エクスプ ローラーから、Northwind の Customers テーブルと Orders テーブルをドラッグした後、次の図は、デザイナーを示します。 テーブル間のリレーションシップに注意してください。

![LINQ to SQL デザイナー](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> O/R デザイナーは、1 対 1 のマッピング関係のみをサポートしているため単純なオブジェクト リレーショナル マッパーです。 つまり、エンティティ クラスには、データベース テーブルまたはビューとの 1:1 のマッピング関係しか持たせることができません。 エンティティ クラスをテーブルにマッピングに参加しているなどの複雑なマッピングがサポートされていません。複雑なマッピングの Entity Framework を使用します。 また、デザイナーは一方向のコード ジェネレーターです。 つまり、デザイナー サーフェイスに加えた変更だけがコード ファイルに反映されます。 O/R デザイナーでは、コード ファイルを手動で変更を反映されません。 コード ファイルに手動で加えた変更は、デザイナーを保存してコードを再生成するときに上書きされます。 ユーザー コードを追加し、O/R デザイナーによって生成されたクラスを拡張する方法については、次を参照してください。[する方法: 拡張、O/r デザイナーによって生成されたコード](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md)です。

## <a name="create-and-configure-the-datacontext"></a>作成し、DataContext の構成

追加した後、 **LINQ to SQL クラス**プロジェクトに項目し O/R デザイナーを開き、空のデザイン サーフェイスを表す空<xref:System.Data.Linq.DataContext>構成できる状態にします。 <xref:System.Data.Linq.DataContext>がデザイン サーフェイスにドラッグされた最初の項目によって提供される接続情報によって構成されます. したがって、<xref:System.Data.Linq.DataContext>デザイン サーフェイスにドロップされた最初の項目からの接続情報を使用して構成します。 詳細については、<xref:System.Data.Linq.DataContext>クラス」を参照して[DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)です。

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>データベースのテーブルとビューにマップされるエンティティ クラスを作成します。

データベース テーブルとビューをドラッグして、テーブルとビューにマップされているエンティティ クラスを作成する**サーバー エクスプ ローラー**/**データベース エクスプ ローラー** O/R デザイナーにします。 前のセクションで示したように、<xref:System.Data.Linq.DataContext> は、デザイン サーフェイスにドラッグされる最初の項目が提供する接続情報で構成されます。 接続を変更するには、O/R デザイナーには、別の接続を使用する後続の項目を追加する場合、<xref:System.Data.Linq.DataContext>です。 詳細については、次を参照してください。[する方法: LINQ to SQL クラスのテーブルとビュー (O/r デザイナー) にマップに作成](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)です。

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>ストアド プロシージャと関数を呼び出す DataContext メソッドを作成します。

作成することができます<xref:System.Data.Linq.DataContext>メソッドを呼び出す (にマップされます) ストアド プロシージャと関数をドラッグしてから**サーバー エクスプ ローラー**/**データベース エクスプ ローラー** O/R デザイナーにします。 メソッドとして、ストアド プロシージャおよび関数 O/R デザイナーに追加されたが、<xref:System.Data.Linq.DataContext>です。

> [!NOTE]
> ストアド プロシージャと関数をドラッグすると**サーバー エクスプ ローラー**/**データベース エクスプ ローラー** 、O/R デザイナーで生成された戻り値の型に<xref:System.Data.Linq.DataContext>方法によって異なりますによっては、項目をドロップする場所です。 詳細については、次を参照してください。 [DataContext メソッド (O/r デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)です。

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>DataContext をストアド プロシージャを使用してエンティティ クラスとデータベース間でデータを保存するを構成します。

前に述べたように、ストアド プロシージャと関数を呼び出す <xref:System.Data.Linq.DataContext> のメソッドを作成できます。 さらに、既定の LINQ to SQL ランタイムの動作を実行して挿入、更新、削除に使用できるストアド プロシージャを割り当てることもできます。 詳細については、次を参照してください。[する方法: 更新、挿入、および削除 (O/r デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)です。

## <a name="inheritance-and-the-or-designer"></a>継承と O/R デザイナー

同様に他のオブジェクトでは、LINQ to SQL クラス継承を使用して他のクラスから派生できます。 データベースでは、継承関係が複数の方法で作成されます。 O/R デザイナーは、多くの場合、リレーショナル システムで実装されている単一テーブル継承の概念をサポートします。 詳細については、次を参照してください。[する方法: O/r デザイナーを使用して継承を構成する](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)です。

## <a name="linq-to-sql-queries"></a>LINQ to SQL クエリ

O/R デザイナーで作成されたエンティティ クラスがで使用するために設計された[統合言語クエリ (LINQ)](/dotnet/csharp/linq/)です。 詳細については、次を参照してください。[する方法: 情報の照会](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information)です。

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>生成された DataContext とエンティティ クラスのコードを分割して異なる名前空間

O/R デザイナーは、提供、**コンテキスト Namespace**と**Entity Namespace**プロパティを<xref:System.Data.Linq.DataContext>です。 これらのプロパティは、<xref:System.Data.Linq.DataContext> およびエンティティ クラスのコードが生成される名前空間を決定します。 既定では、これらのプロパティは空であり、<xref:System.Data.Linq.DataContext> およびエンティティ クラスはアプリケーションの名前空間に生成されます。 アプリケーションの名前空間以外の名前空間にコードを生成するに値を入力してください、**コンテキスト Namespace**や**Entity Namespace**プロパティです。

## <a name="reference-content"></a>リファレンス コンテンツ

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>関連項目

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [よく寄せられる質問 (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)