---
title: Visual Studio のヘルプを作成できるようにC#バグを使用したコード
description: バグをより優れたコードを記述する方法を理解します。
ms.custom: debug-experiments
ms.date: 11/20/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c16cfdc8d554ce9bf556ea707f977989e1dab72
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389378"
---
# <a name="fix-bugs-by-writing-better-c-code-using-visual-studio"></a>適切に記述することでバグを修正C#Visual Studio を使用するコード

コードをデバッグして、--かかることがあります、フラストレーション場合があります--タスク。 効果的にデバッグする方法については時間がかかります。 Visual Studio などの強力な IDE すると、ジョブがずっと容易になります。 IDE より迅速にコードをデバッグしてだけでなく、ですが、ヘルプのバグの減少より優れたコードを記述することができますが役立ちます。 この記事の目的は、コード アナライザーを使用するタイミングを知り、ときに、デバッガーを使用し、その他のツールを使用する場合に、デバッグのプロセスの全体像を提供すること。

この記事でこれは、デバッグ セッションは生産性を向上させる、IDE を活用することについて説明します。 などのいくつかのタスクでは、タッチと。

* IDE のコード アナライザーを活用することにより、デバッグ用のコードを準備します。

* 例外 (ランタイム エラー) を修正する方法

* 目的のためのコーディングでバグを最小限に抑える方法

* デバッガーを使用する場合

これらのタスクを示すためには、エラーと、アプリをデバッグするときに発生するバグの最も一般的な種類のいくつか説明します。 サンプル コードがC#、概念的な情報は、C++、Visual Basic、JavaScript に通常適用されると (場合を除き) Visual Studio で、他の言語がサポートされています。 スクリーン ショットは C# になっています。

## <a name="follow-along-using-the-sample-app"></a>サンプル アプリを使用して作業を進めるに

場合は、正確なバグを含む .NET Framework または .NET Core コンソール アプリとエラーが、ここでは、について説明し、作業を進めるにし、修正プログラムを自分でことができますを作成することができます。

アプリを作成する Visual Studio を開き、選択**ファイル > 新しいプロジェクト**します。 **Visual C#** 、選択**Windows デスクトップ**または **.NET Core**、中央のペインの 、**コンソール アプリ**します。 ような名前を入力**Console_Parse_JSON**  をクリック**OK**します。 Visual Studio によってプロジェクトが作成されます。 貼り付け、[サンプル コード](#sample-code)にプロジェクトの*Program.cs*ファイル。

> [!NOTE]
> **[コンソール アプリケーション]** プロジェクト テンプレートが表示されない場合は、**[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが起動します。 **[.NET デスクトップ開発]** または **[.NET Core クロスプラットフォームの開発]** ワークロードを選択し、**[変更]** を選択します。

## <a name="find-the-red-and-green-squiggles"></a>赤と緑の波線を確認してください。

サンプル アプリを起動し、デバッガーを実行する前に、赤、緑の波線のコード エディターでコードを確認します。 エラーと、IDE のコード アナライザーによって識別される警告を表現します。 赤い波線はコンパイル時のエラー コードを実行する前に修正する必要があることができます。 緑の波線は、警告です。 多くの場合、警告を修正することがなく、アプリも実行できますが、バグの原因になることができする多くの場合、時間とトラブルそれらを調査しています。 これらの警告とエラーにも表示されます、**エラー一覧**ウィンドウで、リスト ビューを使用する場合。

サンプル アプリで、修正する必要があるいくつかの赤の波線とでは、緑色の 1 つの 1 つ参照してください。 最初のエラーを示します。

![赤の波線として表示するエラー](../debugger/media/write-better-code-red-squiggle.png)

このエラーを修正するのには、電球アイコンで表される、IDE のもう 1 つの機能を見ていきます。

## <a name="check-the-light-bulb"></a>電球を確認してください。

赤い波線は、最初は、コンパイル時エラーを表します。 マウス ポインターを置くし、メッセージが表示```The name `Encoding` does not exist in the current context```します。

このエラーに下の左側に電球アイコンが表示されることを確認します。 ドライバーのアイコンと共に![ドライバーのアイコン](../ide/media/screwdriver-icon.png)、電球アイコン![電球アイコン](../ide/media/light-bulb-icon.png)インラインのコードにするのに役立つクイック アクションの修正またはリファクタリングを表します。 電球表します問題*は*修正します。 ドライバーでは、問題を修正することもできます。 クリックしてこのエラーを解決するのには、最初の推奨される修正プログラムを使用して**System.Text を使用して**左側です。

![電球を使用してコードを修正するには](../debugger/media/write-better-code-missing-include.png)

Visual Studio の追加は、この項目をクリックすると、`using System.Text`の上部にあるステートメント、 *Program.cs*ファイル、および赤の波線は表示されなくなります。 (は、推奨される解決がわからない場合は、選択、**変更のプレビュー**修正プログラムを適用する前に、右側にリンクします)。

上記のエラーは通常を追加して修正する一般的なもの`using`ステートメントをコードにします。 このいずれかにいくつかのように、一般的なエラーなどが```The type or namespace `Name` cannot be found.```この種のエラーは、不足しているアセンブリの参照である可能性があります (プロジェクトを右クリックし、選択**追加** > **の参照**)、スペルの正しくない名前、または NuGet を使用して追加する必要のある不足しているライブラリ (プロジェクトを右クリックし、選択**NuGet パッケージの管理**)。

## <a name="fix-the-errors-and-warnings"></a>エラーと警告を修正します。

このコードで確認する詳細について、いくつかの波線があります。 ここでは、一般的な型変換エラーを参照してください。 波線の上にマウス ポインターを移動するコードが、int に変換を行う明示的なコードを追加しない限り、サポートされていない文字列を変換しようとしていることを参照してください。

![型変換エラー](../debugger/media/write-better-code-conversion-error.png)

コード アナライザーは、ユーザーの意図を推測できない、ため、この時間をサポートするための電球がありません。 このエラーを解決するには、コードの意図を把握する必要があります。 この例ではないきわめて難しいことを確認する`points`追加しようとしているため、数値型 (integer) 値でなければなりません`points`に`totalpoints`します。

このエラーを修正するのには、変更、`points`のメンバー、`User`これからのクラス。

```csharp
[DataMember]
internal string points;
```

変更後は次のようになります。

```csharp
[DataMember]
internal int points;
```

コード エディターに赤い波線は表示されなくなりました。

次に、緑の波線の宣言でポインターを合わせる、`points`データ メンバー。 コード アナライザーは、変数は値を割り当てられませんを指示します。

![未割り当ての変数の警告メッセージ](../debugger/media/write-better-code-warning-message.png)

通常、これは修正する必要がある問題を表します。 ただし、サンプル アプリで実際に格納するデータを`points`、逆シリアル化プロセスおよび後にその値を追加中に変数、`totalpoints`データ メンバー。 この例で、コードの意図を知るし、警告を無視できます。 ただし、警告を除去する場合は、次のコードを置き換えることができます。

```csharp
item.totalpoints = users[i].points;
```

以下に置き換えます。

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

緑の波線表示されなくなります。

## <a name="fix-an-exception"></a>例外を修正します。

赤い波線がすべての修正および解決--または少なくとも調査 - が場合緑の波線をすべて準備が完了したら、アプリをデバッガーを起動して実行します。

**F5** キー (**[デバッグ] > [デバッグの開始]**) を押すか、またはデバッグ ツールバーの **[デバッグの開始]** ボタン ![デバッグの開始](../debugger/media/dbg-tour-start-debugging.png "デバッグの開始") を選択します。

この時点では、サンプル アプリがスローされます、`SerializationException`例外 (ランタイム エラー)。 つまり、アプリは、シリアル化しようとするデータのチョークします。 デバッグ モード (デバッガーをアタッチ) でアプリを起動したため、デバッガーの例外ヘルパーは例外をスローし、役に立つエラー メッセージを提供するコードに移動します。

![SerializationException に発生します](../debugger/media/write-better-code-serialization-exception.png)

エラー メッセージでは、するように指示する値`4o`を整数として解析できません。 そのため、この例で、データがわかってが正しくありません:`4o`べき`40`します。 ただし、実際のシナリオ (たとえば、web サービスから取得する) でデータの管理でないかどうかは、それについて実行して操作を行いますか? これをどのように解決すればよいでしょう。

例外が発生したときに、いくつかの質問を依頼 (と回答) する必要があります。

* この例外は、バグを修正するだけですか。 または

* この例外をユーザーが発生する可能性のあるものですか。

以前の場合は、バグを修正します。 (サンプル アプリでは、不適切なデータを修正することを意味する。)後者の場合、可能性がありますを使用してコードで例外を処理する必要があります。、 `try/catch` (見て次のセクションでその他の考えられる修正方法) をブロックします。 サンプル アプリで、次のコードに置き換えます。

```csharp
users = ser.ReadObject(ms) as User[];
```

を、次のコードで置換します。

```csharp
try
{
    users = ser.ReadObject(ms) as User[];
}
catch (SerializationException)
{
    Console.WriteLine("Give user some info or instructions, if necessary");
    // Take appropriate action for your app
}
```

A`try/catch`ブロックにはパフォーマンスの低下されたとき、に使用する本当に必要なつまり、(、) 可能性がありますが発生したアプリのリリース バージョンで、したいだけのため、(b)、ドキュメントのメソッドを示しますを確認する必要がありますして、(が完了すると、ドキュメントを想定)。 例外。 多くの場合、例外を適切に処理できるし、ユーザーがそれについて知っておく必要はありません。

次に、いくつかの例外処理の重要なヒントを示します。

* このような空の catch ブロックは使用しないでください`catch (Exception) {}`、公開またはエラーを処理する適切な操作を取らないしません。 空であるか有益ではない catch ブロックは例外を非表示にすることができ、コードを簡単ではなくデバッグが困難にすることができます。

* 使用して、`try/catch`前後例外をスローする特定の関数のブロック (`ReadObject`、サンプル アプリで)。 コードの大きなチャンクを使用する場合は、エラーの場所を非表示を終了します。 たとえば、使用しないでください、`try/catch`親関数の呼び出し前後のブロック`ReadToObject`を次に示します、例外が発生した正確にわかりませんか。

    ```csharp
    // Don't do this
    try
    {
        User[] users = ReadToObject(data);
    }
    catch (SerializationException)
    {
    }
    ```

* (Web 要求の場合) などの外部のデータを扱うもの expecially アプリに含めることがよく知らない関数では、どのような例外、関数をスローする可能性の高いドキュメントを確認してください。 これは、適切なエラー処理とアプリのデバッグに重要な情報を指定できます。

サンプル アプリでは、修正、`SerializationException`で、`GetJsonData`メソッドを変更して`4o`に`40`します。

## <a name="clarify-your-code-intent-by-using-assert"></a>Assert を使用して、コードの意図を明確化します。

デバッグ ツール バーの **[再起動]** ![アプリの再起動](../debugger/media/dbg-tour-restart.png "RestartApp") ボタンをクリックします (**Ctrl** + **Shift** + **F5**)。 これには、少ない手順で、アプリが再起動されます。 コンソール ウィンドウに次の出力を表示します。

![出力に null 値](../debugger/media/write-better-code-using-assert-null-output.png)

この出力が適切でないものを確認できます。 **名前**と**lastname** 3 番目のレコードが空白です。

これは、これを使用するには多くの場合、使用率が低い、便利なコーディング方法について説明するよい機会`assert`関数のステートメント。 次のコードを追加するには、ことを確認するランタイム チェックが含まれます。`firstname`と`lastname`ない`null`します。 次のコードに置き換えます、`UpdateRecords`メソッド。

```csharp
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

以下に置き換えます。

```csharp
// Also, add a using statement for System.Diagnostics at the start of the file.
Debug.Assert(users[i].firstname != null);
Debug.Assert(users[i].lastname != null);
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

追加することで`assert`開発プロセス中に、関数にこのようなステートメントをコードの意図を指定できることができます。 前の例では、次の指定します。

* 有効な文字列が最初の名前の必要です。
* 有効な文字列が姓に必要です。

この方法で目的を指定して、要件を強制します。 これは、開発中に表面的なバグに使用できる簡単で便利なメソッドです。 (`assert`ステートメントは、単体テストの主要な要素としても使用します)。

デバッグ ツール バーの **[再起動]** ![アプリの再起動](../debugger/media/dbg-tour-restart.png "RestartApp") ボタンをクリックします (**Ctrl** + **Shift** + **F5**)。

> [!NOTE]
> `assert`コードがデバッグ ビルドでのみアクティブになっています。

デバッガーが一時停止、再起動すると、`assert`ステートメントでは、ため、式`users[i].firstname != null`に評価される`false`の代わりに`true`。

![False に解決されるをアサートします。](../debugger/media/write-better-code-using-assert.png)

`assert`エラーは、調査する必要のある問題があることを示します。 `assert` 例外を必ずしも表示されない多くのシナリオに対応できます。 ユーザー、この例では、例外は表示されません、`null`として値を追加取得`firstname`レコードの一覧にします。 これは、問題が生じる後で (など、コンソール出力を参照してください) とデバッグが困難になる可能性があります。

> [!NOTE]
> メソッドを呼び出すシナリオで、`null`値、`NullReferenceException`結果。 通常使用しないようにする、`try/catch`は、特定のライブラリ関数に関連付けられていない例外での一般的な例外をブロックします。 任意のオブジェクトをスローできます、`NullReferenceException`します。 不明な場合は、ライブラリ関数のドキュメントを確認します。

デバッグのプロセス中には、特定をお勧め`assert`に実際のコードの修正プログラムを置き換える必要がありますがわかるまでのステートメント。 たとえば、ユーザーには、アプリのリリース ビルドで例外が発生する可能性がありますを決定したとします。 その場合は、アプリが致命的な例外をスローまたはその他のエラーが発生しないことを確認するためのコードをリファクタリングする必要があります。 そのため、このコードを修正するには、次のコードを置き換えます。

```csharp
if (existingUser == false)
{
    User user = new User();
```

を、次のコードで置換します。

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

このコードを使用すると、コードの要件を満たすし、ことを確認のレコードを`firstname`または`lastname`の値`null`データに追加されていません。

この例では、2 つを追加しました`assert`ループの内部でステートメント。 通常を使用する場合`assert`、追加することをお勧め`assert`関数またはメソッドのエントリ ポイント (最初) のステートメント。 表示されている現在、`UpdateRecords`サンプル アプリでのメソッド。 このメソッドでわかってメソッドの引数のいずれかの場合は問題になって`null`、その両方を確認、`assert`関数のエントリ ポイントでのステートメント。

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

既存のデータを読み込むことが目的に、上記のステートメントは (`db`) および新しいデータの取得 (`users`) 何も更新する前にします。

使用することができます`assert`に解決される式の種類を問わず`true`または`false`します。 そのため、たとえば、でしたを追加する、`assert`このようなステートメント。

```csharp
Debug.Assert(users[0].points > 0);
```

上記のコードは、次の目的を指定する場合に便利です。 新しいポイントよりも大きい値ゼロ (0) は、ユーザーのレコードを更新するために必要です。

## <a name="inspect-your-code-in-the-debugger"></a>デバッガーでコードを検査します。

[Ok]、できたので、サンプル アプリに問題があるすべての重要な修正した、その他の重要なデータに移動できます。

デバッガーの例外のヘルパーをしましたが、デバッガーがはるかに強力なツール、コードをステップ実行などの他の操作し、その変数を検査することもできますです。 これらのより強力な機能には、多くのシナリオ、特に、次があります。

* により、コードで、ランタイムのバグを分離しようとしているが、メソッドと既に説明したツールを使用してこれを行うことができません。

* つまり、コードの検証、期待どおりに動作して、目的の作業をするかどうかを確認する実行中に監視します。

    実行中に、コードを監視することができます。 このように、コードの詳細についてし、明らかな兆候をマニフェストが前に多くの場合、バグを特定できます。

デバッガーの基本機能を使用する方法については、次を参照してください。[超初心者向けのデバッグ](../debugger/debugging-absolute-beginners.md)します。

## <a name="fix-performance-issues"></a>パフォーマンスの問題を修正

別の種類のバグには、アプリの実行速度が遅い、または過度のメモリを使用すると、非効率的なコードが含まれます。 通常、パフォーマンスの最適化は後で、アプリの開発では、何か。 ただし、行うことができますのパフォーマンスの問題を早い段階 (たとえば、表示、アプリの一部が低速に実行されている)、およびプロファイリング ツールを使用してアプリを早い段階でテストする必要があります。 プロファイリング ツール、CPU 使用率ツールとメモリ アナライザーなどの詳細については、次を参照してください。[プロファイリング ツールの紹介](../profiling/profiling-feature-tour.md)します。

## <a name="sample-code"></a>サンプル コード

次のコードでは、Visual Studio IDE を使用して修正できるいくつかのバグを持っています。 ここで、アプリは、いくつかの操作、オブジェクトにデータを逆シリアル化し、新しいデータで単純なリストを更新していますから JSON データの取得をシミュレートする簡単なアプリです。

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON_DotNetCore
{
    class Program
    {
        static void Main(string[] args)
        {
            var localDB = LoadRecords();
            string data = GetJsonData();

            User[] users = ReadToObject(data);

            UpdateRecords(localDB, users);

            for (int i = 0; i < users.Length; i++)
            {
                List<User> result = localDB.FindAll(delegate (User u) { 
                    return u.lastname == users[i].lastname;
                    });
                foreach (var item in result)
                {
                    Console.WriteLine($"Matching Record, got name={item.firstname}, lastname={item.lastname}, age={item.totalpoints}");
                }
            }

            Console.ReadKey();
        }

        // Deserialize a JSON stream to a User object.  
        public static User[] ReadToObject(string json)
        {
            User deserializedUser = new User();
            User[] users = { };
            MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
            DataContractJsonSerializer ser = new DataContractJsonSerializer(users.GetType());

            users = ser.ReadObject(ms) as User[];

            ms.Close();
            return users;
        }

        // Simulated operation that returns JSON data.
        public static string GetJsonData()
        {
            string str = "[{ \"points\":4o,\"firstname\":\"Fred\",\"lastname\":\"Smith\"},{\"lastName\":\"Jackson\"}]";
            return str;
        }

        public static List<User> LoadRecords()
        {
            var db = new List<User> { };
            User user1 = new User();
            user1.firstname = "Joe";
            user1.lastname = "Smith";
            user1.totalpoints = 41;

            db.Add(user1);

            User user2 = new User();
            user2.firstname = "Pete";
            user2.lastname = "Peterson";
            user2.totalpoints = 30;

            db.Add(user2);

            return db;
        }
        public static void UpdateRecords(List<User> db, User[] users)
        {
            bool existingUser = false;

            for (int i = 0; i < users.Length; i++)
            {
                foreach (var item in db)
                {
                    if (item.lastname == users[i].lastname && item.firstname == users[i].firstname)
                    {
                        existingUser = true;
                        item.totalpoints += users[i].points;

                    }
                }
                if (existingUser == false)
                {
                    User user = new User();
                    user.firstname = users[i].firstname;
                    user.lastname = users[i].lastname;
                    user.totalpoints = users[i].points;

                    db.Add(user);
                }
            }
        }
    }

    [DataContract]
    internal class User
    {
        [DataMember]
        internal string firstname;

        [DataMember]
        internal string lastname;

        [DataMember]
        // internal double points;
        internal string points;

        [DataMember]
        internal int totalpoints;
    }
}
```

## <a name="next-steps"></a>次の手順

この記事では、回避およびコードで多くの一般的なバグを修正する方法と、デバッガーを使用する場合を説明しました。 次に、Visual Studio デバッガーを使用してバグを修正する方法の詳細について説明します。

> [!div class="nextstepaction"]
> [入門者向けのデバッグ](../debugger/debugging-absolute-beginners.md)
