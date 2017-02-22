---
title: "方法: データ ドリブン単体テストを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.test.testresults.unittest.datadriven"
  - "vs.test.testresults.unittest.datadriven.failure"
helpviewer_keywords: 
  - "単体テスト、実行"
  - "単体テスト、データドリブン"
  - "データ ドリブン単体テスト"
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: 33
caps.handback.revision: 33
ms.author: "mlearned"
manager: "douge"
---
# 方法: データ ドリブン単体テストを作成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

マネージ コード用の Microsoft の単体テスト フレームワークを使用して、テスト メソッドで使用されるデータ ソースから値を取得するための単体テスト メソッドを設定できます。  メソッドは単一のメソッドを使用して、さまざまな入力をテストしやすくするデータ ソース内の各行に対して繰り返し実行します。  
  
 このトピックは次のセクションで構成されています。  
  
-   [テスト対象のメソッド](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)  
  
-   [データ ソースの作成](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)  
  
-   [クラスに TestContext テストを追加できます。](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)  
  
-   [テスト メソッドを作成できます。](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)  
  
    -   [DataSourceAttribute の指定](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)  
  
    -   [データにアクセスする TestContext.DataRow を使用する](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)  
  
-   [テスト結果の表示および実行](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)  
  
 データ ドリブン単体テストを作成するには、次の手順が T:  
  
1.  テスト メソッドで使用される値を含むデータ ソースを作成します。  データ ソースは、テストを実行するコンピューターに登録されている型にすることができます。  
  
2.  テスト クラスに <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> プライベートなフィールドと `TestContext` のパブリックなプロパティを追加します。  
  
3.  単体テスト メソッドを作成し、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> 属性を追加します。  
  
4.  テストで使用する値を取得するために <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> のインデクサーのプロパティを使用します。  
  
##  <a name="BKMK_The_method_under_test"></a> テスト対象のメソッド  
 たとえば、最初に作成したと仮定しましょう:  
  
1.  アカウントの種類のトランザクションを受け取って処理するソリューションは `MyBank` と呼ばれます。  
  
2.  アカウントのトランザクションを管理する `MyBank` のプロジェクトは `BankDb` と呼ばれます。  
  
3.  クラスには、トランザクションが Bank に便利なことを保証するために、数値演算関数を実行 `DbBank` のプロジェクトの `Maths` と呼ばれます。  
  
4.  単体テスト プロジェクトが `BankDb` コンポーネントの動作をテストするに `BankDbTests` と呼ばれます。  
  
5.  単体テスト クラスは `Maths` クラスの動作を検証するために `MathsTests` と呼ばれます。  
  
 これは、ループを使用して 2 個の整数を加算する `Maths` のメソッドをテストする:  
  
```  
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
 `AddIntegers` のメソッドをテストするために、ユーザーが返されるはずの合計パラメーターには、および値の範囲を指定するデータ ソースを作成します。  この例では、SQL Compact データベースの名前が `MathsData` と `AddIntegersData` という名前の次の項目の名前と値を含むテーブルを作成します。  
  
|FirstNumber|SecondNumber|Sum|  
|-----------------|------------------|---------|  
|0|1|1|  
|1|1|2|  
|2|\-3|\-1|  
  
##  <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> クラスに TestContext テストを追加できます。  
 単体テスト フレームワークは、データ ドリブン テストのデータ ソースの情報を格納する `TestContext` オブジェクトを作成します。  フレームワークは `TestContext` のプロパティの値として、次に作成し、このオブジェクトを設定します。  
  
```  
  
private TestContext testContextInstance;  
public TestContext TestContext  
{  
    get { return testContextInstance; }  
    set { testContextInstance = value; }  
}  
  
```  
  
 テスト メソッドでは、`TestContext`の `DataRow` のインデクサーのプロパティを通じてデータにアクセスします。  
  
##  <a name="BKMK_Writing_the_test_method"></a> テスト メソッドを作成できます。  
 `AddIntegers` のテスト メソッドはきわめて単純です。  データ ソース内の各行には、パラメーターとして **FirstNumber** と **SecondNumber** の列の値を持つ `AddIntegers` を呼び出し、**合計** の列の値に対して戻り値を確認する:  
  
```  
  
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
  
 `Assert` のメソッドは、イテレーションの `x` と `y` 値を表示するメッセージが含まれていることに注意してください。  既定で、アサートされた値、`expected` と `actual`は失敗したテストの詳細は、既に含まれています。  
  
###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> DataSourceAttribute の指定  
 `DataSource` 属性を使用すると、データ ソースの接続文字列とテスト メソッドで使用するテーブルの名前を指定します。  接続文字列の正確な内容は、使用するデータ ソースの種類によって異なります。  この例では、SqlServerCe のデータベースを使用しています。  
  
```  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]  
```  
  
 DataSource 属性に 3 個のコンストラクターがあります。  
  
```  
[DataSource(dataSourceSettingName)]  
```  
  
 1 個のパラメーターのコンストラクターはソリューションの app.config ファイルに保存されている接続情報を使用します。  *dataSourceSettingsName* に接続情報を指定する構成ファイルの XML 要素の名前です。  
  
 app.config ファイル割り当てを使用して他のデータ ソースの場所を変更する単体テスト自体に変更します。  app.config ファイルを作成および使用する方法の詳細については、「[チュートリアル : データ ソースを定義するための構成ファイルの使用](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)」を参照してください。  
  
```  
[DataSource(connectionString, tableName)]  
```  
  
 2 個のパラメーターの `DataSource` のコンストラクターは、データ ソースの接続文字列とテスト メソッドのデータを含むテーブルの名前を指定します。  
  
 接続文字列は、データ ソースの種類によって決まりますが、データ プロバイダーの不変名を指定する provider 要素を含める必要があります。  
  
```  
[DataSource(  
    dataProvider,   
    connectionString,   
    tableName,  
    dataAccessMethod  
    )]  
```  
  
###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> データにアクセスする TestContext.DataRow を使用する  
 `AddIntegersData` のデータにアクセスするには `TestContext.DataRow` のインデクサーを Table に配置して、使用します。  `DataRow` は <xref:System.Data.DataRow> オブジェクトであり、そのインデックスまたは項目の名前によって列の値を取得します。  値をオブジェクトとして返すため、適切な型に変換する必要があります:  
  
```  
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
  
```  
  
##  <a name="BKMK_Running_the_test_and_viewing_results"></a> テスト結果の表示および実行  
 テスト メソッドの作成が終了したら、テスト プロジェクトをビルドします。  テスト メソッドは **\[テストを実行しない\(N\)\]** グループのテスト エクスプローラー ウィンドウに表示されます。  実行して作成し、テスト、テスト エクスプローラーが表示 **\[失敗したテスト\]** グループの結果、**\[成功したテスト数\]** と **\[テストを実行しない\(N\)\]** を再実行します。  テストを実行するに **\[すべて実行\]** をクリックしますできます。また、テストのサブセットを実行するように選択するために **\[実行...\]** をクリックします。  
  
 エクスプローラーの上部のテスト結果のバーはテストの実行中にアニメーション化されます。  テストの実行の終了時に、バーはテストに失敗したすべてのテストが赤渡そうと緑です。  テスト実行の概要はテスト エクスプローラー ウィンドウの下部にある詳細ペインに表示されます。  テストを選択すると、そのテストの詳細が下部のペインに表示されます。  
  
 この例の `AddIntegers_FromDataSourceTest` のメソッドを実行すると、結果のバーは赤に回転してから、データ ソースの繰り返されたメソッドのいずれかが失敗した場合は、テスト メソッドは **\[失敗したテスト\]** A データ ドリブン テストに失敗して移動します。  テスト エクスプローラー ウィンドウで、データ ドリブン テストを選択すると、詳細ペインにはデータ行のインデックスによって識別されるイテレーションの結果が表示されます。  この例では、`AddIntegers` アルゴリズムが負の値を正しく処理しないようです。  
  
 テスト対象のメソッドとテスト再実行修正すると、結果は緑のバーの回転、テスト メソッドは **\[テスト成功\]** のグループに移動されます。  
  
## 参照  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>   
 [How to: Create and Run a Unit Test](http://msdn.microsoft.com/ja-jp/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48)   
 [コードの単体テスト](../test/unit-test-your-code.md)   
 [テスト エクスプローラーを使用して単体テストを実行する](../test/run-unit-tests-with-test-explorer.md)   
 [マネージ コード用の Microsoft 単体テスト フレームワークを使用した .NET Framework 用単体テストの記述](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)