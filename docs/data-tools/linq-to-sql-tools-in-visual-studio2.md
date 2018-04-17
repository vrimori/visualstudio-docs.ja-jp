---
title: Visual Studio O/R デザイナーの概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 09fe5a8cbec1ba1ab5a45abda4c88864e25a1751
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to Visual Studio での SQL ツール
LINQ to SQL では、マイクロソフトによってリリースされた最初のオブジェクト リレーショナル マッピング テクノロジをでした。 基本的なシナリオに適していますし、引き続き Visual Studio でサポートされますが、アクティブな開発ではありません。 LINQ to SQL は既に使用して、従来のアプリケーションを保持する場合または SQL Server を使用して複数のテーブルのマッピングを必要としない単純なアプリケーションを使用します。 一般に、新しいアプリケーションは、オブジェクト リレーショナル マッパー レイヤーが必要な場合、Entity Framework を使用する必要があります。  
  
Visual Studio では、オブジェクト リレーショナル デザイナー (O/R デザイナー) を使用して、SQL テーブルを表す SQL クラスを LINQ を作成します。  
  
[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]デザイン サーフェイスに 2 つの領域を持つ: エンティティ ペインで、左側と右側にメソッド ペインです。 エンティティ ペインは、エンティティ クラス、関連付け、および継承階層を表示するメインのデザイン サーフェイスです。 メソッド ペインは表示するデザイン サーフェイス、<xref:System.Data.Linq.DataContext>ストアド プロシージャおよび関数にマップされているメソッド。  
  
[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 、ビジュアル デザイン画面は、作成する[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)エンティティ クラスとデータベース内のオブジェクトに基づいた関連付け (リレーションシップ)。 つまり、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]は、データベース内のオブジェクトにマップされるオブジェクト モデルをアプリケーションに作成するために使用されます。 また、エンティティ クラスとデータベース間でデータを送受信するために使用する、厳密に型指定された <xref:System.Data.Linq.DataContext> も生成します。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]は、データを返し、エンティティ クラスを設定するために、ストアド プロシージャと関数を <xref:System.Data.Linq.DataContext> のメソッドにマップする機能も提供します。 最後に、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]では、エンティティ クラス間の継承関係をデザインすることもできます。  
  
## <a name="opening-the-or-designer"></a>O/R デザイナーを開く  
 LINQ to SQL エンティティ モデルをプロジェクトを追加する選択**プロジェクト**、**新しい項目の追加**を選択し**LINQ to SQL クラス**プロジェクト項目の一覧から。  
  
 ![LINQ to SQL クラス](../data-tools/media/raddata-linq-to-sql-classes.png "raddata LINQ to SQL クラス")  
  
 Visual Studio では、.dbml ファイルを作成し、ソリューションに追加します。 これは、XML マッピング ファイルとその関連するコード ファイルです。  
  
 ![ソリューション エクスプ ローラーでの LINQ to SQL クラス](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL は、ソリューション エクスプ ローラーでクラス")  
  
 .Dbml ファイルを選択すると、Visual Studio は視覚的にモデルを作成することができます、O/R デザイナー画面を表示します。 サーバー エクスプ ローラーから、Northwind の Customers テーブルと Orders テーブルをドラッグした後、次の図は、デザイナーを示します。 テーブル間のリレーションシップに注意してください。  
  
 ![SQL デザイナーに LINQ](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL デザイナー")  
  
> [!IMPORTANT]
>  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]単純なオブジェクト リレーショナル マッパーでは 1:1 のマッピング関係のみをサポートします。 つまり、エンティティ クラスには、データベース テーブルまたはビューとの 1:1 のマッピング関係しか持たせることができません。 エンティティ クラスをテーブルにマッピングに参加しているなどの複雑なマッピングがサポートされていません。複雑なマッピングの Entity Framework を使用します。 また、デザイナーは一方向のコード ジェネレーターです。 つまり、デザイナー サーフェイスに加えた変更だけがコード ファイルに反映されます。 コード ファイルに手動で加えた変更は、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]に反映されません。 コード ファイルに手動で加えた変更は、デザイナーを保存してコードを再生成するときに上書きされます。 ユーザー コードを追加し、によって生成されたクラスを拡張する方法については、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]を参照してください[する方法: 拡張、O/R デザイナーによって生成されたコード](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md)です。  
  
## <a name="creating-and-configuring-the-datacontext"></a>DataContext の作成と構成  
 追加した後、 **LINQ to SQL クラス**項目をプロジェクトに、開いている、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]、空のデザイン サーフェイスを表す空<xref:System.Data.Linq.DataContext>構成できる状態にします。 <xref:System.Data.Linq.DataContext>がデザイン サーフェイスにドラッグされた最初の項目によって提供される接続情報によって構成されます. したがって、<xref:System.Data.Linq.DataContext>デザイン サーフェイスにドロップされた最初の項目からの接続情報を使用して構成します。 詳細については、<xref:System.Data.Linq.DataContext>クラス」を参照して[DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)です。  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>データベース テーブルおよびビューにマップされるエンティティ クラスの作成  
 データベース テーブルとビューをドラッグして、テーブルとビューにマップされているエンティティ クラスを作成する**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]です。 前のセクションで示したように、<xref:System.Data.Linq.DataContext> は、デザイン サーフェイスにドラッグされる最初の項目が提供する接続情報で構成されます。 別の接続を使用する項目が後で [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]に追加された場合は、<xref:System.Data.Linq.DataContext> の接続を変更できます。 詳細については、次を参照してください。[する方法: LINQ to SQL クラスのテーブルとビュー (O/r デザイナー) にマップに作成](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)です。  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>ストアド プロシージャおよび関数を呼び出す DataContext メソッドの作成  
 作成することができます<xref:System.Data.Linq.DataContext>メソッドを呼び出す (にマップされます) ストアド プロシージャと関数をドラッグしてから**サーバー エクスプ ローラー**/**データベース エクスプ ローラー** に[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. ストアド プロシージャと関数は、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]に <xref:System.Data.Linq.DataContext> のメソッドとして追加されます。  
  
> [!NOTE]
>  ストアド プロシージャと関数をドラッグすると**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]、生成された戻り値の型<xref:System.Data.Linq.DataContext>方法によって異なりますによっては、項目をドロップする場所です。 詳細については、次を参照してください。 [DataContext メソッド (O/r デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)です。  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>ストアド プロシージャを使用してエンティティ クラスとデータベース間でデータを保存するための DataContext の構成  
 前に述べたように、ストアド プロシージャと関数を呼び出す <xref:System.Data.Linq.DataContext> のメソッドを作成できます。 また、挿入、更新、および削除を実行する既定の [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ランタイムの動作の代わりに使用できる、ストアド プロシージャを割り当てることもできます。 詳細については、次を参照してください。[する方法: 更新、挿入、および削除 (O/r デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)です。  
  
## <a name="inheritance-and-the-or-designer"></a>継承と O/R デザイナー  
 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] クラスは、他のオブジェクトと同様に、継承を使用して他のクラスから派生できます。 データベースでは、継承関係が複数の方法で作成されます。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]では、多くのリレーショナル システムに実装されている単一テーブル継承の概念がサポートされています。 詳細については、次を参照してください。[する方法: O/r デザイナーを使用して継承を構成する](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)です。  
  
## <a name="linq-to-sql-queries"></a>LINQ to SQL クエリ  
 によって作成されたエンティティ クラス、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で使用できるように設計された[クエリ (LINQ: Language-Integrated)](/dotnet/csharp/linq/)です。 詳細については、次を参照してください。[する方法: 情報の照会](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information)です。  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>生成された DataContext とエンティティ クラス コードの異なる名前空間への分離  
 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]提供、**コンテキスト Namespace**と**Entity Namespace**プロパティを<xref:System.Data.Linq.DataContext>です。 これらのプロパティは、<xref:System.Data.Linq.DataContext> およびエンティティ クラスのコードが生成される名前空間を決定します。 既定では、これらのプロパティは空であり、<xref:System.Data.Linq.DataContext> およびエンティティ クラスはアプリケーションの名前空間に生成されます。 アプリケーションの名前空間以外の名前空間にコードを生成するに値を入力してください、**コンテキスト Namespace**や**Entity Namespace**プロパティです。
  
## <a name="reference-content"></a>リファレンス コンテンツ
<xref:System.Linq>  
<xref:System.Data.Linq>  
  
## <a name="see-also"></a>関連項目
[LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)    
[よく寄せられる質問 (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions) 