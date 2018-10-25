---
title: TableAdapters の編集 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.dbtablefunctionwizard
- vs.datasource.datacomponentquerywizard
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data component queries
- data [Visual Studio], TableAdapters
- TableAdapter Query Configuration Wizard
- data [Visual Studio], table adapter queries
ms.assetid: 8c06b306-24d0-4521-948d-07e3b7badd95
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b242f8154f31391d168f2a41bfd00c01f037d87e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877648"
---
# <a name="editing-tableadapters"></a>TableAdapters の編集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

場合によってアダプターのテーブルのスキーマを変更します。 アダプターのプライマリを変更するには、`Fill`メソッド。 Tableadapter を main に`Fill`関連付けられたデータ テーブルのスキーマを定義するメソッド。 メイン`Fill`メソッドは、クエリに基づくまたは最初に TableAdapter を構成するときに入力したストアド プロシージャはデータ テーブルの下の最初の (最上位) メソッドでは、[の作成と型指定されたデータセットの編集](../data-tools/creating-and-editing-typed-datasets.md)します。  
  
 ![複数のクエリによる TableAdapter](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 変更する TableAdapter のメイン`Fill`メソッドが関連付けられているデータ テーブルのスキーマに反映されます。 たとえば、メインのクエリから列を削除する`Fill`メソッドは、関連付けられたデータ テーブルから列を削除することもできます。 さらに、メインの列を削除する`Fill`メソッド、TableAdapter の他のクエリから列を削除します。  
  
 使用することができます、 **TableAdapter クエリ構成ウィザード**を作成して、TableAdapter の追加のクエリを編集します。 これらの追加のクエリは、スカラー値を返す場合を除き、テーブルのスキーマに従う必要があります。  追加のクエリは、指定した名前を付ける (たとえば、 `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`)。  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>新しいクエリを使用して、TableAdapter クエリ構成ウィザードを開始するには  
  
1.  データセットを開き、**データセット デザイナー**します。  
  
2.  新しいクエリを作成する場合は、ドラッグ、**クエリ**オブジェクトから、**データセット**のタブ、**ツールボックス**上に、 <xref:System.Data.DataTable>、または選択**クエリの追加**TableAdapter のショートカット メニューから。 ドラッグすることも、**クエリ**オブジェクトの空の領域に、**データセット デザイナー**、関連付けられていない TableAdapter を作成する<xref:System.Data.DataTable>します。 これらのクエリでは、1 つの値 (スカラー) を返すことや、UPDATE、INSERT を実行に制限されます。 またはデータベースに対してコマンドを削除します。 詳細については、次を参照してください。[方法: TableAdapter にグローバル クエリの追加](../data-tools/how-to-add-global-queries-to-a-tableadapter.md)します。  
  
3.  **データ接続の選択**選択のページまたはクエリを使用して接続を作成します。  
  
    > [!NOTE]
    >  このページは、デザイナーを使用する適切な接続が判断できないときに、または接続が使用できない場合にのみ表示されます。  
  
4.  **コマンドの種類を選択** ページで、データベースからデータをフェッチする場合の次の方法から選択します。  
  
    -   **SQL ステートメントを使用して**データベースからデータを選択する SQL ステートメントを入力することができます。  
  
    -   **新しいストアド プロシージャを作成**-ウィザードで新しいストアド プロシージャの作成 (データベース) 内の指定した SELECT ステートメントに基づいて、このオプションを選択します。  
  
    -   **既存のストアド プロシージャを使用して、** -クエリを実行するときに、既存のストアド プロシージャを実行するには、このオプションを選択します。  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>既存のクエリで、TableAdapter クエリ構成ウィザードを開始するには  
  
-   既存の TableAdapter クエリを編集している場合、クエリを右クリックし **構成**ショートカット メニューから。  
  
    > [!NOTE]
    >  TableAdapter を再構成する TableAdapter のメイン クエリを右クリックし、<xref:System.Data.DataTable>スキーマ、TableAdapter に追加のクエリを右クリックして一方のみを構成します、選択したクエリ。 **TableAdapter 構成ウィザード**TableAdapter の定義を再構成、 **TableAdapter クエリ構成ウィザード**選択したクエリのみを再構成します。  
  
## <a name="running-the-wizard"></a>ウィザードの実行  
 クエリをドラッグして、**データセット デザイナー**、または既存のクエリ (任意のクエリが最初のクエリは、以下に示す) を構成します。  
  
 TableAdapter の最初のクエリは TableAdapter のメイン クエリです。 開くメイン クエリを編集、 **TableAdapter 構成ウィザード**および TableAdapter のデータ テーブルのスキーマを編集します。 メイン クエリの下に表示されているすべてのクエリを選択し、その他のクエリを使用して、構成、 **TableAdapter クエリ構成ウィザード**します。 ウィザードの実行の詳細については、次を参照してください。[方法: TableAdapter クエリ構成ウィザードを開始](http://msdn.microsoft.com/library/fc7b468e-3417-48a4-a8aa-cace8f99c24a)します。  
  
## <a name="choose-your-data-connection"></a>データ接続の選択  
 接続の一覧から既存の接続を選択するかクリックして**新しい接続**データベースへの接続を作成します。  
  
 完了時に、**接続プロパティ** ダイアログ ボックスで、**接続の詳細**領域には、選択したプロバイダーと接続文字列に関する読み取り専用の情報が表示されます。  
  
## <a name="save-the-connection-string-to-the-application-configuration-file"></a>アプリケーション構成ファイルへの接続文字列の格納  
 選択**接続を保存、** アプリケーション構成ファイルで接続文字列を格納します。 接続の名前を入力するか、あらかじめ入力されている既定の名前を使用します。  
  
 接続文字列をアプリケーション構成ファイルに保存すると、データベース接続の変更時のアプリケーションの保守プロセスが簡単になります。 データベース接続に変更が加えられた場合は、アプリケーション構成ファイル内の接続文字列を編集できます。 この方法を使うと、ソース コードを編集してアプリケーションを再コンパイルする必要はありません。 アプリケーション構成ファイル内の接続文字列の編集方法の詳細については、次を参照してください。[方法: 接続文字列の編集の保存および](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md)します。  
  
> [!IMPORTANT]
>  情報は、アプリケーション構成ファイル内にプレーンテキストとして格納されます。 機密情報への未承認アクセスの可能性を減らすために、データを暗号化できます。 詳細については、次を参照してください。[の暗号化と復号化するデータ](http://msdn.microsoft.com/en-us/22812ae8-e082-4eb1-a29b-21b6ee00c6b5)します。  
  
## <a name="use-sql-statements"></a>[SQL ステートメントを使用する]  
 このセクションを完了する方法を説明します、 **TableAdapter クエリ構成ウィザード**を選択するとき、 **SQL ステートメントを使用**オプション。  
  
## <a name="choose-a-query-type"></a>[クエリの種類の選択]  
 ウィザードでは、アプリケーションの要件に応じていくつかの種類のクエリを作成します。 データ (データ テーブル) の行を返す SELECT クエリか、またはスカラー値 (`Count`、`Sum` などの単一の値) を返す SELECT クエリを選択できます。  
  
 **クエリの種類を選択** ページで、使用可能なクエリの一覧から作成するクエリの種類を選択します。  
  
> [!NOTE]
>  INSERT、UPDATE、または DELETE の各ステートメントを作成しても、TableAdapter の `Update` メソッドを呼び出すときに使用する TableAdapter のコマンドは置き換えられません。 たとえば、クエリの種類として UPDATE を選択すると、このウィザードの後半で指定する名前の新しいクエリが作成されます。 TableAdapter のこの名前のメソッドを呼び出すことにより、このクエリを実行します。 TableAdapter の `Update` メソッドを呼び出すと、元の TableAdapter を構成したときに作成したステートメントが実行されます。  
  
## <a name="specify-a-sql-query-type-statement"></a>SQL を指定\<クエリの種類 > ステートメント  
 **SQL ステートメントを指定して** ページで、クエリを呼び出すときに実行する SQL ステートメントを入力します。  
  
> [!TIP]
>  ウィザードへのアクセスを提供する、**クエリ ビルダー**、SQL クエリを作成するためのビジュアル ツールです。 開くには、クリックして、**クエリ ビルダー**ボタンをクリックします。  
  
## <a name="choose-methods-to-generate"></a>[生成するメソッドの選択]  
 このページには、このウィザードでクエリに作成するメソッドを選択するために、次のオプションが用意されています。  
  
 **Datatable します。**  
 データ テーブルにデータを読み込むメソッドを作成します。 このメソッドを呼び出すときにデータ テーブルの名前をパラメーターとして渡し、返されたデータをデータ テーブルに読み込みます。  
  
 既定の名前を変更する、必要に応じて、**メソッド名**ボックス。 わかりやすい名前を付けると、コードでこのクエリを使用するときに役立ちます。  
  
 **DataTable を返す**  
 データが読み込まれたデータ テーブルを返すメソッドを作成します。 アプリケーションによっては、既存のデータ テーブルにデータを読み込む方法に比べ、データが読み込まれたデータ テーブルを返す方法がより適している場合があります。  
  
 既定の名前を変更する、必要に応じて、**メソッド名**ボックス。  
  
## <a name="choose-function-name"></a>[関数名の選択]  
 関数の名前を入力します。 TableAdapter クエリを作成すると、ここで指定した名前のメソッドが TableAdapter に追加されます。 クエリを実行するには、このメソッドを呼び出します。 わかりやすい名前を付けると、コードでこのクエリを使用するときに役立ちます。  
  
> [!NOTE]
>  新しいストアド プロシージャを作成する場合は、2 つの名前の指定を求められます。 最初の名前は、データベースに作成するストアド プロシージャの名前です。2 番目の名前は、このストアド プロシージャを実行するときに呼び出す TableAdapter のメソッドの名前です。  
  
## <a name="create-new-stored-procedures"></a>[新しいストアド プロシージャの作成]  
 このセクションを完了する方法を説明します、 **TableAdapter クエリ構成ウィザード**を選択するとき、**新しいストアド プロシージャの作成**オプション。  
  
1. **ストアド プロシージャの生成** ページで、ストアド プロシージャを呼び出すときに実行する SQL ステートメントを入力します。  
  
   > [!NOTE]
   >  ウィザードへのアクセスを提供する、**クエリ ビルダー**、SQL クエリを作成するためのビジュアル ツールです。 開くには、クリックして、**クエリ ビルダー**ボタンをクリックします。  
  
2. **ストアド プロシージャの作成**ページで、次の操作を行います。  
  
   1. 新しいストアド プロシージャの名前を入力します。  
  
   2. 基になるデータベースにストアド プロシージャを作成するかどうかを指定します。  
  
      > [!NOTE]
      >  データベースにストアド プロシージャを作成できるかどうかは、そのデータベースのセキュリティ設定に応じて決まります。  
  
      **ウィザードの結果を表示する**ページには、TableAdapter クエリを作成した結果が表示されます。 ウィザードで問題が発生すると、このページにエラー情報が表示されます。  
  
## <a name="use-existing-stored-procedures"></a>[既存のストアド プロシージャを使用]  
 このセクションを完了する方法を説明します、 **TableAdapter クエリ構成ウィザード**を選択するとき、**既存のストアド プロシージャを使用して、** オプション。  
  
1.  ドロップダウン リストから既存のストアド プロシージャを選択して、**既存のストアド プロシージャを選択**ウィザードのページ。  
  
     **パラメーター**と**結果**参照の選択したストアド プロシージャが表示されます。  
  
2.  **[次へ]** をクリックします。  
  
## <a name="choose-the-shape-of-data-returned-by-the-stored-procedure"></a>[ストアド プロシージャが返すデータの型の選択]  
 選択したストアド プロシージャによって返されるデータ型に応じて、ウィザードで作成される TableAdapter メソッドが決まります。  
  
 このクエリで返すデータ型を選択します。  
  
-   選択**表形式のデータ**が表示されます、**生成するメソッドの選択**(前述のとおりこのヘルプ ページで)、ページ メソッド、メソッド名、および作成するページング サポートの種類を指定することができます。  
  
-   選択**単一の値を**を 1 つの値を返す型指定されたメソッドを作成します。 このオプションを表示、**関数名の選択**ページ (このヘルプ ページで既に説明した)。  
  
-   選択**値なし**ストアド プロシージャを実行し、返されるデータでことはできません型指定されたメソッドを作成します。 このオプションを表示、**関数名の選択**ページ (このヘルプ ページで既に説明した)。  
  
## <a name="view-wizards-results"></a>[ウィザードの結果]  
 **ウィザードの結果を表示する**ページには、TableAdapter クエリを作成した結果が表示されます。 ウィザードで問題が発生した場合は、このページに詳細が表示されます。  
  
## <a name="see-also"></a>関連項目  
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [方法: TableAdapter クエリの編集](../data-tools/how-to-edit-tableadapter-queries.md)   
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio でのデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでデータの編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [データの保存](../data-tools/saving-data.md)