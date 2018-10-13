---
title: 作成し、Tableadapter の構成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c1c9337fac3cde818fd8af298813c89c8c13daf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199252"
---
# <a name="create-and-configure-tableadapters"></a>Tableadapter の作成および構成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
TableAdapter を使用すると、アプリケーションとデータベース間で通信できます。 データベース、クエリの実行またはストアド プロシージャに接続して、新しいデータを返すか、テーブルまたは既存の fill<xref:System.Data.DataTable>返されたデータ。 Tableadapter は、元のデータベースに、アプリケーションから更新されたデータを送信することもできます。  
  
 次の操作のいずれかを実行するときの Tableadapter が作成されます。  
  
-   実行、[データ ソース構成ウィザード](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)いずれかを選択し、**データベース**または**Web サービス**データ ソースの種類。  
  
-   データベース オブジェクトをドラッグ[サーバー エクスプ ローラー](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d)に、**データセット デザイナー**します。  
  
 新しい TableAdapter を作成してで空の領域に TableAdapter をツールボックスからドラッグしてデータ ソースと構成、**データセット デザイナー**画面。  
  
 Tableadapter の概要については、次を参照してください。 [Tableadapter を使用してデータセットを入力](../data-tools/fill-datasets-by-using-tableadapters.md)します。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="use-the-tableadapter-configuration-wizard"></a>TableAdapter 構成ウィザードを使用  
 実行、 **TableAdapter 構成ウィザード**Tableadapter および関連する Datatable の作成または編集します。 既存の TableAdapter を構成するには、上で右クリックし、**データセット デザイナー**します。  
  
 ![テーブル アダプターの構成ウィザードの raddata](../data-tools/media/raddata-table-adapter-configuration-wizard.png "raddata テーブル アダプターの構成ウィザード")  
  
 新しい TableAdapter をツールボックスからドラッグした場合と、**データセット デザイナー**にフォーカスをウィザードの指示、TableAdapter に接続する必要があるデータ ソースを指定してどのような種類のコマンドは、通信に使用する必要がありますが、データベース、SQL ステートメントまたはストアド プロシージャ。 これは、既にデータ ソースに関連付けられた TableAdapter を構成する場合は表示されなくなります。  
  
-   使用して、**データベースに直接更新を送信するためのメソッドを作成する**オプションは設定に相当、`GenerateDBDirectMethods`プロパティを true にします。 元の SQL ステートメントが十分な情報を提供していないか、クエリは更新可能なクエリではない場合は、オプションは使用できません。 この状態が発生する、たとえば、**参加**クエリと 1 つの (スカラー) 値を返すクエリです。  
  
-   データベースの適切なアクセス許可がある場合、基になるデータベースで、新しいストアド プロシージャを作成するオプションがあります。 これらのアクセス許可を持っていない場合は、このオプションはできません。  
  
-   既存のストアド プロシージャの実行を選択することもできます、**選択**、**挿入**、 **UPDATE**、および**削除**のコマンド、。TableAdapter。 割り当てられているストアド プロシージャ、 **Update**コマンド、たとえばを実行ときに、`TableAdapter.Update()`メソッドが呼び出されます。  
  
     選択したストアド プロシージャのパラメーターを、データ テーブルの対応する列に割り当てます。 たとえば、ストアド プロシージャがという名前のパラメーターを受け取る`@CompanyName`に渡される、 `CompanyName` 、テーブルの列の設定、**基になる列**の`@CompanyName`パラメーターを`CompanyName`。  
  
    > [!NOTE]
    >  SELECT コマンドに割り当てられているストアド プロシージャは、ウィザードの次の手順で名前を付けます TableAdapter のメソッドを呼び出すことによって実行します。 既定の方法は`Fill`ので、通常は、SELECT プロシージャの実行に使用するコードは`TableAdapter.Fill(tableName)`します。 による既定の名前を変更する場合`Fill`、置き換える`Fill`名前の割り当て、および"TableAdapter"を TableAdapter の実際の名前に置き換えます (たとえば、 `CustomersTableAdapter`)。  
  
-   **オプションの高度な**ウィザードで使用するで定義されている SELECT ステートメントに基づいた INSERT、UPDATE、および DELETE のステートメントを生成、 **SQL ステートメントの生成**ページ。 オプティミスティック同時実行を使用し、かどうかを INSERT および UPDATE の後に、データ テーブルを更新するステートメントは実行を指定します。  
  
## <a name="configure-a-tableadapters-fill-method"></a>TableAdapter の塗りつぶし方法を構成します。  
 場合があります、TableAdapter のテーブルのスキーマを変更する可能性があります。 TableAdapter のプライマリを変更するには、`Fill`メソッド。 Tableadapter をプライマリに`Fill`関連付けられたデータ テーブルのスキーマを定義するメソッド。 プライマリ`Fill`方法は、クエリまたはストアド プロシージャの最初に TableAdapter を構成するときに入力したに基づいています。 データセット デザイナーでデータ テーブルの下の最初の (最上位) メソッドになります。  
  
 ![複数のクエリによる TableAdapter](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 変更する TableAdapter のメイン`Fill`メソッドが関連付けられているデータ テーブルのスキーマに反映されます。 たとえば、メインのクエリから列を削除する`Fill`メソッドは、関連付けられたデータ テーブルから列を削除することもできます。 さらに、メインの列を削除する`Fill`メソッド、TableAdapter の他のクエリから列を削除します。  
  
 TableAdapter クエリの構成ウィザードを使用して、作成して、TableAdapter の追加のクエリを編集することができます。 これらの追加のクエリは、スカラー値を返す場合を除き、テーブルのスキーマに従う必要があります。  その他のクエリは、指定した名前を持つ (たとえば、 `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`)。  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>新しいクエリを使用して、TableAdapter クエリ構成ウィザードを開始するには  
  
1.  データセットを開き、**データセット デザイナー**します。  
  
2.  新しいクエリを作成する場合は、ドラッグ、**クエリ**オブジェクトから、**データセット**のタブ、**ツールボックス**上に、 <xref:System.Data.DataTable>、または選択**クエリの追加**TableAdapter のショートカット メニューから。 ドラッグすることも、**クエリ**オブジェクトの空の領域に、**データセット デザイナー**、関連付けられていない TableAdapter を作成する<xref:System.Data.DataTable>します。 これらのクエリを返す単一の (スカラー) 値または実行 UPDATE、INSERT、または、データベースに対するコマンドの削除のみできます。  
  
3.  **データ接続の選択**画面で、選択するか、クエリを使用する接続を作成します。  
  
    > [!NOTE]
    >  この画面は、デザイナーを使用する適切な接続が判断できないときに、または接続が使用できない場合にのみ表示されます。  
  
4.  **コマンドの種類を選択** 画面で、データベースからデータをフェッチする場合の次の方法から選択します。  
  
    -   **SQL ステートメントを使用して**データベースからデータを選択する SQL ステートメントを入力することができます。  
  
    -   **新しいストアド プロシージャ作成**新規に作成するウィザードで有効には、指定した SELECT ステートメントに基づいて、(データベース) 内のプロシージャが格納されています。  
  
    -   **既存のストアド プロシージャを使用して、** クエリを実行するときに、既存のストアド プロシージャを実行することができます。  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>既存のクエリで、TableAdapter クエリ構成ウィザードを開始するには  
  
-   既存の TableAdapter クエリを編集している場合、クエリを右クリックし、**構成**ショートカット メニューから。  
  
    > [!NOTE]
    >  TableAdapter を再構成する TableAdapter のメイン クエリを右クリックし、<xref:System.Data.DataTable>スキーマ。 TableAdapter に追加のクエリを右クリックして、ただし、選択したクエリのみを構成します。 **TableAdapter 構成ウィザード**TableAdapter クエリの構成ウィザードは、選択したクエリのみを再構成中には、TableAdapter の定義を再構成します。  
  
#### <a name="to-add-a-global--query-to-a-tableadapter"></a>TableAdapter にグローバル クエリを追加するには  
  
-   *グローバル クエリ*は 1 つの (スカラー) 値または値を返す SQL クエリ。 通常、グローバル関数は、挿入、更新、削除など、データベース操作を実行します。 テーブルまたは特定の順序ですべてのアイテムの請求額を合計顧客数などの情報を集計します。  
  
     グローバル クエリをドラッグして追加する、**クエリ**オブジェクトから、**データセット**のタブ、**ツールボックス**の空の領域に、**データセット デザイナー**.  
  
-   たとえば、目的のタスクを実行するクエリの指定`SELECT COUNT(*) AS CustomerCount FROM Customers`します。  
  
    > [!NOTE]
    >  ドラッグ、**クエリ**オブジェクトに直接、**データセット デザイナー**スカラー (単一) 値のみを返すメソッドを作成します。 クエリまたはストアド プロシージャを選択する複数の単一の値を返す可能性があります、中に、ウィザードによって作成されるメソッドは、単一の値のみを返します。 たとえば、クエリは、返されるデータの最初の行の最初の列を返す可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [TableAdapters を使用してデータセットを入力する](../data-tools/fill-datasets-by-using-tableadapters.md)

