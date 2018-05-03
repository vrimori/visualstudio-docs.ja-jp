---
title: '方法: Visual Studio でデータ ドリブン単体テストを作成する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b72f2099f629a35659d67832f4ec583f1409f1c4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-data-driven-unit-test"></a>方法: データ ドリブン単体テストを作成する

マネージ コード用の Microsoft の単体テスト フレームワークを使用して、データ ソースからテスト メソッドで使用される値を取得するための単体テスト メソッドを設定できます。 メソッドはデータ ソース内の各行に対して連続して実行されるため、単一のメソッドを使用してさまざまな入力を簡単にテストできます。

データ ドリブン単体テストの作成には、次の手順が含まれます。

1.  テスト メソッドで使用する値を含むデータ ソースを作成します。 データ ソースは、テストを実行するコンピューターに登録されている任意の型にすることができます。

2.  プライベート <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> フィールドとパブリック `TestContext` プロパティをテスト クラスに追加します。

3.  単体テスト メソッドを作成し、それを <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> 属性に追加します。

4.  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> インデクサー プロパティを使用して、テストで使用する値を取得します。

##  <a name="BKMK_The_method_under_test"></a>テスト対象のメソッド

たとえば、次が用意されています。

1.  さまざまな種類の勘定のトランザクションを受け入れて処理する `MyBank` というソリューション。

2.  勘定のトランザクションを管理する `BankDb` という `MyBank` 内のプロジェクト。

3.  トランザクションが必ず銀行にとって有利になるように数値演算関数を実行する `DbBank` プロジェクト内の `Maths` というクラス。

4.  `BankDb` コンポーネントの動作をテストする `BankDbTests` という単体テスト プロジェクト。

5.  `Maths` クラスの動作を確認する `MathsTests` という単体テスト クラス。

ループを使用して 2 つの整数を追加する `Maths` のメソッドをテストします。

```csharp
public int AddIntegers(int first, int second)
{
    int sum = first;
    for( int i = 0; i < second; i++)
    {
        sum += 1;
    }
    return sum;
}
```

##  <a name="BKMK_Creating_a_data_source"></a> データ ソースの作成
 `AddIntegers` メソッドをテストするには、パラメーターの値の範囲と返される必要のある合計を指定するデータ ソースを作成します。 この例では、`MathsData` という名前の Sql Compact データベースと、次の列の名前と値を含む `AddIntegersData` という名前のテーブルを作成します

|FirstNumber|SecondNumber|Sum|
|-----------------|------------------|---------|
|0|1|1|
|1|1|2|
|2|-3|-1|

##  <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> テスト クラスへの TestContext の追加
 単体テスト フレームワークは、データ ドリブン テストのデータ ソース情報を格納する `TestContext` オブジェクトを作成します。 次に、フレームワークは作成する `TestContext` プロパティの値としてこのオブジェクトを設定します。

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

 テスト メソッドでは、`TestContext` の `DataRow` インデクサー プロパティを使用してデータにアクセスします。

##  <a name="BKMK_Writing_the_test_method"></a> テスト メソッドの記述
 `AddIntegers` のテスト メソッドは非常に単純です。 データ ソース内の各行に対して、パラメーターとして **FirstNumber** 列値と **SecondNumber** 列値を持つ `AddIntegers` を呼び出して、**Sum** 列値に対して戻り値を確認します。

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]
[TestMethod()]
public void AddIntegers_FromDataSourceTest()
{
    var target = new Maths();

    // Access the data
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);
    int actual = target.IntegerMethod(x, y);
    Assert.AreEqual(expected, actual,
        "x:<{0}> y:<{1}>",
        new object[] {x, y});
}
```

`Assert` メソッドには、失敗したイテレーションの `x` と `y` の値を表示するメッセージが含まれます。 既定では、アサートされた値である `expected` と `actual` が失敗したテストの詳細に既に含まれています。

###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> DataSourceAttribute の指定
 `DataSource` 属性は、データ ソースの接続文字列とテスト メソッドで使用するテーブル名を指定します。 接続文字列の正確な情報は、使用しているデータ ソースの種類によって異なります。 この例では、SqlServerCe データベースを使用しました。

```
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

DataSource 属性には 3 つのコンストラクターがあります。

```
[DataSource(dataSourceSettingName)]
```

 1 つのパラメーターを持つコンストラクターは、ソリューションの app.config ファイルに格納されている接続情報を使用します。 *dataSourceSettingsName* は、接続情報を指定する構成ファイル内の Xml 要素の名前です。

 app.config ファイルを使用すると、単体テスト自体に変更を加えずに、データ ソースの場所を変更できます。 app.config ファイルの作成と使用方法については、「[チュートリアル : データ ソースを定義するための構成ファイルの使用](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)」を参照してください

```
[DataSource(connectionString, tableName)]
```

 2 つのパラメーターを持つ `DataSource` コンストラクターは、データ ソースの接続文字列とテスト メソッドのデータを含むテーブルの名前を指定します。

 接続文字列は、データ ソースの種類によって異なりますが、データ プロバイダーの不変名を指定する Provider 要素を含んでいる必要があります。

```
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> データにアクセスするための TestContext.DataRow の使用
 `AddIntegersData` テーブル内のデータにアクセスするには、`TestContext.DataRow` インデクサーを使用します。 `DataRow` は、<xref:System.Data.DataRow> オブジェクトであるため、インデックスまたは列の名前で列の値を取得します。 値はオブジェクトとして返されるため、適切な型に変換します。

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

##  <a name="BKMK_Running_the_test_and_viewing_results"></a>テストの実行と結果の表示
 テスト メソッドの記述が完了したら、テスト プロジェクトを構築します。 **[テストを実行しない]** グループのテスト エクスプローラー ウィンドウに、テスト メソッドが表示されます。 テストを実行して、記述し、再実行すると、テスト エクスプローラーに **[失敗したテスト]**、**[成功したテスト]**、および **[テストを実行しない]** のグループの結果が表示されます。 **[すべて実行]** を選択してテストをすべて実行することも、**[実行...]** を選択して実行するテストのサブセットを選択することもできます。

 テストの実行中は、エクスプローラーの上部にあるテスト結果バーがアニメーションで表示されます。 テストの実行の終了時に、すべてのテストが成功した場合はバーが緑色になり、いずれかのテストが失敗した場合は赤色になります。 テスト エクスプローラー ウィンドウの下部の詳細ウィンドウに、テストの実行の概要が表示されます。 テストを選択すると、そのテストの詳細が下部のペインに表示されます。

 この例の `AddIntegers_FromDataSourceTest` メソッドを実行すると、結果バーが赤に変わり、テスト メソッドは **[失敗したテスト]** に移動されます。データ ソースからの反復されたメソッドのいずれかが失敗した場合は、データ ドリブン テストは失敗します。 テスト エクスプローラー ウィンドウで、失敗したデータ ドリブン テストを選択すると、詳細ウィンドウにはデータ行インデックスによって識別される各イテレーションの結果が表示されます。 この例では、`AddIntegers` アルゴリズムが負の値を正しく処理していないことがわかります。

 テスト対象のメソッドを修正して、テストを再実行すると、結果バーが緑に変わり、テスト メソッドは **[成功したテスト]** グループに移動されます。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [コードの単体テスト](../test/unit-test-your-code.md)
- [テスト エクスプローラーを使用して単体テストを実行する](../test/run-unit-tests-with-test-explorer.md)
- [マネージ コード用の Microsoft 単体テスト フレームワークを使用した .NET Framework 用単体テストの記述](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)