---
title: Visual Studio でのプロジェクトとソリューションの概要
ms.date: 12/11/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e02be3774d0da28b96af0fb14ef64fd4bec6456e
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080725"
---
# <a name="quickstart-projects-and-solutions"></a>クイック スタート: プロジェクトとソリューション

この 10 分間のクイック スタートでは、Visual Studio で "*ソリューション*" と "*プロジェクト*" を作成することの意味について説明します。 ソリューションは、1 つまたは複数の関連するコード プロジェクトを整理するために使われるコンテナーです。たとえば、クラス ライブラリとそれに対応するテスト プロジェクトなどです。 プロジェクトのプロパティと、プロジェクトに含めることができるファイルのいくつかを紹介します。 また、あるプロジェクトから別のプロジェクトへの参照も作成します。

Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

プロジェクトの概念を学習して理解するための演習として、ソリューションとプロジェクトをゼロから構築します。 Visual Studio の一般的な使い方として、新しいプロジェクトを作成するときに、Visual Studio で用意されているさまざまなプロジェクト "*テンプレート*" を使うことがよくあります。

> [!NOTE]
> Visual Studio でアプリを開発するにあたり、ソリューションとプロジェクトは必須ではありません。 また、コードが含まれているフォルダーを開いて、コードの作成、ビルド、およびデバッグを開始することもできます。 たとえば、[GitHub](https://github.com/) リポジトリを複製しても、それには Visual Studio のプロジェクトとソリューションが含まれていない場合があります。 詳細については、「[プロジェクトまたはソリューションを使用せずに Visual Studio でコードを開発する](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)」を参照してください。

## <a name="solutions-and-projects"></a>ソリューションとプロジェクト

ソリューションとは、Visual Studio で 1 つまたは複数の関連プロジェクトを整理するために使用するコンテナーです。 Visual Studio でソリューションを開くと、ソリューションに含まれているすべてのプロジェクトが自動的に読み込まれます。

### <a name="create-a-solution"></a>ソリューションを作成する

空のソリューションを作成するところから説明を始めます。 Visual Studio に慣れてきても、自分が空のソリューションを頻繁に作成していることにはほとんど気づかないでしょう。 Visual Studio で新しいプロジェクトを作成するとき、ソリューションがまだ開いていなければ、プロジェクトを格納するためのソリューションが自動的に作成されます。

1. Visual Studio を開きます。

1. メニュー バー (**[ファイル]** や **[編集]** などのメニューの行) で、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。

   **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

1. 左側のウィンドウで、**[その他のプロジェクトの種類]** を展開し、**[Visual Studio ソリューション]** を選択します。 中央のウィンドウで、**[空のソリューション]** テンプレートを選択します。 ソリューションに「**QuickSolution**」という名前を付けて、**[OK]** ボタンを選択します。

   ![Visual Studio での空のソリューション テンプレート](media/quickstart-projects-new-solution.png)

   **[スタート ページ]** が閉じて、Visual Studio ウィンドウの右側にある**ソリューション エクスプローラー**にソリューションが表示されます。 多くの場合、**ソリューション エクスプローラー**を使用して、プロジェクトの内容を参照することになります。

### <a name="add-a-project"></a>プロジェクトを追加する

次に、最初のプロジェクトをソリューションに追加してみましょう。 空のプロジェクトから始めて、そのプロジェクトに必要なアイテムを追加します。

1. **ソリューション エクスプローラー**で**ソリューション 'QuickSolution'** の右クリックまたはコンテキスト メニューから、**[追加]**、**[新しいプロジェクト]** を選択します。

   **[新しいプロジェクトの追加]** ダイアログ ボックスが表示されます。

1. 左側のウィンドウで、**[Visual C#]** を展開し、**[Windows デスクトップ]** を選択します。 次に、中央のウィンドウで、**[空のプロジェクト (.NET Framework)]** テンプレートを選択します。 プロジェクトに「**QuickDate**」という名前を付けて、**[OK]** ボタンを選択します。

   **ソリューション エクスプローラー**で、ソリューションの下に QuickDate という名前のプロジェクトが表示されます。 現在のところ、このプロジェクトには *App.config* と呼ばれるファイルが 1 つ含まれています。

   > [!NOTE]
   > ダイアログ ボックスの左側のウィンドウに **Visual C#** が表示されない場合は、**.NET デスクトップ開発** Visual Studio "*ワークロード*" をインストールする必要があります。 Visual Studio は、ワークロード ベースのインストールを使って、行われる開発の種類に必要なコンポーネントだけをインストールします。 新しいワークロードをインストールする簡単な方法は、**[新しいプロジェクトの追加]** ダイアログ ボックスの左下隅にある **[Visual Studio インストーラーを開く]** リンクをクリックすることです。 Visual Studio インストーラーが起動した後、**[.NET デスクトップ開発]** ワークロードを選択して、**[変更]** ボタンを選択します。

   ![Visual Studio インストーラー リンクを開く](media/quickstart-projects-open-installer.png)

## <a name="add-an-item-to-the-project"></a>プロジェクトにアイテムを追加する

空のプロジェクトを用意しました。 コード ファイルを追加しましょう。

1. **ソリューション エクスプローラー**で **QuickDate** プロジェクトの右クリック メニューまたはコンテキスト メニューから、**[追加]** > **[新しいプロジェクト]** を選択します。

   **[新しい項目の追加]** ダイアログ ボックスが開きます。

1. **[Visual C# アイテム]** を展開し、**[コード]** を選択します。 中央のウィンドウで、**[クラス]** 項目テンプレートを選択します。 クラスに「**Calendar**」という名前を付け、**[追加]** ボタンを選択します。

   *Calendar.cs* という名前のファイルがプロジェクトに追加されます。 末尾の *.cs* は、C# コード ファイルに与えられるファイル拡張子です。 **ソリューション エクスプローラー**のビジュアル プロジェクト階層にファイルが表示され、その内容がエディターで開かれます。

1. *Calendar.cs* ファイルの内容を次のコードに置き換えます。

   ```csharp
   using System;

   namespace QuickDate
   {
       internal class Calendar
       {
           static void Main(string[] args)
           {
               DateTime now = GetCurrentDate();
               Console.WriteLine($"Today's date is {now}");
               Console.ReadLine();
           }

           internal static DateTime GetCurrentDate()
           {
               return DateTime.Now.Date;
           }
       }
   }
   ```

   このコードが何を行うかを理解する必要はありませんが、必要なら、プログラムを実行して、コンソール (または標準出力) ウィンドウに今日の日付が出力されるのを確認することができます。

## <a name="add-a-second-project"></a>2 つ目のプロジェクトを追加する

ソリューションには複数のプロジェクトが含まれているのが一般的です。これらのプロジェクトは多くの場合、互いに参照しています。 ソリューション内に含めるプロジェクトはクラス ライブラリ、実行可能なアプリケーション、および単体テスト プロジェクトまたは Web サイトとすることができます。

単体テスト プロジェクトをソリューションに追加してみましょう。 今度はプロジェクト テンプレートから開始します。これにより、プロジェクトに追加のコード ファイルを追加する必要がなくなります。

1. **ソリューション エクスプローラー**で**ソリューション 'QuickSolution'** の右クリックまたはコンテキスト メニューから、**[追加]**、**[新しいプロジェクト]** を選択します。

   **[新しいプロジェクトの追加]** ダイアログ ボックスが表示されます。

1. 左側のウィンドウで、**[Visual Basic]** を展開し、**[テスト]** カテゴリを選択します。 中央のウィンドウで、**[単体テスト プロジェクト (.NET Framework)]** プロジェクト テンプレートを選択します。 プロジェクトに「**QuickTest**」という名前を付けて、**[OK]** ボタンをクリックします。

   2 つ目のプロジェクトが**ソリューション エクスプローラー**に追加され、*UnitTest1.vb* という名前のファイルがエディターで開きます。 *.vb* は Visual Basic コード ファイルに付けられるファイル拡張子です。

   ![2 つのプロジェクトを含む Visual Studio ソリューション エクスプローラー](media/quickstart-projects-solution-explorer.png)

## <a name="add-a-project-reference"></a>プロジェクト参照を追加する

これから、新しい単体テスト プロジェクトを使用して **QuickDate** プロジェクト内のメソッドをテストします。それには、そのプロジェクトへの参照を追加する必要があります。 そうすることで、2 つのプロジェクトの間に "*ビルドの依存関係*" が作成されます。つまり、ソリューションをビルドすると、先に **QuickDate** がビルドされてから、**QuickTest** がビルドされます。

1. **QuickTest** プロジェクトで **[参照]** ノードを選択し、右クリックまたはコンテキスト メニューから、**[参照の追加]** を選択します。

   ![[参照の追加] メニュー](media/quickstart-projects-add-reference.png)

   **[参照マネージャー]** ダイアログ ボックスが開きます。

1. 左側のウィンドウで、**[プロジェクト]** を展開し、**[ソリューション]** を選択します。 中央のウィンドウで、**QuickDate** の横にあるチェック ボックスを選択し、**[OK]** ボタンを選択します。

   **QuickDate** プロジェクトへの参照が追加されます。

## <a name="add-test-code"></a>テスト コードを追加する

1. ここで、Visual Basic コード ファイルにテスト コードを追加します。 *UnitTest1.vb* の内容を次のコードに置き換えます。

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   コードの一部分の下に赤色の "波線" が表示されます。 テスト プロジェクトを、**QuickDate** プロジェクトに対する[フレンド アセンブリ](/dotnet/csharp/programming-guide/concepts/assemblies-gac/friend-assemblies)にすることで、このエラーを修正します。

1. **QuickDate** プロジェクトに戻り、*Calendar.cs* ファイルをまだ開いていない場合は開きます。さらに、次の [using ステートメント](/dotnet/csharp/language-reference/keywords/using-statement)と <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性を追加して、テスト プロジェクトのエラーを解決します。

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   コード ファイルは、次のようになります。

   ![CSharp コード](media/quickstart-projects-cs-code.png)

## <a name="project-properties"></a>プロジェクト プロパティ

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性を含む C# コード ファイル内の行は、**QuickTest** プロジェクトのアセンブリ名 (ファイル名) を参照します。 アセンブリ名はプロジェクト名と常に同じであるとは限りません。 プロジェクトのアセンブリ名を検索するには、プロジェクトのプロパティを開きます。

1. **ソリューション エクスプローラー**で **QuickTest** プロジェクトを選択します。 右クリックまたはコンテキスト メニューから、**[プロパティ]** を選択するか、または**Alt**+**Enter** キーを押します。

   **[アプリケーション]** タブで、プロジェクトの "*プロパティ ページ*" が開きます。プロパティ ページには、プロジェクトのさまざまな設定が含まれます。 **QuickTest** プロジェクトのアセンブリ名が "QuickTest" であることに注目してください。 これを変更する場合は、ここでその変更を行います。 テスト プロジェクトをビルドすると、結果として得られる実行可能ファイルの名前は *QuickTest.exe* から、選択した任意の名前に変わります。

   ![プロジェクト プロパティ](media/quickstart-projects-properties.png)

1. **[コンパイル]** や **[設定]** など、プロジェクトのプロパティ ページの他のいくつかのタブを紹介します。 これらのタブは、プロジェクトの種類によって異なります。

## <a name="next-steps"></a>次の手順

単体テストが動作していることを確認する場合は、メニュー バーから **[テスト]** > **[実行]** > **[すべてのテスト]** を選択します。 **テスト エクスプローラー**と呼ばれるウィンドウが開くので、**TestGetCurrentDate** テストが成功しているか確認する必要があります。

このクイック スタートは完了しました。 次に、Visual Studio に関する他のクイック スタートを参照したり、[プロジェクトとソリューションの作成](../ide/creating-solutions-and-projects.md)についてより深く学習することもできます。

## <a name="see-also"></a>関連項目

- [クイックスタート: Visual Studio IDE の表示の紹介](../ide/quickstart-ide-orientation.md)
- [クイックスタート: Visual Studio IDE とエディターのカスタマイズ](../ide/quickstart-personalize-the-ide.md)
- [クイックスタート: エディター内のコーディング](../ide/quickstart-editor.md)
- [プロジェクトおよびソリューションのプロパティの管理](../ide/managing-project-and-solution-properties.md)
- [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)
- [プロジェクトまたはソリューションを使用せずに Visual Studio でコードを開発する](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE の概要](../ide/visual-studio-ide.md)