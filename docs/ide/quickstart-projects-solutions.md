---
title: "Visual Studio でのプロジェクトとソリューションの概要 | Microsoft Docs"
ms.custom: 
ms.date: 12/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b757178f29439f162df9e8844ae65ed8df642bb5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-projects-and-solutions"></a>クイック スタート: プロジェクトとソリューション

この 10 分間のクイック スタートでは、Visual Studio でソリューションとプロジェクトを作成することの意味について説明します。 プロジェクトのプロパティと、プロジェクトに含めることができるファイルのいくつかを紹介します。 また、別のプロジェクトへの参照を作成することもできます。

> [!TIP]
> このクイック スタートでは、プロジェクトの概念を学習して理解するための演習として、ソリューションとプロジェクトをゼロから構築します。 Visual Studio の一般的な使い方として、新しいプロジェクトを作成するときは、ほとんどの場合、Visual Studio で用意されているさまざまなプロジェクト テンプレートを使用することができます。

> [!NOTE]
> Visual Studio でアプリを開発するにあたり、ソリューションとプロジェクトは必須ではありません。 また、コードが含まれているフォルダーを開いて、コードの作成、ビルド、およびデバッグを開始することもできます。 たとえば、GitHub リポジトリを複製しても、それには Visual Studio のプロジェクトとソリューションが含まれていない場合があります。 詳細については、「[プロジェクトまたはソリューションを使用せずに Visual Studio でコードを開発する](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)」を参照してください。

## <a name="solutions"></a>ソリューション

ソリューションとは、Visual Studio で 1 つまたは複数の関連プロジェクトを整理するために使用するコンテナーです。 Visual Studio でソリューションを開くと、ソリューションに含まれているすべてのプロジェクトが自動的に読み込まれます。

### <a name="create-a-solution"></a>ソリューションを作成する

空のソリューションを作成するところから説明を始めます。 Visual Studio に慣れてきても、空のソリューションが何度も作成されることには、ほとんど気づかないでしょう。 Visual Studio で新しいプロジェクトを作成するとき、ソリューションがまだ開いていなければ、プロジェクトを格納するためのソリューションが自動的に作成されます。

1. Visual Studio を起動します。

   Visual Studio が開くと、多くの場合は、ウィンドウの領域の大部分を占める **[スタート ページ]** が表示されます。

1. メニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** を選択します。

   **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

1. 左側のウィンドウで、**[その他のプロジェクトの種類]** を展開し、**[Visual Studio ソリューション]** を選択します。 中央のウィンドウで、**[空のソリューション]** を選択します。 ソリューションに "QuickSolution" という名前を付けて、**[OK]** を選択します。

   ![空のソリューション テンプレート](media/quickstart-projects-new-solution.png)

   **[スタート ページ]** が閉じて、Visual Studio ウィンドウの右側にある**ソリューション エクスプローラー**にソリューションが表示されます。 多くの場合、**ソリューション エクスプローラー**を使用して、プロジェクトの内容を参照することになります。

### <a name="add-a-project"></a>プロジェクトを追加する

次に、最初のプロジェクトをソリューションに追加してみましょう。 空のプロジェクトから始めて、そのプロジェクトに必要なアイテムを追加します。

1. **ソリューション エクスプローラー**で**ソリューション 'QuickSolution'** の右クリックまたはコンテキスト メニューから、**[追加]** > **[新しいプロジェクト]** を選択します。

   **[新しいプロジェクトの追加]** ダイアログ ボックスが表示されます。

1. 左側のウィンドウで、**[Visual C#]** を展開し、**[Windows クラシック デスクトップ]** を選択します。 次に、中央のウィンドウで、**[空のプロジェクト (.NET Framework)]** を選択します。 プロジェクトに "QuickDate" という名前を付けて **[OK]** ボタンをクリックします。

   **ソリューション エクスプローラー**で、ソリューションの下に "QuickDate" という名前のプロジェクトが表示されます。 現在のところ、このプロジェクトには **App.config** と呼ばれるファイルが 1 つ含まれています。

   > [!NOTE]
   > ダイアログ ボックスの左側のウィンドウに **Visual C#** が表示されない場合は、**.NET デスクトップ開発**ワークロードをインストールする必要があります。 このインストールは、左側のウィンドウの下部にあるリンク **[Visual Studio インストーラーを開く]** をクリックすると、簡単に行えます。 **Visual Studio インストーラー**が開いたら、そこで適切なワークロードを選択し、**[変更]** ボタンをクリックします。

   ![Visual Studio インストーラー リンクを開く](media/quickstart-projects-open-installer.png)

## <a name="add-an-item-to-the-project"></a>プロジェクトにアイテムを追加する

空のプロジェクトがあります&mdash;コード ファイルを追加してみましょう。

1. **ソリューション エクスプローラー**で **QuickDate** の右クリックまたはコンテキスト メニューから、**[追加]** > **[新しいプロジェクト]** を選択します。

   **[新しい項目の追加]** ダイアログ ボックスが開きます。

1. **[Visual C# アイテム]** を展開し、**[コード]** を選択します。 中央のウィンドウで、**[クラス]** を選択します。 クラスに "Calendar" という名前を付け、**[追加]** ボタンをクリックします。

   "Calendar.cs" という名前のファイルがプロジェクトに追加されます。 末尾の **.cs** は、C# コード ファイルに与えられるファイル拡張子です。 **ソリューション エクスプローラー**のビジュアル プロジェクト階層にファイルが表示され、その内容がエディターで開かれます。

1. **Calendar.cs** ファイルの内容を次のコードに置き換えます。

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

   このコードが何を行うかを理解する必要はありませんが、必要なら、プログラムを実行して、コンソール ウィンドウに今日の日付が出力されるのを確認することができます。

## <a name="add-a-second-project"></a>2 つ目のプロジェクトを追加する

ソリューションには複数のプロジェクトが含まれているのが一般的です。これらのプロジェクトは多くの場合、互いに参照しています。 ソリューション内に含めるプロジェクトはクラス ライブラリ、実行可能なアプリケーション、および単体テスト プロジェクトまたは Web サイトとすることができます。

単体テスト プロジェクトをソリューションに追加してみましょう。 今度はプロジェクト テンプレートから開始します。これにより、プロジェクトに追加のコード ファイルを追加する必要がなくなります。

1. **ソリューション エクスプローラー**で**ソリューション 'QuickSolution'** の右クリックまたはコンテキスト メニューから、**[追加]** > **[新しいプロジェクト]** を選択します。

   **[新しいプロジェクトの追加]** ダイアログ ボックスが表示されます。

1. 左側のウィンドウで、**[Visual Basic]** を展開し、**[テスト]** カテゴリを選択します。 中央のウィンドウで、**[単体テスト プロジェクト (.NET Framework)]** を選択します。 プロジェクトに "QuickTest" という名前を付けて、**[OK]** ボタンをクリックします。

   2 つ目のプロジェクトが**ソリューション エクスプローラー**に追加され、**UnitTest1.vb** という名前のファイルがエディターで開きます。 **.vb** は Visual Basic コード ファイルに付けられるファイル拡張子です。

   ![2 つのプロジェクトを含むソリューション エクスプローラー](media/quickstart-projects-solution-explorer.png)

## <a name="add-a-project-reference"></a>プロジェクト参照を追加する

これから、新しい単体テスト プロジェクトを使用して **QuickDate** プロジェクト内のメソッドをテストします。それには、そのプロジェクトへの参照を追加する必要があります。 そうすることで、2 つのプロジェクト間にビルドの依存関係が作成されます。つまり、ソリューションをビルドするとき、**QuickDate** がビルドされてから **QuickTest** がビルドされます。

1. **QuickTest** プロジェクトで **[参照]** ノードを選択し、右クリックまたはコンテキスト メニューから、**[参照の追加]** を選択します。

   ![[参照の追加] メニュー](media/quickstart-projects-add-reference.png)

   **[参照マネージャー]** ダイアログ ボックスが開きます。

1. 左側のウィンドウで、**[プロジェクト]** を展開し、**[ソリューション]** を選択します。 中央のウィンドウで、**QuickDate** の横にあるチェック ボックスを選択し、**[OK]** ボタンを選択します。

   **QuickDate** プロジェクトへの参照が追加されます。

## <a name="add-test-code"></a>テスト コードを追加する

1. ここで、Visual Basic コード ファイルにテスト コードを追加します。 **UnitTest1.vb** の内容を次のコードに置き換えます。

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   コードの一部分の下に赤色の "波線" が表示されます。 テスト プロジェクトを、**QuickDate** プロジェクトに対する[フレンド アセンブリ](/dotnet/csharp/programming-guide/concepts/assemblies-gac/friend-assemblies)にすることで、このエラーを修正します。

1. **QuickDate** プロジェクトに戻り、**Calendar.cs** ファイルがまだ開いていない場合は開きます。さらに次の using ステートメントと <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性を追加して、テスト プロジェクトのエラーを解決します。

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   コード ファイルは、次のようになります。

   ![CSharp コード](media/quickstart-projects-cs-code.png)

## <a name="project-properties"></a>プロジェクト プロパティ

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性を含む C# コード ファイル内の行は、**QuickTest** プロジェクトのアセンブリ名を参照します。 アセンブリ名はプロジェクト名と常に同じであるとは限りません。 プロジェクトのアセンブリ名を検索するには、プロジェクトのプロパティを開きます。

1. **ソリューション エクスプローラー**で **QuickTest** プロジェクトを選択します。 右クリックまたはコンテキスト メニューから、**[プロパティ]** を選択するか、または**Alt**+**Enter** キーを押します。

   **[アプリケーション]** タブで、プロジェクトのプロパティ ページが開きます。**QuickTest** プロジェクトのアセンブリ名が "QuickTest" であることに注目してください。 これを変更する場合は、ここでその変更を行います。 テスト プロジェクトをビルドすると、結果として得られる実行可能ファイルの名前は **QuickTest.exe** から、選択した任意の名前に変わります。

   ![プロジェクト プロパティ](media/quickstart-projects-properties.png)

1. **[コンパイル]** や **[設定]** など、プロジェクトのプロパティ ページの他のいくつかのタブを紹介します。 これらのタブは、プロジェクトの種類に応じて異なります。

## <a name="next-steps"></a>次の手順

単体テストが動作していることを確認する場合は、メニュー バーから **[テスト]** > **[実行]** > **[すべてのテスト]** を選択します。 **テスト エクスプローラー**と呼ばれるウィンドウが開くので、**TestGetCurrentDate** テストが成功しているか確認する必要があります。

このクイック スタートは完了しました。 次に、Visual Studio に関する他のクイック スタートを参照することがきます。あるいは、[プロジェクトおよびソリューションの作成](../ide/creating-solutions-and-projects.md)についてより深く学習することもできます。

## <a name="see-also"></a>関連項目

[クイックスタート: Visual Studio IDE の表示の紹介](../ide/quickstart-ide-orientation.md)  
[クイックスタート: Visual Studio IDE とエディターのカスタマイズ](../ide/quickstart-personalize-the-ide.md)  
[クイックスタート: エディター内のコーディング](../ide/quickstart-editor.md)  
[プロジェクトおよびソリューションのプロパティの管理](../ide/managing-project-and-solution-properties.md)  
[プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)  
[プロジェクトまたはソリューションを使用せずに Visual Studio でコードを開発する](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)  
[Visual Studio IDE の概要](../ide/visual-studio-ide.md)
