---
title: "Visual Studio での Live Unit Testing | Microsoft Docs"
ms.date: 2017-03-07
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
ms.assetid: 5b51fb96-94f4-4926-92b9-262156c05b85
author: rpetrusha
ms.author: ronpet
ms.workload: dotnet
ms.openlocfilehash: 45ab3f266a46cd08d269f0c463fb6cc26f494a91
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="live-unit-testing-with-visual-studio-2017"></a>Visual Studio 2017 での Live Unit Testing

Live Unit Testing は、アプリケーションの開発中に、影響を受けた単体テストをバックグラウンドで自動的に実行して、結果とコード カバレッジを Visual Studio IDE にリアルタイムで表示します。 コードを変更すると、Live Unit Testing は、既存のテストへの変更の影響と、新しいコードが 1 つ以上の既存のテストによってカバーされているかどうかに関するフィードバックを提供します。 それにより、バグ修正や新機能の追加を行ったら単体テストを作成する必要があることを思い出させます。

> [!NOTE]
> Live Unit Testing は、Visual Studio 2017 の Enterprise Edition で .NET Core または .NET Framework を対象とする C# および Visual Basic プロジェクトに使うことができます。

テストで Live Unit Testing を使用すると、テストの状態に関するデータが Live Unit Testing で保持されます。 保持されたデータを使用できることで、Live Unit Testing はコード変更に対応して動的にテストを実行しながら、優れたパフォーマンスを実現できます。
 
## <a name="supported-test-frameworks"></a>サポートされるテスト フレームワーク
Live Unit Testing は、次の表に示されている 3 つの一般的な単体テスト フレームワークで動作します。 アダプターやフレームワークのサポートされる最小バージョンも表に示されています。 単体テスト フレームワークはすべて NuGet.org から入手できます。
 
<table> 
<tr>
   <th>テスト フレームワーク</th>
   <th>Visual Studio アダプターの最小バージョン</th>
   <th>フレームワークの最小バージョン</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio バージョン 2.2.0-beta3-build1187</td>
   <td>xunit 1.9.2</td> 
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter バージョン 3.5.1</td>  
   <td>NUnit バージョン 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>MSTest.TestFramework 1.0.5-preview</td>
</tr>
</table>

`Microsoft.VisualStudio.QualityTools.UnitTestFramework` を参照している以前の MSTest に基づくテスト プロジェクトを使用しており、新しい MSTest NuGet パッケージへの移行を希望されない場合は、Visual Studio 2017 バージョン 15.4 にアップグレードしてください。 

場合によっては、Live Unit Testing を動作させるため、ソリューションのプロジェクトによって参照されている NuGet パッケージの明示的な復元が必要になります。 そのためには、Living Unit Testing を有効にする前に、ソリューションの明示的なビルドを行うか (Visual Studio の最上位メニューから **[ビルド]** の **[ソリューションのリビルド]** を選択)、またはソリューションのパッケージを復元します (ソリューションを右クリックして **[NuGet パッケージの復元]** を選択)。 

#   <a name="configuring-live-unit-testing"></a>Live Unit Testing の構成

Live Unit Testing を構成するには、Visual Studio の最上位メニューから **[ツール]** の **[オプション]** を選び、**[オプション]** ダイアログの左側のウィンドウで **[Live Unit Testing]** を選びます。 次の図は、ダイアログで設定できる Live Unit Testing の構成オプションです。

  ![イメージ](./media/lut-options.png)

次のオプションを構成できます。

- ソリューションをビルドしてデバッグするときに Live Unit Testing を一時停止するかどうか。
 
- システムのバッテリ電源が指定したしきい値を下回ったときに Live Unit Testing を一時停止するかどうか。
- ソリューションを開いたら Live Unit Testing を自動的に実行するかどうか。
- 保持されたデータを格納するディレクトリ。   
   **[Delete Persisted Data]/(保持されたデータの削除/)** ボタンをクリックすると、保持されたデータをすべて削除できます。 これは、Live Unit Testing で予測不能なまたは予期しない動作が発生している場合に便利です。この状態は、保持されたデータが破損していることを表しています。   
- テスト ケースがタイムアウトするまでの時間 (既定値は 30 秒)。 
- Live Unit Testing が作成するテスト プロセスの最大数。 
- Live Unit Testing のプロセスが使用できるメモリの最大容量。
- Live Unit Testing の **[出力]** ウィンドウに書き込まれる情報のレベル。   
   オプションは、ログなし (**[なし]**)、エラー メッセージのみ (**[エラー]**)、エラーと情報メッセージ (**[情報]**、既定値)、またはすべての詳細 (**[詳細]**) です。

`VS_UTE_DIAGNOSTICS` という名前のユーザー レベル環境変数に値 "1" を設定して Visual Studio を再起動することにより、Live Unit Testing の **[出力]** ウィンドウに詳細な出力を表示することもできます。 

Live Unit Testing からファイルに詳細な MSBuild ログ メッセージをキャプチャするには、`LiveUnitTesting_BuildLog` ユーザー レベル環境変数に、ログを格納するファイルの名前を設定します。

Live Unit Testing を有効にすると (次のセクション「[Live Unit Testing の開始、一時停止、停止](#starting-pausing-and-stopping-live-unit-testing)」を参照)、**[テスト]**、**[Live Unit Testing]**、**[オプション]** を選択して **[オプション]** ダイアログを開くこともできます。

## <a name="starting-pausing-and-stopping-live-unit-testing"></a>Live Unit Testing の開始、一時停止、停止

Live Unit Testing を有効にするには、Visual Studio の最上位メニューから **[テスト]**、**[Live Unit Testing]**、**[開始]** の順に選びます。 Live Unit Testing を有効にすると、**[Live Unit Testing]** メニューのオプションが、**[開始]** の 1 項目から、**[一時停止]**、**[停止]**、**[Reset Clean]/(クリーンのリセット/)** に変わります。

> [!NOTE]
> 単体テスト プロジェクトが含まれていないソリューションで Live Unit Testing を開始する場合、**Live Unit Testing** メニューには **[一時停止]**、**[停止]**、**[Reset Clean]\(クリーンのリセット\)** の各オプションが表示されますが、Live Unit Testing は開始されません。 **[出力]** ウィンドウには、"このソリューションではサポートされているテスト アダプターが参照されていません..." という内容で始まるメッセージが表示されます。  

いつでも、Live Unit Testing を一時停止または完全に停止できます。 たとえば、リファクタリングの途中で、しばらくテストが中断されることがわかっている場合に、これを行うことがあります。 3 つのメニュー オプションは次のとおりです。

- **[一時停止]** は、Live Unit Testing を一時的に中断します。 
 
    Live Unit Testing を一時停止すると、エディターにカバレッジの視覚化は表示されませんが、収集されたすべてのデータが保持されます。 Live Unit Testing を再開するには、Live Unit Testing メニューから **[続行]** を選びます。 Live Unit Testing は、一時停止中に行われたすべての編集を取得するために必要な作業を実行し、グリフを適切に更新します。 

- **[停止]** は、Live Unit Testing を完全に停止します。 Live Unit Testing は収集したすべてのデータを破棄します。

- **[Reset Clean]/(クリーンのリセット/)** は、Live Unit Testing を停止し、保持されたデータを削除し、Live Unit Testing を再起動します。

- **[オプション]** は、「[Live Unit Testing の構成](#configuring-live-unit-testing)」セクションに説明されている **[オプション]** ダイアログを開きます。
 
##  <a name="viewing-coverage-visualization-in-the-editor-as-you-type"></a>入力しながらエディターにカバレッジの視覚化を表示する

Live Unit Testing を有効にすると、Visual Studio エディターの各コード行が更新されて、記述しているコードが単体テストによってカバーされているかどうか、およびコードをカバーしているテストが合格かどうかが示されます。  次の図では、テストに合格したコード行と不合格のコード行、およびテストでカバーされていないコード行が示されています。 緑の "✓" で示される行は、すべてのテストに合格しています。赤い "x" で示される行は、1 つ以上のテストで不合格になっています。青い "➖" で示される行は、どのテストでもカバーされていません。

  ![イメージ](./media/lut-codewindow.png)

Live Unit Testing のカバレッジの視覚化は、コード エディターでコードを変更するとすぐに更新されます。 次の図のように、編集を処理している間は、合格、不合格、非カバーのシンボルの下に丸いタイマーのイメージを追加することで、データが最新ではないことが示されます。

  ![イメージ](./media/lut-codeupdating.png)
 
## <a name="getting-information-on-successful-or-failed-tests"></a>テストの合格または不合格に関する情報の取得

コード ウィンドウの合格または不合格のシンボルをカーソルでポイントすると、その行にヒットしているテストの数を確認できます。 シンボルをクリックすると、個々のテストの状態を確認できます (次の図を参照)。
 
  ![イメージ](./media/lut-failedinfo.png) 

さらに、テストの名前と結果を指定すると、ツールヒントで、デバッガーを使用して一連のテストを実行するだけでなく、一連のテストを再実行することもできます。 ツールヒントで 1 つ以上のテストを選択して、それらのテストのみを実行またはデバッグすることもできます。 これにより、コード ウィンドウから移動することなくテストをデバッグできます。 既に設定したブレークポイントを確認するときだけでなく、デバッグを実行するときにも、デバッガーが [ `Assert` ](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert) メソッドを実行して予期しない結果が返されると、プログラムの実行は一時停止します。 

ツールヒントで不合格になったテストをポイントすると、展開されて、次の図に示すような不合格に関する追加情報が表示されます。 不合格になったテストをツールヒントでダブルクリックすると、そのテストに直接移動できます。

  ![イメージ](./media/lut-failedmsg.png) 

不合格になったテストに移動すると、Live Unit Testing は合格したテスト (半分満たされたビーカーと緑の "✓" で示される)、不合格になったテスト (半分満たされたビーカーと赤の "🞩" で示される)、Live Unit Testing に含まれないテスト (半分満たされたビーカーと青の "➖" で示される) をメソッド シグネチャで視覚的に表示します。 テスト以外のメソッドにはシンボルは付きません。 次の図は、メソッドの 4 つのタイプすべてを示しています。
 
  ![イメージ](media/lut-testsource.png)
 
## <a name="diagnosing-and-correcting-test-failures"></a>不合格になったテストの診断と修正

不合格になったテストからは、簡単に製品コードをデバッグし、編集して、アプリケーションの開発を続けることができます。 Live Unit Testing はバックグラウンドで実行されるため、デバッグ、編集、続行のサイクルの間、Live Unit Testing を停止して再起動する必要はありません。

たとえば、前の図に示した不合格になったテストの原因は、<xref:System.Char.IsLower%2A?displayProperty=fullName> メソッドに非アルファベット文字を渡すと `true` が返るという、テスト メソッドでの誤った想定です。 このテスト メソッドを修正すると、すべてのテストに合格します。 これを行っている間、Live Unit Testing を一時停止または停止する必要はありません。

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing とテスト エクスプローラー

通常、**テスト エクスプローラー**では、実行、デバッグ、およびテスト結果の分析を行うことができるインターフェイスが提供されます。 Live Unit Testing は**テスト エクスプローラー**と統合します。 Live Unit Testing が有効になっていないか、停止されていると、**テスト エクスプローラー**には最後のテスト実行時の単体テストの状態が表示されます。 ソース コードを変更すると、テストを再実行する必要があります。 これに対し、Live Unit Testing が有効になっていると、**テスト エクスプローラー**の単体テストの状態はすぐに更新されます。 単体テストを明示的に実行する必要はありません。 

> [!NOTE]
> Visual Studio の上部にあるメニューで、**[テスト]**、**[Windows]**、**[テスト エクスプローラー]** の順に選択すると、**テスト エクスプローラー**を開くことができます。  

**テスト エクスプローラー** ウィンドウで、一部のテストがフェード アウトしているのに気付くことがあります。たとえば、以前保存したプロジェクトを開いた後に Live Unit Testing を有効にすると、次の図のように、**テスト エクスプローラー** ウィンドウで、不合格となったテストを除くすべてがフェード アウトします。 この場合、Live Unit Testing は不合格になったテストを返しますが、合格したテストは返しません。これは、Live Unit Testing の保持されたデータにより、テストが最後に正常実行されて以降は変更されていないことが示されているためです。

  ![イメージ](media/lut-test-explorer.png)

フェード アウトしたテストを再実行するには、**テスト エクスプローラー** メニューから **[すべて実行]** または **[実行]** オプションを選択するか、**テスト エクスプローラー** メニューで 1 つ以上のテストを選び、右クリックして、ポップアップ メニューから **[選択したテストの実行]** か **[選択したテストのデバッグ]** を選択します。 実行中のテストは最上部に表示されます。

Live Unit Testing で自動的にテストを実行してテスト結果を更新するのと、**テスト エクスプローラー**からテストを明示的に実行するのには、いくつかの違いがあります。 こうした違いには、次のようなものがあります。

- [テスト エクスプローラー] ウィンドウからテストを実行またはデバッグすると標準バイナリが実行されますが、Live Unit Testing ではインストルメント化されたバイナリが実行されます。 
- Live Unit Testing ではテストを実行するために新しいアプリケーション ドメインは作成されず、既定のドメインからテストが実行されます。 **[テスト エクスプローラー]** ウィンドウからテストを実行すると、新しいアプリケーション ドメインが作成されます。
- Live Unit Testing では、各テスト アセンブリで順番にテストが実行されます。 **[テスト エクスプローラー]** ウィンドウから複数のテストを実行した場合、**[テストを並列で実行する]** ボタンが選ばれていると、テストは並列で実行されます。

## <a name="live-unit-testing-and-large-solutions"></a>Live Unit Testing と大規模なソリューション

ご利用のソリューションに 10 個以上のプロジェクトがある場合、Live Unit Testing を開始したときに永続的データが存在しないと、または Visual Studio の上部にあるメニューで **[テスト]**、**[Live Unit Testing]**、**[Reset Clean]\(クリーンのリセット\)** オプションを順に選択すると、次のダイアログが Visual Studio に表示され、多数のプロジェクト内の多数のテストを動的に実行するとパフォーマンスに深刻な影響が出る可能性があることを警告します。 **[OK]** を選択すると、Live Unit Testing はそのソリューション内のすべてのテストを実行します。 **[キャンセル]** を選択すると、実行するテストを選択できます。 この方法の詳細については、次の「[テスト プロジェクトとテスト メソッドを含めるか除外する](#including-and-excluding-test-projects-and-test-methods)」セクションをご覧ください。  

 ![多数のプロジェクト用の Live Unit Testing ダイアログ](media/lut-large-project.png)

## <a name="including-and-excluding-test-projects-and-test-methods"></a>テスト プロジェクトとテスト メソッドを含めるか除外する

多くのテスト プロジェクトを含むソリューションでは、Live Unit Testing に参加するプロジェクトおよびプロジェクト内の個別メソッドを制御できます。 たとえば、数百のテスト プロジェクトを含むソリューションがある場合、Live Unit Testing に参加する対象のテスト プロジェクト セットを選ぶことができます。 このような選択を行う方法は多数あり、プロジェクトまたはソリューション内のすべてのテストを除外するか、大半のテストを含めるか除外するか、テストを個別に除外するかによって決まります。 Live Unit Testing は、包含/除外の状態をユーザー設定として保存し、ソリューションを閉じて再び開くときに記憶しています。 

**プロジェクトまたはソリューション内のすべてのテストを除外する**

単体テストで個別のプロジェクトを選ぶには、Live Unit Testing を開始した後で次のようにします。

1.  ソリューション全体を除外するには、ソリューション エクスプローラーでソリューションを右クリックし、**[Live Tests (ライブ テスト)]** の **[除外する]** を選びます。
1.  個別のテスト プロジェクトをテストに含めるには、各テスト プロジェクトを右クリックし、**[Live Tests (ライブ テスト)]** の **[含める]** を選びます。

**コード エディター ウィンドウからテストを個別に除外する**

テスト メソッドを個別に追加または除外する場合には、コード エディター ウィンドウを使います。 コード エディター ウィンドウで、テスト メソッドのシグネチャを右クリックして、**[Live Tests]/(ライブ テスト/)** - **[[選択したメソッド] を含める]**、**[Live Tests]/(ライブ テスト/)** - **[[選択したメソッド] を除外する]**、**[Live Tests]/(ライブ テスト/)** - **[[選択したメソッド] 以外のすべてを除外する]** のいずれかを選択します。ここで、"選択したメソッド" はコード ウィンドウで選択したメソッドの名前です。 

**プログラムによってテストを除外する** 

Live Unit Testing でのカバレッジのレポートからメソッド、クラス、または構造体をプログラムによって除外する場合には、<xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> 属性を適用できます。

また、Live Unit Testing からメソッドを個別に除外する場合は、次の属性も使用できます。

- xUnit の場合: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- NUnit の場合: `[Category("SkipWhenLiveUnitTesting")]`
- MSTest の場合: `[TestCategory("SkipWhenLiveUnitTesting")]` 
 
## <a name="see-also"></a>関連項目

[コード テスト ツール](https://www.visualstudio.com/vs/testing-tools/)   
[Live Unit Testing のブログ](https://go.microsoft.com/fwlink/?linkid=842514)   
[Live Unit Testing に関する FAQ](live-unit-testing-faq.md)    
[Channel 9 ビデオ: Visual Studio 2017 での Live Unit Testing](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)

