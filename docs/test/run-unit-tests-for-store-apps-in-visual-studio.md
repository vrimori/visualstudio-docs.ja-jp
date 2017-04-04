---
title: "Visual Studio でのストア アプリの単体テストの実行 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a6f5b32-bfce-4a63-81e9-02d54c592539
caps.latest.revision: 12
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4ecdcce4d45b15e6574ca70044249e4d32776fdd
ms.lasthandoff: 02/22/2017

---
# <a name="run-unit-tests-for-store-apps-in-visual-studio"></a>Visual Studio での ストア アプリの単体テストの実行
このトピックでは、Microsoft Visual Studio でテスト エクスプローラーを使用して単体テストを実行する方法について説明します。  
  
> [!NOTE]
>  このセクションのトピックでは、Visual Studio Express for Windows 8 の機能について解説します。 Visual Studio Community、Enterprise、および Professional には、単体テストの追加機能が備わっています。  
>   
>  -   Microsoft テスト エクスプローラーのアドオン アダプターを作成したサードパーティまたはオープン ソースの単体テスト フレームワークを使用します。 また、テストのコード カバレッジ情報を分析して表示することもできます。  
> -   ビルドの後に毎回テストを実行します。 Microsoft Fakes を使用することもできます。これは、システムおよびサードパーティの機能をテスト コードに置き換えることにより、自分のコードにテストの重点を置くことができる、マネージ コードの分離フレームワークです。  
>   
>  詳細については、「[コードの単体テスト](../test/unit-test-your-code.md)」を参照してください。  
  
##  <a name="BKMK_In_this_topic"></a> このトピックの内容  
 [単体テスト フレームワークとテスト プロジェクト](#BKMK_Unit_test_frameworks_and_test_projects)  
  
 [テスト エクスプローラーでテストを実行する](#BKMK_Running_tests_in_Test_Explorer)  
  
-   [テストの実行](#BKMK_Running_tests)  
  
 [テスト結果の表示](#BKMK_Viewing_test_results)  
  
-   [テストの詳細を表示する](#BKMK_Viewing_test_details)  
  
-   [テスト メソッドのソース コードの表示](#BKMK_Viewing_the_source_code_of_a_test_method)  
  
 [テスト一覧の整理](#BKMK_Organizing_the_test_list)  
  
-   [テストのグループ化](#BKMK_Grouping_tests)  
  
-   [テスト一覧の検索およびフィルター処理](#BKMK_Searching_and_filtering_the_test_list)  
  
 [単体テストのデバッグ](#BKMK_Debugging_unit_tests)  
  
##  <a name="BKMK_Unit_test_frameworks_and_test_projects"></a> 単体テスト フレームワークとテスト プロジェクト  
 Visual Studio Express for Windows Store Apps には、マネージ コードとネイティブ C++ コード用の Microsoft 単体テスト フレームワークが含まれています。 テスト エクスプローラーは、ソリューション内の複数のテスト プロジェクト、および運用コード プロジェクトに含まれるテスト クラスからテストを実行できます。 テスト プロジェクトには、Visual C++ または Visual C# と Visual Basic の単体テスト フレームワークを自由に組み合わせることができます。 テスト対象のコードを .NET Framework 用に記述する場合、対象コードの言語にかかわらず、テスト プロジェクトをどの .NET Framework 言語でも記述できます。 ネイティブ C/C++ コード プロジェクトは、C++ の単体テスト フレームワークを使用してテストする必要があります。  
  
##  <a name="BKMK_Running_tests_in_Test_Explorer"></a> テスト エクスプローラーでテストを実行する  
 テスト プロジェクトをビルドすると、テストはテスト エクスプローラーに表示されます。 テスト エクスプローラーが表示されない場合は、Visual Studio メニューの **[テスト]** をクリックし、 **[Windows]**、 **[テスト エクスプローラー]**の順に選択します。  
  
 ![単体テスト エクスプローラー](../ide/media/ute_failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")  
  
 テストを実行して、記述し、再実行すると、テスト エクスプローラーに **[失敗したテスト]**、 **[成功したテスト]**、 **[スキップされたテスト]** 、および **[テストを実行しない]**の既定のグループの結果が表示されます。 テスト エクスプローラーでテストをグループ化する方法を変更できます。  
  
 テスト エクスプローラーのツール バーからテストの検索、整理、および実行の作業の多くを実行できます。  
  
 ![テスト エクスプローラー ツールバーからテストを実行](../test/media/ute_toolbar.png "UTE_ToolBar")  
  
###  <a name="BKMK_Running_tests"></a> テストの実行  
 ソリューション内のすべてのテスト、グループ内のすべてのテスト、または選択した一連のテストを実行できます。 次のいずれかの操作を行います。  
  
-   ソリューション内のすべてのテストを実行するには、 **[すべて実行]**をクリックします。  
  
-   既定のグループ内のすべてのテストを実行するには、 **[実行]** をクリックし、メニューでグループを選択します。  
  
-   実行する個々のテストを選択し、選択したテストのショートカット メニューを開いて、**[選択したテストの実行]** を選択します。  
  
 テストの実行中、テスト エクスプローラー ウィンドウの一番上にある成功/失敗ステータス バーがアニメーション化されます。 テストの実行の終了時に、すべてのテストが成功した場合は、成功/失敗ステータス バーが緑色に変わり、いずれかのテストが失敗した場合は、赤色に変わります。  
  
##  <a name="BKMK_Viewing_test_results"></a> テスト結果の表示  
 テストを実行して、記述し、再実行すると、テスト エクスプローラーに **[失敗したテスト]**、 **[成功したテスト]**、 **[スキップされたテスト]** 、および **[テストを実行しない]**のグループの結果が表示されます。 テスト エクスプローラーの下部の詳細ペインに、テストの実行の概要が表示されます。  
  
###  <a name="BKMK_Viewing_test_details"></a> テストの詳細を表示する  
 個々のテストの詳細を表示するには、そのテストを選択します。  
  
 テストの詳細ペインに次の情報が表示されます。  
  
-   テスト メソッドのソース ファイル名と行番号。  
  
-   テストの状態。  
  
-   テスト メソッドの実行に要した経過時間。  
  
 テストが失敗した場合、詳細ペインには次の情報も表示されます。  
  
-   テストの単体テスト フレームワークによって返されたメッセージ。  
  
-   テストが失敗した時刻のスタック トレース。  
  
###  <a name="BKMK_Viewing_the_source_code_of_a_test_method"></a> テスト メソッドのソース コードの表示  
 Visual Studio エディターのテスト メソッドのソース コードを表示するには、テストを選択し、ショートカット メニューの **[テストを開く]** を選択します (キーボードの F12 キー)。  
  
##  <a name="BKMK_Organizing_the_test_list"></a> テスト一覧の整理  
  
###  <a name="BKMK_Grouping_tests"></a> テストのグループ化  
 既定では、テスト エクスプローラーに **[失敗したテスト]**、**[成功したテスト]**、**[スキップされたテスト]**、および **[未実行のテスト]** の子ノードとしてテストが表示されます。  
  
|||  
|-|-|  
|![テスト エクスプローラー グループ ボタン](../test/media/ute_groupby_btn.png "UTE_GroupBy_btn")|これらのテストの実行に要する時間によってテストをグループ化するには、**[グループ化]** ボックスの一覧を開き、**[期間]** を選択します。 元のグループに切り替えるには、**[テスト成果]** を選択します。|  
  
###  <a name="BKMK_Searching_and_filtering_the_test_list"></a> テスト一覧の検索およびフィルター処理  
 多数のテストがある場合、テスト エクスプローラーの検索ボックスに入力し、指定した文字列によって一覧をフィルター処理できます。 検索文字列を入力する前に、フィルターの一覧から選択して、フィルターを特定の種類の文字列に制限できます。  
  
 ![検索フィルターのカテゴリ](../test/media/ute_searchfilter.png "UTE_SearchFilter")  
  
##  <a name="BKMK_Debugging_unit_tests"></a> 単体テストのデバッグ  
 テスト エクスプローラーを使用して、テストのデバッグ セッションを開始できます。 Visual Studio デバッガーを使用してコードをシームレスにステップ実行すると、テスト対象のプロジェクトと単体テストの間を切り替えることができます。 デバッグを開始するには:  
  
1.  Visual Studio エディターで、デバッグする&1; つ以上のテスト メソッドにブレークポイントを設定します。  
  
    > [!NOTE]
    >  テスト メソッドを任意の順序で実行できるため、デバッグするすべてのテスト メソッドにブレークポイントを設定します。  
  
2.  テスト エクスプローラーでテスト メソッドを選択し、ショートカット メニューの **[選択したテストのデバッグ]** を選択します。  
  
 デバッガーの詳細については、「[Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)」を参照してください。

