---
title: "単体テストの概要 - テスト計画の作成 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit testing, create unit test plans
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e6789c3a8ddb9b0aa317df0d2362d39946069cbd
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="get-started-with-unit-testing"></a>単体テストの概要

Visual Studio を使用して、単体テストを定義および実行してコードの正常性を維持し、コード カバレッジを保証し、事前にエラーとフォールトを見つけます。

<a name="create-tests"></a>
## <a name="create-unit-tests"></a>単体テストの作成

単体テストを作成し、コードが正しく動作していることを確認するために頻繁に実行します。

1. 単体テスト プロジェクトを作成します。
        
   ![単体テスト プロジェクトをソリューションに追加する](media/createunittest1.png)
    
1. プロジェクトに名前を付けます。
        
   ![単体テスト プロジェクト テンプレート](media/createunittest2.png)
  
   プロジェクトがソリューションに追加されます。
    
   ![ソリューション エクスプローラーの単体テスト プロジェクト](media/createunittest5.png)
    
1. 単体テスト プロジェクトで、テストするプロジェクトに参照を追加します。
        
   ![単体テストプロジェクトへの参照を追加する](media/createunittest6.png)
    
1. テストするコードを含むプロジェクトを選択します。
        
   ![追加する参照を選択する](media/createunittest7.png)
    
1. 単体テストのコードを作成します。

   ![コードを単体テストに追加する](media/createunittest8.png) 

[**[単体テストの作成]** コマンド](create-unit-tests-menu.md)を使用して、単体テスト メソッド スタブを作成することもできます。
または、[別の単体テスト フレームワーク](#frameworks)を使用して、別のコード言語のテストを作成できます。

![[単体テストの作成] コマンドの使用](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>単体テストを実行する

1. テスト エクスプローラーを開きます。
        
   ![[テスト] メニューで、テスト エクスプローラーを開く](media/rununittest1.png) 

1. 単体テストを実行します。
        
   ![テスト エクスプローラーでの単体テストの実行](media/rununittest2.png) 

   テスト エクスプローラーに成功または失敗した単体ユニット テストが表示されます。
      
   ![テスト エクスプローラーで単体テストの結果を確認する](media/rununittest3.png) 

## <a name="view-live-unit-test-results"></a>ライブ単体テストの結果を表示する

Visual Studio 2017 以降で MSTest、xUnit、または NUnit テスト フレームワークを使用する場合は、Visual Studio UI 内で単体テストのライブ結果を表示できます。

1. **[テスト]** メニューで、ライブ単体テストをオンにします。

   ![ライブ単体テストをオンにする](media/live-test-results-start.png) 

1. コードの作成および編集時に、コード エディター ウィンドウ内でテストの結果を表示します。

   ![テスト結果インジケーターをポイントしてクリックする](media/live-test-results-ui.png) 

1. テスト結果インジケーターをポイントしてクリックし、詳細を表示します。

   ![テスト結果を表示する](media/live-test-results-details.png) 

詳細については、[Visual Studio でのライブ単体テスト](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/live-unit-testing-visual-studio-2017-rc/)に関するページを参照してください。

<a name="intellitest"></a>
## <a name="generate-unit-tests-with-intellitest"></a>IntelliTest で単体テストを生成する

IntelliTest を実行すると、どのテストが失敗しているかを簡単に把握し、必要なコードを追加して修正できます。 回帰スイートを提供するために、生成されたどのテストをテスト プロジェクトに保存するかを選択できます。 コードを変更する際に、IntelliTest を再実行して、生成されたテストとコードの変更を同期させます。 その方法については、「[IntelliTest でのコードの単体テストの生成](../test/generate-unit-tests-for-your-code-with-intellitest.md)」を参照してください。

![IntelliTest での単体テストの生成](media/intellitest.png)

<a name="unit-tests"></a>
## <a name="run-unit-tests-with-test-explorer"></a>テスト エクスプローラーを使用して単体テストを実行する

テスト エクスプローラーを使用して、Visual Studio またはサードパーティの単体テスト プロジェクトから単体テストを実行し、テストをカテゴリにグループ化し、テスト リストをフィルター処理し、テストのプレイリストを作成、保存、および実行します。 テストをデバッグし、テストのパフォーマンスとコード カバレッジを分析することもできます。 その方法については、「[テスト エクスプローラーを使用して単体テストを実行する](../test/run-unit-tests-with-test-explorer.md)」を参照してください。

![テスト エクスプローラーを使用した単体テストの実行](media/testexplorer.png)

<a name="code-coverage"></a>
## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>コード カバレッジを使用した、テストされるコード割合の確認

単体テストなどのコード化されたテストによって実際にテストされるプロジェクトのコードの割合を調べるには、Visual Studio のコード カバレッジ機能を使用できます。 バグから効果的に保護するには、コードの大部分を "カバー" するようにテストを実行する必要があります。 その方法については、「[コード カバレッジを使用した、テストされるプロジェクトのコード割合の確認](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)」を参照してください。

![コード カバレッジを使用した、テストされるコード割合の確認](media/codecoverage.png)

## <a name="q--a"></a>Q & A

<!-- BEGINSECTION class="m-qanda" -->

<a name="frameworks"></a>
####Q: 別の単体テスト フレームワークを使用する場合、Visual Studio で単体テストを実行できますか?

A: はい。Visual Studio のテスト ランナーがそのフレームワークで作業できるようにそのフレームワークのプラグインを使用します。 [Visual Studio 用の単体テスト フレームワーク プラグイン](http://go.microsoft.com/fwlink/?LinkID=246630)がいくつかあります。

1. Visual Studio の拡張機能マネージャーを使用して、プラグインをダウンロードします。
        
   ![拡張機能マネージャーでサード パーティの単体テスト プラグインを選択する](media/install3rdpartyunittestframeworks1.png) 

1. [ツール] - [テスト] の下の Visual Studio ギャラリーからプラグインをダウンロードするか、名前がわかっている場合は検索します。
        
   ![プラグインのダウンロード](media/install3rdpartyunittestframeworks2.png) 

1. クラス ライブラリ プロジェクトを作成します。
        
   ![クラス ライブラリ プロジェクトを作成する](media/create3rdpartyunittest1.png) 

   プロジェクトをソリューションに追加します。
    
   ![クラス ライブラリ プロジェクトに名前を付けて追加する](media/create3rdpartyunittest3.png) 

1. クラス ライブラリ プロジェクトで、NuGet を実行してプラグインをインストールします。

   ![プラグインをインストールするための [NuGet パッケージの管理]](media/create3rdpartyunittest3a.png) 

   [NuGet](https://www.nuget.org/) はプロジェクトのライブラリとツールの追加および更新に使用できる Visual Studio の拡張機能です。

1. プラグインをインストールします。 名前がわかっている場合は、オンラインで検索することができます。

   ![サード パーティのフレームワークをインストールする](media/create3rdpartyunittest4.png) 

   フレームワークはプロジェクトで参照されます。
        
   ![サード パーティの単体テスト フレームワークの参照がソリューションに追加されている](media/create3rdpartyunittest6.png) 

1. クラス ライブラリ プロジェクトで、テストするプロジェクトに参照を追加します。
        
   ![プロジェクトに参照を追加する](media/createunittest6.png) 

1. テストするコードを含むプロジェクトを選択します。
        
   ![テストするコード プロジェクトを選択する](media/createunittest7.png) 

1. 単体テストのコードを作成します。

   ![コードを単体テストに追加する](media/create3rdpartyunittest7.png)   

<!-- ENDSECTION -->

## <a name="see-also"></a>関連項目

* [単体テスト コマンドの作成](create-unit-tests-menu.md)
* [IntelliTest でのテストの生成](generate-unit-tests-for-your-code-with-intellitest.md)
* [テスト エクスプローラーを使用してテストを実行する](run-unit-tests-with-test-explorer.md)
* [コード カバレッジを確認する](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [コード品質の向上](improve-code-quality.md)
