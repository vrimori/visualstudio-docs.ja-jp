---
title: "Visual Studio での Live Unit Testing | Microsoft Docs"
ms.date: 2017-03-07
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
ms.assetid: 5b51fb96-94f4-4926-92b9-262156c05b85
author: rpetrusha
ms.author: ronpet
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
ms.translationtype: Human Translation
ms.sourcegitcommit: c559290c8e88c8b4e37feabc7014188fad15434d
ms.openlocfilehash: 0a939044b9806236cf55333c30bce24ae0fdb28a
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017

---

# <a name="live-unit-testing-with-visual-studio-2017"></a>Visual Studio 2017 での Live Unit Testing

Live Unit Testing は、アプリケーションの開発中に、影響を受けた単体テストをバックグラウンドで自動的に実行して、結果とコード カバレッジを Visual Studio IDE にリアルタイムで表示します。 コードを変更すると、Live Unit Testing は、既存のテストへの変更の影響と、新しいコードが 1 つ以上の既存のテストによってカバーされているかどうかに関するフィードバックを提供します。 それにより、バグ修正や新機能の追加を行ったら単体テストを作成する必要があることを思い出させます。

> [!NOTE]
> Live Unit Testing は、Visual Studio 2017 の Enterprise Edition で .NET Core または .NET Framework を対象とする C# および Visual Basic プロジェクトに使うことができます。

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
   <td>xunit 2.0</td> 
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter バージョン 3.5.1</td>  
   <td>NUnit バージョン 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.11</td>
   <td>MSTest.TestFramework 1.1.11</td>
</tr>
</table>

既存のプロジェクトから以前のアダプターとテスト フレームワークを参照している場合は、必ずそれらを削除してください  (MSTest を使っている場合は、`Microsoft.VisualStudio.QualityTools.UnitTestFramework` の参照を削除したことを確認してください)。Live Unit Testing が動作しない場合は、新しく追加します。 

場合によっては、Live Unit Testing を動作させるため、ソリューションのプロジェクトによって参照されている NuGet パッケージの明示的な復元が必要になります。 そのためには、Living Unit Testing を有効にする前に、ソリューションの明示的なビルドを行うか (Visual Studio の最上位メニューから **[ビルド]** の **[ソリューションのリビルド]** を選択)、またはソリューションのパッケージを復元します (ソリューションを右クリックして **[NuGet パッケージの復元]** を選択)。 

#   <a name="configuring-live-unit-testing"></a>Live Unit Testing の構成

Live Unit Testing を構成するには、Visual Studio の最上位メニューから **[ツール]** の **[オプション]** を選び、**[オプション]** ダイアログの左側のウィンドウで **[Live Unit Testing]** を選びます。 次の図は、ダイアログで設定できる Live Unit Testing の構成オプションです。

  ![イメージ](./media/lut-options.png)

次のオプションを構成できます。

- ソリューションを開いたら Live Unit Testing を自動的に実行するかどうか。
- ソリューションをビルドしてデバッグするとき、またはシステムのバッテリ電源が指定したしきい値を下回ったときに、Live Unit Testing を一時停止するかどうか。
- テスト ケースがタイムアウトするまでの時間 (既定値は 30 秒)。 
- Live Unit Testing が作成するテスト プロセスの数。 
- Live Unit Testing の **[出力]** ウィンドウに書き込まれる情報のレベル。 オプションは、ログなし ([なし])、エラー メッセージのみ ([エラー])、エラーと情報メッセージ ([情報]、既定値)、またはすべての詳細 ([詳細]) です。

`VS_UTE_DIAGNOSTICS` という名前のユーザー レベル環境変数に値 "1" を設定して Visual Studio を再起動することにより、Live Unit Testing の **[出力]** ウィンドウに詳細な出力を表示することもできます。 

Live Unit Testing からファイルに詳細な MSBuild ログ メッセージをキャプチャするには、`LiveUnitTesting_BuildLog` ユーザー レベル環境変数に、ログを格納するファイルの名前を設定します。

## <a name="starting-pausing-and-stopping-live-unit-testing"></a>Live Unit Testing の開始、一時停止、停止

Live Unit Testing を有効にするには、Visual Studio の最上位メニューから **[テスト]**、**[Live Unit Testing]**、**[開始]** の順に選びます。 Live Unit Testing を有効にすると、**[Live Unit Testing]** メニューのオプションが、**[開始]** の 1 項目から、**[一時停止]**、**[停止]**、**[再起動]** に変わります。

いつでも、Live Unit Testing を一時停止または完全に停止できます。 たとえば、リファクタリングの途中で、しばらくテストが中断されることがわかっている場合に、これを行うことがあります。 3 つのメニュー オプションは次のとおりです。

- **[一時停止]** は、Live Unit Testing を一時的に中断します。 
    Live Unit Testing を一時停止すると、カバレッジの視覚化はエディターに表示されませんが、収集されたすべてのデータは保持されます。 Live Unit Testing を再開するには、Live Unit Testing のメニューから [続行] を選びます。 Live Unit Testing は、一時停止中に行われたすべての編集を取得するために必要な作業を実行し、グリフを適切に更新します。 
- **[停止]** は、Live Unit Testing を完全に停止します。 Live Unit Testing は収集したすべてのデータを破棄します。
- **[再起動]** は、**[Live Unit Testing]** メニューで **[停止]** を選んでから **[開始]** を選ぶのと同じです。

##  <a name="viewing-coverage-visualization-in-the-editor-as-you-type"></a>入力しながらエディターにカバレッジの視覚化を表示する

Live Unit Testing を有効にすると、Visual Studio エディターの各コード行が更新されて、記述しているコードが単体テストによってカバーされているかどうか、およびコードをカバーしているテストが合格かどうかが示されます。  次の図では、テストに合格したコード行と不合格のコード行、およびテストでカバーされていないコード行が示されています。 緑の "✓" で示される行は、合格したテストによってのみカバーされています。赤い "🞩" で示される行は、1 つ以上のテストで不合格になっています。青い "" によって示される行は、どのテストでもカバーされていません。

  ![イメージ](./media/lut-codewindow.png)

Live Unit Testing のカバレッジの視覚化は、コード エディターでコードを変更するとすぐに更新されます。 次の図のように、編集を処理している間は、合格、不合格、非カバーのシンボルの下に丸いタイマーのイメージを追加することで、データが最新ではないことが示されます。

  ![イメージ](./media/lut-codeupdating.png)
 
## <a name="getting-information-on-successful-or-failed-tests"></a>テストの合格または不合格に関する情報の取得

コード ウィンドウの合格または不合格のシンボルをカーソルでポイントすると、その行にヒットしているテストの数を確認できます。 シンボルをクリックすると、個々のテストの状態を確認できます (次の図を参照)。
 
  ![イメージ](./media/lut-failedinfo.png) 

ツール ヒントで不合格になったテストをポイントすると、次の図に示すように、不合格に関する追加情報が表示されます。 ツール ヒントで不合格なテストをクリックすると、追加情報に直接移動できます。

  ![イメージ](./media/lut-failedmsg.png) 

## <a name="diagnosing-and-correcting-test-failures"></a>不合格になったテストの診断と修正

不合格になったテストからは、簡単に製品コードをデバッグし、編集して、アプリケーションの開発を続けることができます。 Live Unit Testing はバックグラウンドで実行するので、デバッグ、編集、続行のサイクルの間も、Live Unit Testing を停止して再起動する必要はありません。

たとえば、前の図に示されている不合格なテストは、[Char.IsLower](xref:System.Char.IsLower(System.Char)) メソッドに非アルファベット文字を渡すと `true` が返るという、テスト メソッドでの誤った想定によるものです。 テスト メソッドを修正すると、すべてのテストに合格します。 これを行っている間、Live Unit Testing を一時停止または停止する必要はありません。

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing とテスト エクスプローラー

通常、**テスト エクスプローラー**では、実行、デバッグ、およびテスト結果の分析を行うことができるインターフェイスが提供されます。 Live Unit Testing は**テスト エクスプローラー**と統合します。 Live Unit Testing が有効になっていないか、停止されていると、**テスト エクスプローラー**には最後のテスト実行時の単体テストの状態が表示されます。 ソース コードを変更すると、テストを再実行する必要があります。 これに対し、Live Unit Testing が有効になっていると、**テスト エクスプローラー**の単体テストの状態はすぐに更新されます。 単体テストを明示的に実行する必要はありません。 

ただし、Live Unit Testing による自動的な実行およびテスト結果の更新と、**テスト エクスプローラー**からの明示的なテスト実行の間には、いくつかの違いがあります。 次の設定があります。

- [テスト エクスプローラー] ウィンドウからテストを実行またはデバッグすると標準バイナリが実行されますが、Live Unit Testing ではインストルメント化されたバイナリが実行されます。 
- Live Unit Testing ではテストを実行するために新しいアプリケーション ドメインは作成されず、既定のドメインからテストが実行されます。 **[テスト エクスプローラー]** ウィンドウからテストを実行すると、新しいアプリケーション ドメインが作成されます。
- Live Unit Testing では、各テスト アセンブリで順番にテストが実行されます。 **[テスト エクスプローラー]** ウィンドウから複数のテストを実行した場合、**[テストを並列で実行する]** ボタンが選ばれていると、テストは並列に実行されます。

## <a name="including-and-excluding-test-projects-and-test-methods"></a>テスト プロジェクトとテスト メソッドを含めるか除外する

多くのテスト プロジェクトを含むソリューションでは、Live Unit Testing に参加するプロジェクトおよびプロジェクト内の個別メソッドを制御できます。 

たとえば、数百のテスト プロジェクトを含むソリューションがある場合、Live Unit Testing に参加する対象のテスト プロジェクト セットを選ぶことができます。 単体テストで個別のプロジェクトを選ぶには、Live Unit Testing を開始した後で次のようにします。

1.  ソリューション全体を除外するには、ソリューション エクスプローラーでソリューションを右クリックし、**[Live Tests (ライブ テスト)]** の **[除外する]** を選びます。
2.  個別のテスト プロジェクトをテストに含めるには、各テスト プロジェクトを右クリックし、**[Live Tests (ライブ テスト)]** の **[含める]** を選びます。
 
個々のテスト メソッドを追加または除外するには、コード エディター ウィンドウを使います。 コード エディター ウィンドウでテスト メソッドのシグネチャを右クリックし、**[Live Tests (ライブ テスト)]** の **[含める]** または **[Live Tests (ライブ テスト)]** の **[除外する]** を選びます。 

または、[<ExcludeFromCodeCoverage>](https://msdn.microsoft.com/library/system.diagnostics.codeanalysis.excludefromcodecoverageattribute.aspx) 属性をプログラムで適用して、Live Unit Testing でのカバレッジのレポートからメソッド、クラス、または構造体を除外することもできます。

Live Unit Testing は、包含/除外の状態をユーザー設定として保存し、ソリューションを閉じて再び開くときに記憶しています。 

## <a name="see-also"></a>関連項目

[Live Unit Testing のブログ](https://go.microsoft.com/fwlink/?linkid=842514)   
[Live Unit Testing に関する FAQ](live-unit-testing-faq.md)    
[Channel 9 ビデオ: Visual Studio 2017 での Live Unit Testing](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)


