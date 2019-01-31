---
title: デバッガーでの例外の管理 |Microsoft Docs
ms.custom: seodec18
ms.date: 10/09/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6a43e42f68b93c358ed5808a6cffc9570fcbef9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918110"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Visual Studio のデバッガーでの例外を管理します。

例外は、プログラムの実行中に発生したエラー状態を示します。 例外または上で、中断する例外のセットは、デバッガーを設定でき、この時点でデバッガーが中断する (つまり、デバッガーで一時停止) します。 デバッガーが中断したときでは、例外がスローされました。 追加または例外を削除することもできます。 Visual Studio で開いているソリューションを使用して**デバッグ > Windows > 例外設定**を開く、**例外設定**ウィンドウ。

最も重要な例外に応答するハンドラーを提供します。 例外のハンドラーを追加、表示する方法を理解する必要がある場合[より適切に記述することでバグを修正C#コード](../debugger/write-better-code-with-visual-studio.md)します。 また、常に実行を中断する一部の例外のデバッガーを構成する方法について説明します。

例外が発生すると、**[出力]** ウィンドウに例外メッセージが書き込まれます。 次の実行を壊す可能性がある場合します。

- 処理されない例外がスローされます。
- デバッガーを構成するには任意のハンドラーが呼び出される前に実行を中断します。
- 設定した[マイ コードのみ](../debugger/just-my-code.md)デバッガーはユーザー コードで処理されない例外で中断するよう構成します。

> [!NOTE]
> ASP.NET は、エラー ページをブラウザーに表示する最上位の例外ハンドラーを持っています。 しない限り、実行は中断されません、**マイ コードのみ**がオンにします。 例については、次を参照してください。[ユーザーよって処理されない例外を続行するようにデバッガー](#BKMK_UserUnhandled)以下。

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> Visual Basic アプリケーションのデバッガーでは、すべてのエラーが例外として管理されます。On Error 形式のエラー ハンドラーを使用している場合でもそうです。

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>例外がスローされたときに中断するようにデバッガー

デバッガーは、ハンドラーが呼び出される前に、例外を調べることができますので、例外がスローされた時点で実行を中断できます。

**例外設定**ウィンドウ (**デバッグ > Windows > 例外設定**) など、例外のカテゴリのノードを展開**Common Language Runtime Exceptions**. など、そのカテゴリ内の特定の例外のチェック ボックスを選択し、 **System.AccessViolationException**します。 例外のカテゴリ全体を選択することもできます。

![チェック AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> 使用して特定の例外を見つけることができます、**検索**ウィンドウで、**例外設定**ツールバー、または特定の名前空間をフィルター処理するために検索を使用して (よう**System.IO**)。

例外を選択した場合、**例外設定**ウィンドウで、それを処理するかどうかに関係なく、例外がスローされた場所に、デバッガーの実行が中断されます。 これで、例外には、初回例外が呼び出されます。 例として、いくつかのシナリオを以下に示します。

- 次の C# コンソール アプリケーションで、Main メソッドは `try/catch` ブロック内で **AccessViolationException** をスローします。

  ```csharp
  static void Main(string[] args)
  {
      try
      {
          throw new AccessViolationException();
          Console.WriteLine("here");
      }
      catch (Exception e)
      {
          Console.WriteLine("caught exception");
      }
      Console.WriteLine("goodbye");
  }
  ```

  あれば**AccessViolationException**チェックイン**例外設定**、実行が中断されます、`throw`デバッガーでこのコードを実行するときの行。 実行は続行することができます。 コンソールには、次の行が両方とも表示される必要があります。

  ```cmd
  caught exception
  goodbye
  ```

  表示されませんが、`here`行。

- AC#コンソール アプリケーションは、2 つのメソッドを持つクラスを使用してクラス ライブラリを参照します。 1 つのメソッドは、例外をスローし、2 番目のメソッドが同じ例外をスローしますが、その処理を行いません、それを処理します。

  ```csharp
  public class Class1
  {
      public void ThrowHandledException()
      {
          try
          {
              throw new AccessViolationException();
          }
          catch (AccessViolationException ave)
          {
              Console.WriteLine("caught exception" + ave.Message);
          }
      }

      public void ThrowUnhandledException()
      {
          throw new AccessViolationException();
      }
  }
  ```

  コンソール アプリケーションの Main() メソッドを次に示します。

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  あれば**AccessViolationException**チェックイン**例外設定**、実行が中断されます、`throw`両方で行**ある**と**ThrowUnhandledException()** デバッガーでこのコードを実行するとします。

例外の設定を既定値に復元するには、選択、**一覧を既定の設定に復元**ボタン。

![例外設定の既定値に戻す](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="BKMK_UserUnhandled"></a>ユーザーよって処理されない例外を続行するようにデバッガー

.NET や JavaScript コードをデバッグしている場合[マイ コードのみ](../debugger/just-my-code.md)、ユーザー コードで処理されないが、別の場所で処理される例外での中断を防ぐためにデバッガーを設定できます。

1. **例外設定**ウィンドウで、列のラベルを右クリックしてショートカット メニューを開き、クリックして**列を表示 > その他のアクション**します。 (オフになっている場合**マイ コードのみ**、このコマンドは表示されません)。という名前の 3 番目の列**生じず**が表示されます。

   ![アクション列の追加](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   例外を示す**ユーザー コードで処理されない場合は続行**でこの列は、デバッガーは引き続きかどうか、その例外はユーザー コードでハンドルされませんが、外部で処理されます。

2. 特定の例外は、この設定を変更する、例外を選択、ショートカット メニューを表示する右クリックして、選択**継続処理されない場合はユーザー コードで**します。 変更することも、全体の共通言語ランタイム例外などの例外のカテゴリ全体の設定)。

   ![* * * * コードのユーザーの設定で処理されない場合の続行](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

ASP.NET web アプリケーションが HTTP 500 ステータス コードに変換して例外を処理するなど、([ASP.NET Web API での例外処理](http://www.asp.net/web-api/overview/error-handling/exception-handling))、これも役に立ちません例外の原因を特定します。 次の例では、ユーザー コードは、 `String.Format()` をスローする <xref:System.FormatException>を呼び出します。 実行は次のように中断されます。

![ユーザーの中断&#45;ハンドルされない例外](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>例外を追加および削除する

例外は追加および削除することができます。 例外の種類カテゴリからを削除する、例外を選択し、選択、**を一覧から選択されている例外を削除**ボタン (マイナス記号) を**例外設定**ツールバー。 例外を右クリックし、選択することがありますまたは**削除**ショートカット メニューから。 例外を削除していますと同じ効果がオフの場合、例外がスローされたときに、デバッガーが中断しないことであります。

例外を追加します。

1. **例外設定**ウィンドウで、例外カテゴリのいずれかを選択します (たとえば、**共通言語ランタイム**)。

2. 選択、 **、選択したカテゴリに例外を追加**(プラス記号) ボタンをクリックします。

   ![* * を選択したカテゴリ * * ボタンに例外を追加する](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. 例外の名前を入力 (たとえば、 **System.UriTemplateMatchException**)。

   ![例外の名前を入力](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   例外が (アルファベット順) の一覧に追加され、自動的にオンにします。

GPU メモリ アクセス例外を JavaScript ランタイム例外をまたは Win32 例外というカテゴリに例外を追加するには、エラー コードと説明を含めます。

> [!TIP]
> スペルを確認してください。 **[例外設定]** ウィンドウでは、追加された例外の存在について確認が行われません。 したがって、「**Sytem.UriTemplateMatchException**」と入力した場合は、その例外のエントリ (**System.UriTemplateMatchException** のエントリではなく) が表示されます。

例外の設定はソリューションの .suo ファイルに保持され、特定のソリューションに適用されます。 複数のソリューションの間で、特定の例外設定を再利用することはできません。 これで、追加された例外のみが保持されます。削除された例外はありません。 閉じる、例外を追加して、ソリューションを再度、例外は削除されません。 しかし、例外を削除してから、ソリューションをいったん閉じて、再度開いた場合、例外は再表示されます。

**[例外設定]** ウィンドウでは、C# の汎用的な例外タイプをサポートしていますが、Visual Basic の汎用的な例外タイプはサポートしていません。 `MyNamespace.GenericException<T>`のような例外が発生したときに実行が中断されるようにするには、例外を **[MyNamespace.GenericException`1]** として追加する必要があります。 つまり、このコードのような例外を作成した場合。

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

例外を追加する**例外設定**前の手順を使用します。

![汎用の例外を追加する](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>例外に条件を追加します。

使用して、**例外設定**例外での条件を設定するウィンドウ。 現在サポートされている条件には、例外の追加または除外モジュール名が含まれます。 モジュール名を設定すると、条件としての特定のコード モジュールでのみ、例外で中断する選択できます。 特定のモジュールでの中断を回避することもできます。

> [!NOTE]
> 新機能では、例外条件の追加[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]します。

条件付きの例外を追加するには。

1. 選択、**条件の編集**例外設定 ウィンドウのボタンか、例外を右クリックして選択**条件の編集**します。

   ![例外条件](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. 例外には、必要な追加の条件を追加するには、選択**条件の追加**新しい条件ごとにします。 追加の条件の行が表示されます。

   ![例外の追加条件](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. 条件の行ごとに、モジュールの名前を入力し、比較演算子のリストを変更**Equals**または**Not Equals**します。 ワイルドカードを指定することがあります (**\\\***) では、複数のモジュールを指定する名前。

4. 条件を削除する必要がある場合は、選択、 **X**条件の行の最後にします。

## <a name="see-also"></a>関連項目

[例外後の実行の継続](../debugger/continuing-execution-after-an-exception.md)<br/>
[方法: 例外の後にシステム コードを調べる](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
[方法: ネイティブ ランタイム チェックを使用する](../debugger/how-to-use-native-run-time-checks.md)<br/>
[C ランタイム ライブラリなしのランタイム チェックを使用する](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
[デバッガーでのはじめに](../debugger/debugger-feature-tour.md)
