---
title: マネージド コードの単体テストを作成し、実行する
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 29472e2590a767c98c5674bce14712171f16fdbf
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>チュートリアル: マネージ コードの単体テストを作成し、実行する

このチュートリアルでは、マネージド コード用の Microsoft 単体テスト フレームワークと Visual Studio **テスト エクスプローラー**を使用して一連の単体テストを作成、実行、およびカスタマイズする手順について説明します。 開発中の C# プロジェクトで作業を開始し、そのコードを実行するテストを作成し、テストを実行し、結果を調べます。 次に、プロジェクト コードを変更し、テストを再実行します。

> [!NOTE]
> このチュートリアルでは、マネージ コード用の Microsoft 単体テスト フレームワークを使用します。 また、**テスト エクスプローラー**用のアダプターを備えたサード パーティの単体テスト フレームワークから**テスト エクスプローラー**を実行することもできます。 詳細については、「[サードパーティ製の単体テスト フレームワークをインストールする](../test/install-third-party-unit-test-frameworks.md)」をご覧ください。

> [!NOTE]
> コマンド ラインからテストを実行する方法については、「[チュートリアル: コマンド ライン テスト ユーティリティの使用](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)」を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

- Bank プロジェクト。 「[単体テストを作成するサンプル プロジェクト](../test/sample-project-for-creating-unit-tests.md)」をご覧ください。

## <a name="create-a-project-to-test"></a>テストするプロジェクトを作成する

1. Visual Studio を開きます。

2. **[ファイル]** メニューで、**[新規作成]** > **[プロジェクト]** の順に選択します。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3. **[インストールされているテンプレート]** の **[Visual C#]** をクリックします。

4. アプリケーションの種類の一覧の **[クラス ライブラリ]** をクリックします。

5. In the **[名前]** ボックスに「 `Bank` をポイントし、 **[OK]**」をご覧ください。

    > [!NOTE]
    > "Bank" という名前が既に使用されている場合は、別のプロジェクト名を選択します。

     新しい Bank プロジェクトが作成され、コード エディターに *Class1.cs* ファイルが開いた状態で**ソリューション エクスプローラー**が表示されます。

    > [!NOTE]
    > コード エディターに *Class1.cs* ファイルが表示されない場合、ソリューション エクスプローラーのファイル *Class1.cs* をダブルクリックして開きます。

6. 「[単体テストを作成するサンプル プロジェクト](../test/sample-project-for-creating-unit-tests.md)」からソース コードをコピーし、*Class1.cs* の元の内容をコピーしたコードに置き換えます。

7. ファイルを *BankAccount.cs* という名前で保存します。

8. **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

Bank という名前のプロジェクトができます。 これには、テストするソース コードとテストに使用するツールが含まれています。 Bank の BankAccountNS 名前空間には、パブリック クラス BankAccount が含まれます。そのメソッドを次の手順でテストします。

この記事のテストは Debit メソッドに焦点を当てています。 Debit メソッドは、口座から現金が引き出されるときに呼び出されます。 メソッド定義は次のとおりです。

```csharp
// Method to be tested.
public void Debit(double amount)
{
    if(amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    m_balance += amount;
}
```

## <a name="create-a-unit-test-project"></a>単体テスト プロジェクトを作成する

1. **[ファイル]** メニューで **[追加]** > **[新しいプロジェクト]** の順に選択します。

2. [新しいプロジェクト] ダイアログ ボックスで、 **[インストール済み]**、 **[Visual C#]** の順に展開し、 **[テスト]** をクリックします。

3. テンプレートの一覧から、 **[単体テスト プロジェクト]** を選択します。

4. **[名前]** ボックスに「`BankTests`」と入力して、**[OK]** を選択します。

     **BankTests** プロジェクトが **Bank** ソリューションに追加されます。

5. **BankTests** プロジェクトで、**Bank** プロジェクトへの参照を追加します。

     ソリューション エクスプローラーで、**BankTests** プロジェクトの **[参照設定]** をクリックし、コンテキスト メニューの **[参照の追加]** をクリックします。

6. [参照マネージャー] ダイアログ ボックスで、 **[ソリューション]** を展開し、 **[Bank]** チェックボックスをオンにします。

## <a name="create-the-test-class"></a>テスト クラスを作成する

`BankAccount` クラスを検証するテスト クラスを作成します。 プロジェクト テンプレートによって生成された *UnitTest1.cs* ファイルを使用できますが、ファイルとクラスにはよりわかりやすい名前を付けます。 **ソリューション エクスプローラー**でファイルの名前変更機能を使用すると、この処理を 1 つの手順で実行できます。

### <a name="rename-a-class-file"></a>クラス ファイルの名前を変更する

**ソリューション エクスプローラー**で、BankTests プロジェクトの *UnitTest1.cs* ファイルを選択します。 コンテキスト メニューの **[名前の変更]** をクリックし、ファイルの名前を *BankAccountTests.cs* に変更します。 プロジェクト内のコード要素 `UnitTest1` に対するすべての参照を名前変更するかどうかを確認するダイアログで、**[はい]** をクリックします。

この手順により、クラスの名前が `BankAccountTests`に変更されます。 *BankAccountTests.cs* ファイルには次のコードが含まれるようになりました。

```csharp
using System;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace BankTests
{
    [TestClass]
    public class BankAccountTests
    {
        [TestMethod]
        public void TestMethod1()
        {
        }
    }
}
```

### <a name="add-a-using-statement-to-the-project-under-test"></a>テスト対象のプロジェクトに using ステートメントを追加する

`using` ステートメントをクラスに追加して、完全修飾名を使用せずにテスト対象のプロジェクトに呼び出すことができるようにすることもできます。 クラス ファイルの先頭に次のように追加します。

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>テスト クラスの要件

テスト クラスの最小要件は次のとおりです。

- マネージ コード用の Microsoft 単体テスト フレームワークでは、テスト エクスプローラーで実行する単体テスト メソッドを含むすべてのクラスについて、 `[TestClass]` 属性が必要です。

- テスト エクスプローラーで実行する各テスト メソッドには `[TestMethod]`属性が必要です。

単体テスト プロジェクトで `[TestClass]` 属性がない別のクラスを使用することができます。また、テスト クラスで `[TestMethod]` 属性がない別のメソッドを使用することもできます。 こうした別のクラスやメソッドをテスト メソッドで使用できます。

## <a name="create-the-first-test-method"></a>最初のテスト メソッドを作成する

この手順では、`BankAccount` クラスの `Debit` メソッドの動作を検証する単体テスト メソッドを記述します。 `Debit` メソッドについては、この記事で前述されています。

確認する必要がある動作は少なくとも 3 つあります。

- 引き落とし金額が残高を上回る場合、このメソッドは <xref:System.ArgumentOutOfRangeException> をスローします。

- 引き落とし金額が 0 未満の場合、このメソッドは <xref:System.ArgumentOutOfRangeException> をスローします。

- 引き落とし金額が有効な場合、このメソッドは口座残高から借方金額を減算します。

> [!TIP]
> このチュートリアルでは使用しないため、既定の `TestMethod1` メソッドを削除できます。

### <a name="to-create-a-test-method"></a>テスト メソッドを作成するには

最初のテストでは、正しい金額 (つまり、口座残高未満かつ 0 を上回る金額) によって口座から正しい金額が引き出されることが確認されます。 次のメソッドを `BankAccountTests` クラスに追加します。

```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
}
```

このメソッドは単純です。期首残高を含む新しい `BankAccount` オブジェクトを設定し、有効な金額を引き出します。 期末残高が予想どおりであることを確認するには、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> メソッドを使用します。

### <a name="test-method-requirements"></a>テスト メソッドの要件

テスト メソッドは次の条件を満たしている必要があります。

- `[TestMethod]` 属性で修飾されています。

- `void` を返します。

- パラメーターを含むことができません。

## <a name="build-and-run-the-test"></a>テストをビルドして実行する

1. **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

   エラーがない場合は、**テスト エクスプローラー**が表示され、**[テストを実行しない]** グループに **[Debit_WithValidAmount_UpdatesBalance]** が表示されます。

   > [!TIP]
   > ビルドの成功後に**テスト エクスプローラー**が表示されない場合は、メニューの **[テスト]** をクリックし、**[ウィンドウ]**、**[テスト エクスプローラー]** の順に選択します。

2. **[すべて実行]** をクリックしてテストを実行します。 テストの実行中は、ウィンドウの上部にあるステータス バーがアニメーション化されます。 テストの実行の終了時に、すべてのテスト メソッドが成功した場合はステータス バーが緑色に変わり、いずれかのテストが失敗した場合は赤色に変わります。

3. この場合は、テストが失敗します。 このテスト メソッドは、**[失敗したテスト]** グループに移動します。 **テスト エクスプローラー**でメソッドを選択すると、ウィンドウの下部に詳細が表示されます。

## <a name="fix-your-code-and-rerun-your-tests"></a>コードを修正してテストを再実行する

**テスト結果を分析する**

テスト結果には失敗を示すメッセージが含まれています。 `AreEquals` メソッドについて、メッセージには、想定された事項 (**Expected\<*value*>** パラメーター) および実際に受け取られた事項 (**Actual\<*value*>** パラメーター) が示されます。 残高が減少すると予想していましたが、実際には代わりに引き出し額によって増加しています。

単体テストにより、引き出し額は、*減算*する必要があるときに口座残高に*追加*されます。単体テストではバグがわかりました。

**バグを修正する**

エラーを修正するには、行を置き換えます。

```csharp
m_balance += amount;
```

次の内容に置き換えます。

```csharp
m_balance -= amount;
```

**テストを再実行する**

テスト エクスプローラーで、 **[すべて実行]** をクリックしてテストを再実行します。 赤色/緑色のステータス バーはテストが成功したことを示す緑色になり、テストは **[成功したテスト]** グループに移動します。

## <a name="use-unit-tests-to-improve-your-code"></a>単体テストを使用してコードを改良する

このセクションでは、分析の反復処理、単体テストの進展、およびリファクタリングが、実稼働のコードの堅牢性と有効性を高めるうえでどのように役立つかを説明します。

**問題を分析する**

有効な金額が `Debit` メソッドで正しく差し引かれているかどうかを確認するテスト メソッドを作成しました。 引き落とし金額が次のいずれかである場合、メソッドが <xref:System.ArgumentOutOfRangeException> をスローすることを確認します。

- 残高よりも大きい、または
- 0 未満。

**テスト メソッドを作成する**

引き落とし金額が 0 未満の場合の正しい動作を検証するテスト メソッドを作成します。

```csharp
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert is handled by the ExpectedException attribute on the test method.
}
```

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> 属性を使用して、正しい例外がスローされたことをアサートします。 この属性により、 <xref:System.ArgumentOutOfRangeException> がスローされない限り、テストは失敗します。 引き落とし金額が 0 未満の場合、より汎用的な <xref:System.ApplicationException> をスローするようにテスト対象のメソッドを一時的に変更すると、テストは正しく動作します。つまり失敗します。

引き出し金額が残高を上回るケースをテストするには、次の手順を実行します。

1. `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`という新しいテスト メソッドを作成します。

2. メソッド本体を `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` から新しいメソッドにコピーします。

3. `debitAmount` を、残高を上回る数値に設定します。

**テストを実行**

2 つのテスト メソッドを実行すると、テストが正しく機能することがわかります。

**分析を継続する**

一方で、最後の 2 つのテスト メソッドには問題もあります。 いずれかのテストが実行されたときに、テスト対象のメソッドのどの条件が例外をスローするかを特定することはできません。 負の引き落とし金額または残高よりも大きい金額の 2 つの条件を区別するいくつかの方法を利用すると、テストの信頼が高くなります。

テスト対象のメソッドをもう一度確認すると、引数の名前をパラメーターとして使用する `ArgumentOutOfRangeException` コンストラクターが両方の条件ステートメントで使用されていることがわかります。

```csharp
throw new ArgumentOutOfRangeException("amount");
```

はるかに豊富な情報を報告するために使用できるコンストラクターがあります。<xref:System.ArgumentOutOfRangeException.%23ctor%2A>`(String, Object, String)` には、引数の名前、引数の値、ユーザー定義のメッセージが含まれています。 このコンストラクターを使用するようにテスト対象のメソッドをリファクタリングできます。 さらに、一般に公開されている型メンバーを使用して、エラーを指定できます。

**テスト対象のコードをリファクタリングする**

最初に、エラー メッセージの 2 つの定数をクラス スコープで定義します。 これらをテスト対象のクラスに入れます (`Bank`)。

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

次に、`Debit` メソッドの 2 つの条件ステートメントを変更します。

```csharp
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
```

**テスト メソッドをリファクタリングする**

`ExpectedException` テスト メソッド属性を削除し、代わりにスローされた例外をキャッチし、関連付けられたメッセージを確認します。 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> メソッドには、2 つの文字列を比較する機能があります。

`Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` は次のようになります。

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

**再テストする、書き換える、再分析する**

テスト対象のメソッドにバグがあっても `Debit` メソッドが <xref:System.ArgumentOutOfRangeException> を*スロー*せず、例外と共に正しいメッセージを出力するとします。 現在、テスト メソッドはこのケースを処理しません。 `debitAmount` 値が有効な場合 (つまり、残高未満だが 0 よりは大きい場合)、例外はキャッチされないので、アサートはキャッチされません。 それでも、テスト メソッドは成功します。 これは適切ではありません。例外がスローされない場合はテスト メソッドが失敗することを想定しているためです。

これはテスト メソッドのバグです。 この問題を解決するには、テスト メソッドの最後に <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> アサートを追加して、例外がスローされないケースを処理するようにします。

ただし、テストを再実行すると、正しい例外がキャッチされた場合にテストが*失敗*したことが示されます。 `catch` ブロックは例外をキャッチしますが、メソッドは引き続き実行され、新しい <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> アサート時に失敗します。 この問題を解決するには、`catch` ブロックの `StringAssert` の後に `return` ステートメントを追加します。 テストを再実行して、この問題が解決したことを確認します。 `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` の最終バージョンは、次のようになります。

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

テスト コードを改善することで、より堅牢で有益なテスト方法になりました。 ただし、もっと重要な点は、テスト対象のコードも改善されたことです。
