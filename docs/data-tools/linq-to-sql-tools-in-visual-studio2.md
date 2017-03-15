---
title: "LINQ to SQL ツール Visual Studio2 で | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# LINQ to Visual Studio での SQL ツール
LINQ to SQL では、マイクロソフトによってリリースされた最初のオブジェクト リレーショナル マッピング テクノロジはでした。 これは、基本的なシナリオに適してはで、引き続き Visual Studio でサポートされるが不要になった開発します。 LINQ to SQL、既に使用しているレガシ アプリケーションを保守する際にまたはを SQL Server を使用して複数のテーブルのマッピングを必要としない単純なアプリケーションを使用します。 一般に、オブジェクト リレーショナル マッパー レイヤーが必要な場合は、新しいアプリケーションは Entity Framework を使用する必要があります。  
  
 Visual Studio で、作成 LINQ to SQL クラスを使用して SQL テーブルを表す、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]です。  
  
  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 、デザイン サーフェイスに 2 つの領域を持つ: エンティティ ペインで、左側と右側のメソッド ペインです。 エンティティ ペインは、エンティティ クラス、関連付け、および継承階層を表示するメインのデザイン サーフェイスです。 メソッド ペインは表示するデザイン サーフェイス、 <xref:System.Data.Linq.DataContext> ストアド プロシージャおよび関数にマップされるメソッドです。  
  
  [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) を作成するためのビジュアル デ ザイン サーフェイスを提供 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md) エンティティ クラスとデータベース内のオブジェクトに基づく関連付け (リレーションシップ) です。 つまり、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]は、データベース内のオブジェクトにマップされるオブジェクト モデルをアプリケーションに作成するために使用されます。 生成することも、厳密に型指定された <xref:System.Data.Linq.DataContext> エンティティ クラスとデータベース間でデータの送受信に使用されます。  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] にストアド プロシージャをマップする機能を提供し、関数を <xref:System.Data.Linq.DataContext> データを返し、エンティティ クラスを設定するためのメソッドです。 最後に、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]では、エンティティ クラス間の継承関係をデザインすることもできます。  
  
## <a name="opening-the-or-designer"></a>O/R デザイナーを開く  
 LINQ to SQL エンティティ モデルをプロジェクトに追加する **プロジェクトと #124 文字です。新しい項目の追加** にして  **LINQ to SQL クラス** プロジェクト項目の一覧から。  
  
 ![LINQ to SQL クラス](../data-tools/media/raddata-linq-to-sql-classes.png "raddata LINQ to SQL Classes")  
  
 Visual Studio では、.dbml ファイルを作成し、ソリューションに追加します。 これは、XML マッピング ファイルとその関連するコード ファイルです。  
  
 ![LINQ to SQL クラスのソリューション エクスプ ローラー](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL classes in Solution Explorer")  
  
 .Dbml ファイルを選択すると、Visual Studio は視覚的にモデルを作成することができます、O/R デザイナー画面を表示します。 次の図は、サーバー エクスプ ローラーから、Northwind の Customers テーブルと Orders テーブルをドラッグした後に、デザイナーを示します。 テーブル間のリレーションシップに注意してください。  
  
 ![LINQ to SQL デザイナー](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL Designer")  
  
> [!IMPORTANT]
>   [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 単純なオブジェクト リレーショナル マッパーは、1 対 1 のマッピング関係のみがサポートしているためです。 つまり、エンティティ クラスには、データベース テーブルまたはビューとの 1:1 のマッピング関係しか持たせることができません。 エンティティ クラスの結合テーブルへのマッピングなどの複雑なマッピングがサポートされていません。複雑なマッピングの Entity Framework を使用します。 また、デザイナーは一方向のコード ジェネレーターです。 つまり、デザイナー サーフェイスに加えた変更だけがコード ファイルに反映されます。 コード ファイルに手動で加えた変更は、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]に反映されません。 コード ファイルに手動で加えた変更は、デザイナーを保存してコードを再生成するときに上書きされます。 ユーザー コードを追加し、によって生成されたクラスを拡張する方法については、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], を参照してください [方法: 拡張、O/R デザイナーによって生成されたコード](../Topic/How%20to:%20Extend%20Code%20Generated%20by%20the%20O-R%20Designer.md)します。  
  
## <a name="creating-and-configuring-the-datacontext"></a>DataContext の作成と構成  
 追加した後、 **LINQ to SQL クラス** 項目がプロジェクトに、開いている、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], 、空のデザイン サーフェイスを表す空 <xref:System.Data.Linq.DataContext> 構成できる状態にします。  <xref:System.Data.Linq.DataContext> デザイン サーフェイスにドラッグされる最初の項目によって提供される接続情報で構成されます. したがって、 <xref:System.Data.Linq.DataContext> デザイン サーフェイスにドロップされた最初の項目からの接続情報を使用して構成します。 詳細については、 <xref:System.Data.Linq.DataContext> クラスでは、「 [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)します。  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>データベース テーブルおよびビューにマップされるエンティティ クラスの作成  
 データベース テーブルやビューをドラッグすることにより、テーブルとビューにマッピングされたエンティティ クラスを作成する **サーバー エクスプ ローラー**/**データベース エクスプ ローラー** 上に、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]です。 前のセクションで示すとおり、 <xref:System.Data.Linq.DataContext> デザイン サーフェイスにドラッグされる最初の項目によって提供される接続情報で構成されます。 別の接続を使用する後続の項目を追加するかどうか、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], 、用の接続を変更することができます、 <xref:System.Data.Linq.DataContext>します。 詳細については、次を参照してください。 [方法: LINQ to SQL クラスのテーブルとビュー (O/r デザイナー) にマップに作成](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md)します。  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>ストアド プロシージャおよび関数を呼び出す DataContext メソッドの作成  
 作成することができます <xref:System.Data.Linq.DataContext> メソッドを呼び出す (にマップされる) ストアド プロシージャおよび関数をドラッグしてから **サーバー エクスプ ローラー**/**データベース エクスプ ローラー** 上に、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]です。 ストアド プロシージャおよび関数が追加されている場合に、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] のメソッドとして、 <xref:System.Data.Linq.DataContext>します。  
  
> [!NOTE]
>  ストアド プロシージャと関数をドラッグすると **サーバー エクスプ ローラー**/**データベース エクスプ ローラー** 上に、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], 、戻り値の型を生成された <xref:System.Data.Linq.DataContext> メソッドは、項目をドロップする場所によって異なります。 詳細については、次を参照してください。 [DataContext メソッド (O/r デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)します。  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>ストアド プロシージャを使用してエンティティ クラスとデータベース間でデータを保存するための DataContext の構成  
 前述のように、作成 <xref:System.Data.Linq.DataContext> ストアド プロシージャおよび関数を呼び出すメソッド。 また、挿入、更新、および削除を実行する既定の [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ランタイムの動作の代わりに使用できる、ストアド プロシージャを割り当てることもできます。 詳細については、次を参照してください。 [方法: 更新、挿入、および削除 (O/r デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)します。  
  
## <a name="inheritance-and-the-or-designer"></a>継承と O/R デザイナー  
 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] クラスは、他のオブジェクトと同様に、継承を使用して他のクラスから派生できます。 データベースでは、継承関係が複数の方法で作成されます。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]では、多くのリレーショナル システムに実装されている単一テーブル継承の概念がサポートされています。 詳細については、次を参照してください。 [方法: O/r デザイナーを使用して継承を構成する](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)です。  
  
## <a name="linq-to-sql-queries"></a>LINQ to SQL クエリ  
 作成されるエンティティ クラス、 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] で使用できるように設計された [LINQ (Language-Integrated Query)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)します。 詳細については、次を参照してください。 [方法: 情報の照会](../Topic/How%20to:%20Query%20for%20Information.md)します。  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>生成された DataContext とエンティティ クラス コードの異なる名前空間への分離  
  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 提供、 **Context Namespace** と **Entity Namespace** プロパティを <xref:System.Data.Linq.DataContext>します。 これらのプロパティは、名前空間を調べる、 <xref:System.Data.Linq.DataContext> およびにエンティティ クラスのコードを生成します。 既定では、これらのプロパティは空と <xref:System.Data.Linq.DataContext> およびエンティティ クラスは、アプリケーションの名前空間に生成します。 アプリケーションの名前空間以外に、コードを生成するに値を入力してください、 **Context Namespace** や **Entity Namespace** プロパティです。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataContext メソッド (O/R デザイナー)](../data-tools/datacontext-methods-o-r-designer.md)  
 何かについて説明 <xref:System.Data.Linq.DataContext> メソッドと作成方法について説明します。  
  
 [データ クラスの継承 (O/R デザイナー)](../data-tools/data-class-inheritance-o-r-designer.md)  
 単一テーブル継承の概念と、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]におけるその実装方法について説明します。  
  
 [方法: LINQ to SQL クラスのテーブルとビュー (O/R デザイナー) にマップを作成](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md)  
 データベース内のテーブルとビューにマップされるエンティティ クラスの作成方法について説明します。  
  
 [方法: LINQ to SQL クラス (O/R デザイナー) の間の関連付け (リレーションシップ) の作成](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)  
 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] エンティティ クラス間にリレーションシップを作成する方法について説明します。  
  
 [方法: ストアド プロシージャおよび関数 (O/R デザイナー) にマップされる DataContext メソッドの作成](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)  
 作成する方法について説明 <xref:System.Data.Linq.DataContext> メソッドが呼び出されると、ストアド プロシージャまたは関数を実行します。  
  
 [方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
 構成する方法について説明する <xref:System.Data.Linq.DataContext> エンティティからデータを保存する場合は、ストアド プロシージャを使用するクラスは、データベースをバックアップします。  
  
 [方法: DataContext メソッド (O/R デザイナー) の戻り値の型を変更します。](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)  
 戻り値の型を設定する方法について説明、 <xref:System.Data.Linq.DataContext> 、エンティティ クラスの型または O/R デザイナーで作成された自動生成された型にするメソッドです。  
  
 [方法: エンティティ クラスに検証を追加](../data-tools/how-to-add-validation-to-entity-classes.md)  
 プロパティの変更中およびエンティティ クラスの更新中にコードを追加できるようにする部分メソッドの生成方法について説明します。  
  
 [方法: 複数形化のオンとオフ (O/R デザイナー)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)  
 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]に追加されるクラスの自動的な名前変更をオンまたはオフにする方法について説明します。  
  
 [方法: O/R デザイナーを使用して継承を構成します。](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)  
 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で単一テーブル継承を使用してエンティティ クラスを構成する方法について説明します。  
  
 [方法: O/R デザイナーによって生成されたコードを拡張します。](../Topic/How%20to:%20Extend%20Code%20Generated%20by%20the%20O-R%20Designer.md)  
 O/R デザイナー上でのオブジェクトの変更によってコードが再生成されても上書きされないコードの追加方法と、そのようなコードを追加する場所について説明します。  
  
 [チュートリアル: 単一テーブル継承 (O/R デザイナー) を使用して LINQ to SQL クラスを作成します。](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)  
 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で単一テーブル継承を使用してエンティティ クラスを構成するための詳細な手順を示します。  
  
 [チュートリアル: のカスタマイズ、挿入、更新、およびエンティティ クラスの動作を削除](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
 構成する手順については、 <xref:System.Data.Linq.DataContext> エンティティからデータを保存する場合は、ストアド プロシージャを使用するクラスは、データベースをバックアップします。  
  
## <a name="reference-content"></a>リファレンス コンテンツ  
 <xref:System.Linq>  
  
 <xref:System.Data.Linq>  
  
## <a name="see-also"></a>「  
 [.NET 用の visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [よく寄せられる質問](../Topic/Frequently%20Asked%20Questions.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Visual Studio でのデータにアクセスします。](../data-tools/accessing-data-in-visual-studio.md)