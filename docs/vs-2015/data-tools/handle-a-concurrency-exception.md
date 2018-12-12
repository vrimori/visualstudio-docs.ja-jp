---
title: 同時実行例外の処理 |Microsoft Docs
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
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3141f2480aabc2ce6aa7b10f99991fc5cba0d05
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220418"
---
# <a name="handle-a-concurrency-exception"></a>コンカレンシー例外を処理する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
2 人のユーザーが同じデータベースの同じデータを同時に変更しようとすると、コンカレンシー例外 (<xref:System.Data.DBConcurrencyException>) が発生します。 このチュートリアルをキャッチする方法を説明する Windows アプリケーションを作成、<xref:System.Data.DBConcurrencyException>エラーの原因となった行を見つけて、それを処理する方法の戦略について説明します。  
  
 ここでは次の手順を実行します。  
  
1.  新規作成**Windows アプリケーション**プロジェクト。  
  
2.  Northwind `Customers` テーブルに基づいて、新しいデータセットを作成します。  
  
3.  データを表示する <xref:System.Windows.Forms.DataGridView> を備えたフォームを作成します。  
  
4.  Northwind データベースの `Customers` テーブルからデータセットにデータを読み込みます。  
  
5.  使用して、 [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1)に直接アクセスする Visual Studio で、`Customers`データ テーブルし、レコードを変更します。  
  
6.  別の値に同じレコードを変更、データセットを更新および発生している同時実行エラーが発生すると、データベースへの変更の書き込みを試行します。  
  
7.  エラーをキャッチし、操作を継続してデータベースを更新するか、または更新をキャンセルするかを判断できるように、レコードの異なるバージョンを表示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベースにアクセスして更新を実行するためのアクセス許可。 詳細については、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)します。  
  
> [!NOTE]
>  アクティブな設定または使用しているエディションによって、ヘルプの説明から、ダイアログ ボックスとメニュー コマンドが表示が異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="create-a-new-project"></a>新しいプロジェクトを作成する  
 新しい Windows アプリケーションの作成からチュートリアルを開始します。  
  
#### <a name="to-create-a-new-windows-application-project"></a>新しい Windows アプリケーション プロジェクトを作成するには  
  
1.  **ファイル**] メニューの [新しいプロジェクトを作成します。  
  
2.  **プロジェクトの種類**ウィンドウで、プログラミング言語を選択します。  
  
3.  **テンプレート**ペインで、 **Windows アプリケーション**します。  
  
4.  プロジェクトに名前を`ConcurrencyWalkthrough`、し、 **OK**します。  
  
     Visual Studio にプロジェクトが追加**ソリューション エクスプ ローラー**し、デザイナーで新しいフォームを表示します。  
  
## <a name="create-the-northwind-dataset"></a>Northwind データセットを作成します。  
 このセクションでという名前のデータセットを作成する`NorthwindDataSet`します。  
  
#### <a name="to-create-the-northwinddataset"></a>NorthwindDataSet を作成するには  
  
1.  **データ**] メニューの [選択**新しいデータの追加ソース**します。  
  
     [データ ソース構成ウィザード](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)が開きます。  
  
2.  **データ ソースの種類を選択**画面で、**データベース**します。  
  
3.  利用可能な接続の一覧から Northwind サンプル データベースへの接続を選択します。接続が接続の一覧で使用できない場合は、選択**新しい接続**  
  
    > [!NOTE]
    >  ローカル データベース ファイルに接続する場合は、選択**いいえ**されたら、ファイルをプロジェクトに追加したい場合。  
  
4.  **接続文字列をアプリケーション構成ファイルに保存**画面で、**次**します。  
  
5.  展開、**テーブル**ノード、`Customers`テーブル。 既定のデータセット名は、`NorthwindDataSet` です。  
  
6.  選択**完了**にデータセットをプロジェクトに追加します。  
  
## <a name="create-a-data-bound-datagridview-control"></a>データ バインド DataGridView コントロールを作成します。  
 このセクションで作成、<xref:System.Windows.Forms.DataGridView>をドラッグして、**顧客**から項目、**データ ソース**ウィンドウから、Windows フォームにします。  
  
#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Customers テーブルにバインドする DataGridView コントロールを作成するには  
  
1.  **データ**] メニューの [選択 **[データ ソースの**を開く、**データ ソース] ウィンドウ**します。  
  
2.  **データソース**ウィンドウで、展開、 **NorthwindDataSet**ノード、および選択し、**顧客**テーブル。  
  
3.  テーブル ノードで、下向きの矢印を選択し、 **DataGridView**ドロップダウン リストでします。  
  
4.  テーブルをフォームの空の領域にドラッグします。  
  
     A<xref:System.Windows.Forms.DataGridView>という名前のコントロール`CustomersDataGridView`と<xref:System.Windows.Forms.BindingNavigator>という`CustomersBindingNavigator`にバインドされているフォームに追加されます、<xref:System.Windows.Forms.BindingSource>します。これは、有効にするにバインドされている、`Customers`テーブルに、`NorthwindDataSet`します。  
  
## <a name="test-the-form"></a>フォームをテストします。  
 フォームをテストして、ここまでの設定が期待どおりに動作することを確認します。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
1.  選択**F5**アプリケーションを実行するには  
  
     フォームが表示されます、<xref:System.Windows.Forms.DataGridView>からのデータが格納されるコントロール、`Customers`テーブル。  
  
2.  **デバッグ**メニューの [**デバッグの停止]** します。  
  
## <a name="handleconcurrency-errors"></a>Handleconcurrency エラー  
 エラーを処理する方法は、アプリケーションを管理する特定のビジネス ルールに依存します。 このチュートリアルで次の戦略例として使用方法の開発、同時実行エラー。  
  
 次の 3 つのバージョンのレコードを持つユーザーの applicationpresents:  
  
- データベースの現在のレコード  
  
- データセットに読み込まれた元のレコード  
  
- データセットの変更の提案  
  
  ユーザーに提案されたバージョンでは、データベースを上書きするか、または更新をキャンセルし、データベースから新しい値でデータセットを更新できます。  
  
#### <a name="to-enable-the-handling-of-concurrency-errors"></a>コンカレンシー エラーを処理できるようにするには  
  
1.  カスタム エラー ハンドラーの作成  
  
2.  ユーザーに対する選択肢の表示  
  
3.  ユーザーの応答の処理  
  
4.  更新の再送、またはデータセット内のデータのリセット  
  
### <a name="addcode-to-handle-the-concurrency-exception"></a>同時実行例外を処理する Addcode  
 更新プログラムを実行しようとすると、例外が発生、一般に、発生した例外によって提供される情報で何か操作します。  
  
 このセクションでは、データベースを更新しようとするコードを追加します。いずれかの処理も<xref:System.Data.DBConcurrencyException>を生成される可能性やその他の例外。  
  
> [!NOTE]
>  このチュートリアルの後半で、`CreateMessage` メソッドと `ProcessDialogResults` メソッドを追加します。  
  
##### <a name="to-add-error-handling-for-the-concurrency-error"></a>コンカレンシー エラー用のエラー処理を追加するには  
  
1.  `Form1_Load` メソッドの下に次のコードを追加します。  
  
     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]  
  
2.  次のように `CustomersBindingNavigatorSaveItem_Click` メソッドを `UpdateDatabase` メソッドの呼び出しに置き換えます。  
  
     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]  
  
### <a name="displaychoices-to-the-user"></a>ユーザーに Displaychoices  
 上のコードにより `CreateMessage` プロシージャが呼び出され、ユーザーにエラー情報が表示されます。 このチュートリアルでは、ユーザーに異なるバージョンのレコードを表示するのにメッセージ ボックスを使用します。これにより、ユーザーが変更で、レコードを上書きしたり、編集をキャンセルするかどうかを選択できます。 ユーザーがメッセージ ボックスのオプションを選択する (ボタンをクリックする) と、`ProcessDialogResult` メソッドに応答が渡されます。  
  
##### <a name="to-create-the-message-to-display-to-the-user"></a>ユーザーに表示するメッセージを作成するには  
  
-   次のコードを追加して、メッセージを作成、**コード エディター**します。 このコードは、`UpdateDatabase` メソッドの下に入力します。  
  
     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]  
  
### <a name="process-the-users-response"></a>ユーザーの応答を処理します。  
 メッセージ ボックスに、ユーザーの応答を処理するコードも必要です。 、提案された変更で、データベースの現在のレコードを上書きまたはローカルの変更を破棄し、現在、データベース内にあるレコードをデータ テーブルを更新することもできます。 ユーザーが [はい] を選択した場合、<xref:System.Data.DataTable.Merge%2A>メソッドを呼び出すと、 *preserveChanges*引数に設定`true`します。 これにより、レコードの元のバージョンがデータベース内のレコードと一致するように成功すると、ある更新の試行です。  
  
##### <a name="to-process-the-user-input-from-the-message-box"></a>メッセージ ボックスからのユーザーの入力を処理するには  
  
-   前のセクションで追加されたコードの下の次のコードを追加します。  
  
     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>フォームをテストします。  
 フォームをテストして、期待どおりに動作することを確認します。 コンカレンシー違反をシミュレートするには、NorthwindDataSet にデータを読み込んだ後で、データベースのデータを変更する必要があります。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
1.  選択**F5**アプリケーションを実行します。  
  
2.  フォームが表示されたら、実行を継続したまま Visual Studio IDE に切り替えます。  
  
3.  **ビュー** ] メニューの [選択**サーバー エクスプ ローラー**します。  
  
4.  **サーバー エクスプ ローラー**、接続、アプリケーションを使用して、順に展開を展開、**テーブル**ノード。  
  
5.  右クリックし、**顧客**テーブルし、**テーブル データの表示**します。  
  
6.  最初のレコード (`ALFKI`) 変更`ContactName`に`Maria Anders2`します。  
  
    > [!NOTE]
    >  別の行に移動し、変更をコミットします。  
  
7.  `ConcurrencyWalkthrough` の実行中のフォームに切り替えます。  
  
8.  フォームの最初のレコードで (`ALFKI`)、変更`ContactName`に`Maria Anders1`します。  
  
9. 選択、**保存**ボタンをクリックします。  
  
     コンカレンシー エラーが発生し、メッセージ ボックスが表示されます。  
  
10. 選択**いいえ**更新をキャンセルし、現在、データベース内にある値でデータセットを更新します。 選択**はい**データベースに指定された値を書き込みます。
  
## <a name="see-also"></a>関連項目

- [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)