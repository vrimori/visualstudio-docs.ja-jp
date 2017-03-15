---
title: "Visual Studio 2017 RC の新機能 | Microsoft Docs"
ms.custom: 
ms.date: 12/13/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 4fb097ab0ee0d45fd5727e3170db3393392abf23
ms.openlocfilehash: dc1941fd755c28039560b608733067b1da365c3a

---
# <a name="what39s-new-in-visual-studio-2017"></a>Visual Studio 2017 の新機能
Visual Studio 2017 RC へようこそ。これは開発者用の生産性ツール、クラウド サービス、および拡張機能の統合されたスイートであり、お客様およびチームが、Web、Windows ストア、デスクトップ、Android および iOS 用のアプリやゲームを作成できるようにするものです。  

最新バージョンの Visual Studio のこのリリース候補 (RC) では、パフォーマンスと生産性の向上に注目しました。 パフォーマンスについては、Visual Studio を以前より速く、応答性を高め、メモリの使用量を節約するようにしています。 また、生産性については、Visual Studio の使用時に効率を高められるように、機能を追加または更新しました。

> [!TIP]
> 新しいリリース候補の操作を確認するには、Channel 9 で 「[What's New in Visual Studio](https://channel9.msdn.com/events/connect/2016/159)」 (Visual Studio の新機能) のビデオをご覧ください。   

変更を行った基本的な概要は、次のとおりです。

* **生産性の増強**。 コード ナビゲーション、IntelliSense、リファクタリング、コード修正、デバッグの各機能が強化され、言語やプラットフォームに関係なく、日々のタスクで時間と労力を節約できます。 さらに、DevOps を取り入れているチームは、Visual Studio 2017 で、ライブ単体テストやリアルタイム アーキテクチャ依存関係検証などの新しいリアルタイムの機能を使用して、開発者の内部ループを効率化し、コード フローを高速化できます。
* **基本の再定義**。  毎日開発者が行う基本的なタスクの効率を高めることが改めて重視されました。 開発者のニーズに合わせてカスタマイズできる新しい軽量のモジュール式のインストール、スタートアップからシャットダウンまで高速な IDE、プロジェクトやソリューションなしであらゆるコードの表示と編集とデバッグが行える新しい方法などの機能により、Visual Studio 2017 は、開発者が全体像をとらえ続けられるようお手伝いします。
* **Azure 開発の簡素化**。 Microsoft Azure を使用するクラウド ファーストのアプリケーションを開発者が簡単に作成できる Azure ツールのビルトイン スイート。 Visual Studio を使用すれば、IDE から直接 Microsoft Azure でアプリケーションとサービスを構成、ビルド、デバッグ、パッケージ化、展開するのが容易になります。
* **優れたモバイル開発**。 高度なデバッグ ツールとプロファイル ツールや単体テスト生成機能を備えた Visual Studio 2017 と Xamarin を使用すれば、開発者が Android、iOS、Windows 用モバイル アプリをこれまでになく高速かつ簡単にビルド、接続、調整できます。 開発者は、Visual Studio に含まれる、Apache Cordova または Visual C++ のクロスプラットフォーム ライブラリ開発を使用したモバイル アプリ開発を選択することもできます。  

また、最も注目すべき変更の詳細を次に示します。

> [!NOTE]
> Visual Studio 2017 RC の新機能および後続の RC Refresh の完全な一覧については、「[リリース ノート](https://www.visualstudio.com/news/vs2015-vs)」を参照してください。 また、問題と回避策の一覧については、リリース ノートの「[既知の問題](https://www.visualstudio.com/news/vs2015-vs#knownissues)」セクションを参照してください。   

## <a name="performance-improvements"></a>パフォーマンスの向上

### <a name="a-new-setup-experience"></a>新しいセットアップ エクスペリエンス  
[Visual Studio Enterprise 2017 のダウンロード](https://aka.ms/vs/15/preview/vs_enterprise)または [Visual Studio システム要件の確認](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 必要なときに必要な機能を容易にインストールできるように、Visual Studio セットアップ エクスペリエンスを再設計しました。 また、最小フットプリントも減らしているため、Visual Studio はシステムへの影響をより少なくかつ迅速にインストールされます。 また、アンインストールも正常に行われます。

 Visual Studio をインストールするときに確認できる最も重要な変更は、その新しいインストール エクスペリエンスです。 **[ワークロード]** タブには、一般的なフレームワーク、言語、プラットフォームを表すためにグループ化されたインストール オプションが表示されます。これは、.NET のデスクトップ開発から R、Python、F# でのデータ サイエンスまでのあらゆるものをカバーしています。  

 ![[Visual Studio 2017 RC のセットアップ] ダイアログ](../ide/media/willow1.png "VS2017RC_Setup_screen")

必要なワークロードを選択し、必要に応じてそれらを変更します。 最小のインストールはわずか数百 MB ですが、それでも&20; を超える言語の基本的なコード編集サポートとソース コード管理が含まれます。

Visual Studio をインストールする別の方法も追加しています。 ワークロードを使用する代わりに、独自のコンポーネントを選択するには、 インストーラーから **[個別のコンポーネント]** タブを選択するだけです。 また、Windows の言語オプションを変更することなく、言語パックをインストールする場合は、 インストーラーの **[言語パック]** タブを選択します。  

ステップ バイ ステップの手順を含む、新しいインストール エクスペリエンスの詳細については、[Visual Studio のインストール](../install/install-visual-studio.md)に関するページを参照してください。


### <a name="start-visual-studio-faster"></a>Visual Studio の起動の高速化
Visual Studio で起動時間が遅い IDE が検出された場合、高速化できるように新しい Visual Studio パフォーマンス センターが示されます。 パフォーマンス センターでは、IDE の起動を遅くしている拡張機能やツール ウィンドウをすべて一覧表示します。 拡張機能を起動するタイミングや、ツール ウィンドウを起動時に開くかどうかを指定して、起動時のパフォーマンスを向上させるために使用することができます。

### <a name="decrease-solution-load-time"></a>ソリューションの読み込み時間の短縮
100 以上のプロジェクトを含む、ソリューションでの作業でも、一度にすべてのファイルまたはプロジェクトを使用する必要があるというわけではありません。 ここでは、Visual Studio がすべてのプロジェクトを読み込むのを待たずに、編集やデバッグを行えるようになりました。 マネージ プロジェクトでこれを試すには、[ツール]、[オプション]、[プロジェクトおよびソリューション] の順に選択して、**[Lightweight Solution load]** (ライトウェイト ソリューション ロード) をオンにします。

  ![Visual Studio 2017 RC の [オプション] ダイアログ ボックス](../ide/media/vs2017ide-LightweightSolutionLoad.PNG "VS2017RC Options dialog box - Lightweight Solution Load")

### <a name="faster-on-demand-loading-of-extensions"></a>拡張機能のオンデマンド読み込みの高速化
考え方は単純です。Visual Studio の起動時ではなく、必要なときに拡張機能を読み込みます。 最初に、Python と Xamarin の拡張機能をオンデマンドの読み込みに移行しました。次に、Visual Studio で提供するすべての拡張機能 (およびサードパーティのベンダーから提供された拡張機能) をこのモデルに移行するよう取り組んでいます。 どの拡張機能が起動、ソリューションの読み込み、および入力パフォーマンスに影響があるかについて関心をお持ちですか? この情報については、[ヘルプ]、[Visual Studio のパフォーマンスの管理] の順に選択して確認することができます。

  ![Visual Studio 2017 RC の [オプション] ダイアログ ボックス](../ide/media/vs2017ide-ManageVSperf.png "VS2017RC Help dialog box - Performance Management")

## <a name="productivity-improvements"></a>生産性の向上

### <a name="sign-in-across-multiple-accounts"></a>複数のアカウント間のサインイン  
チーム エクスプ ローラー、Azure のツール、Windows ストアの発行などの Microsoft 開発者ツール間でユーザー アカウントを共有できるように、Visual Studio 2017 RC で新しい ID サービスを導入しました。

また、長時間サインインし続けることもできます。12 時間ごとにもう一度サインインすることを求めることはありません。 詳細については、「[Fewer Visual Studio Sign-in Prompts](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/)」 (Visual Studio のサインインの確認メッセージを減らす) のブログの投稿を参照してください。

### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>[拡張機能マネージャーのローミング] で拡張機能を管理する
Visual Studio にサインインすると、お気に入りの拡張機能を使用して、各開発環境を容易に設定できるようになりました。 クラウドに同期されたリストを作成すると、新しい [拡張機能マネージャーのローミング] では、お気に入りの拡張機能をすべて追跡し続けます。  

Visual Studio の拡張機能の一覧を表示するには、[ツール]、[拡張機能と更新プログラム] の順にクリックし、[拡張機能マネージャーのローミング] をクリックします。

![Visual Studio 2017 - [拡張機能と更新プログラム] ダイアログ](../ide/media/vs2017ide-ExtensionsAndUpdates.png "Visual Studio 2017 - Tools > Extensions and Updates dialog")

[拡張機能マネージャーのローミング] では、インストールするすべての拡張機能を追跡しますが、どの拡張機能をローミング リストに追加するかを選択することができます。

![Visual Studio 2017 - [拡張機能と更新プログラム] ダイアログ](../ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 - Roaming Extension Manager")

[拡張機能マネージャーのローミング] を使用する場合、リストに次の 3 つの種類のアイコンが表示されます。
* ![ローミング済みアイコン](../ide/media/vs2017ide-roamedicon.png "Roamed Icon") ***ローミング済みアイコン***: ローミング リストにあり、このコンピューターにはインストールされていない拡張機能を示します。
  (これらの拡張機能は、**[ダウンロード]** ボタンでインストールできます。)
* ![ローミングおよびインストール済みアイコン](../ide/media/vs2017ide-roamedinstalledicon.png "Roamed and Installed Icon") ***ローミングおよびインストール済みアイコン***: ローミング リストにあり、使用している開発環境にインストールされているすべての拡張機能を示します。
  (ローミングしない場合は、**[ローミングの停止]** ボタンで削除することができます。)
* ![インストール済みアイコン](../ide/media/vs2017ide-installedicon.png "Installed Icon") ***インストール済みアイコン***: この環境にインストールされ、ローミング リストにはないすべての拡張機能を示します。
  (**[ローミングの開始]** ボタンを使用して、拡張機能をローミング リストに追加できます。)

これらのアイコンは、リストの現在の状態を示しています。 任意の状態の任意の拡張機能を使用できるので、好みに合わせてカスタマイズするか、 既定の設定を利用してください。 サインイン中にダウンロードした拡張機能は、**[Roamed & Installed]** (ローミングおよびインストール済み) としてリストに追加され、ローミング リストに表示されます。そのため、どのコンピューターからでもアクセスできるようになります。

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>ライブ アーキテクチャの依存関係検証とライブ単体テストのエクスペリエンス

Visual Studio Enterprise 2017 RC では、依存関係検証ダイアグラム ( レイヤー ダイアグラム) を設定している場合、コード エディターにコードを入力すると、リアルタイムでアーキテクチャの依存関係ルールの違反を確認できるようになりました。

エラーは [エラー一覧] に表示され、テキスト エディターの波線は違反の正確な位置を示します。 不要な依存関係を導入する可能性を低減できるようになります。

![ライブ アーキテクチャの検証](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "Live Architecture Dependency validation")

#### <a name="live-unit-testing"></a>ライブ単体テスト

ライブ単体テストは、新しく導入された機能で、Visual Studio の Enterprise Edition にのみ存在します。 この機能は、コーディング中に、単体テストの結果とコード カバレッジをエディター上でライブで視覚化します。 これは、.NET Framework の C# または VB プロジェクトに対応し、MSTest、xUnit、および NUnit の&3; つのテスト フレームワークをサポートします。

### <a name="visual-studio-ide-enhancements"></a>Visual Studio IDE の拡張機能
#### <a name="interact-with-git"></a>Git との連携
Visual Studio IDE の下隅のコントロールでは、プロジェクトを Git にすぐにコミットおよび発行したり、Git リポジトリを管理したりすることができます。

![[Visual Studio 2017 RC のセットアップ] ダイアログ](../ide/media/vsIDE-GitInteraction.png "Git-tools-in-the-VS2017RC-IDE")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>構造ビジュアライザーを使用したコードの表示と移動
構造ビジュアライザーと呼ばれる新しい機能は、Visual Studio コード エディターで使用できます。 この機能は、入れ子になったコードの領域間に垂直方向のガイドラインを示し、コード内の表示および移動を容易にします。 この機能は、TextMate でサポートされるすべての言語だけでなく、Visual C#、Visual Basic、および XAML で使用できます。

![[Visual Studio 2017 RC のセットアップ] ダイアログ](../ide/media/vsIDE-StructureVisualizer.png "Structure-Visualizer-in-VS2017RC")

#### <a name="experience-an-improved-navigate-to"></a>改善された [移動] のエクスペリエンス
[移動] 機能を改善しました。 [移動] ウィンドウを簡略化し、コード検索を絞り込めるように追加のフィルター文字のサポートを追加しました。

#### <a name="create-apps-in-even-more-programming-languages"></a>さらに多くのプログラミング言語でのアプリの作成
以前のバージョンより多くのプログラミング言語を使用して、Visual Studio でアプリを作成することができ、ソリューションおよびプロジェクトが必要なくなりました。 コードは、構文の色設定、基本的なステートメント入力候補を取得します。場合によっては、[移動] やその他のサポートを取得することもあります。 お気に入りの言語がサポートされていない場合、TextMate の文法を使用して、その言語のサポートを作成できます。

### <a name="visual-c"></a>Visual C++
Visual Studio 2017 RC には、Visual C++ 環境に対する多くの更新プログラムと修正プログラムが導入されています。 250 以上のバグを修正し、コンパイラおよびツールの問題をレポートしてきました。その多くは [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect") を通じてお客様から寄せられたものです。

また、Visual Studio での C++ Core ガイドラインの配信、C++11 および C++ 機能の拡張サポートを追加することによるコンパイラの更新、C++ ライブラリへの機能の追加および更新、C++ IDE のパフォーマンス、インストールのワークロードなどの改善を含めるために、いくつかの改善も行っています。

詳細については、[Visual 2017 RC での Visual C++ の新機能](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)に関するページを参照してください。  


### <a name="debugging-and-diagnostics"></a>デバッグと診断
デバッグが高速化され、編集時に遅延を引き起こすことがなくなりました。

例: Visual Studio の以前のバージョンでは、 WPF のホスティング プロセス、Windows フォーム、および管理コンソールのプロジェクトなどを導入して、次のデバッグ セッションで使用するバックグラウンドのプロセスをスピンアップしることにより、デバッグを高速化していました。 この機能は意図は適切でしたが、デバッグを停止したとき、またはデバッグ セッションが終了した後に Visual Studio を使用した場合、Visual Studio を数秒間、一時的に応答させなくしていました。

Visual Studio 2017 では、ホスティング プロセスと最適化されたデバッグをオフにしました。そのため、ホスティング プロセスがない場合と同様に速く、ホスティング プロセス (ASP.NET、ユニバーサル Windows、C++ プロジェクトなど) を使用していないプロジェクトではさらに速くなっています。

#### <a name="run-to-click"></a>クリックで実行
デバッグ時にコード行の隣にあるアイコンをクリックすると、その行を実行できるようになりました。 目的の行でのコードの実行や停止のため、一時的なブレークポイントを設定したり、複数の手順を実行したりする必要がなくなりました。

![Visual Studio 2017 RC のデバッグ - クリックで実行](../ide/media/vs2017ide-RunToClick.png "Run To Click in Visual Studio 2017 debug & diagnostics")

#### <a name="the-new-exception-helper"></a>新しい例外ヘルパー

新しい例外ヘルパーを使用して、内部例外にすぐにアクセスできるコンパクトな非モーダル ダイアログに例外情報を表示できます。

NullReferenceException を診断するときに、例外ヘルパー内の null をすばやく確認します。

また、特定のモジュールからスローされた例外の種類の中断も除外できるようになりました。スローされた例外での中断時に条件を追加するチェックボックスをオンにします。

![新しい例外ヘルパー ダイアログ](../ide/media/vs2017ide-ExceptionHelper.png "The New Exception Helper dialog")

詳細については、「[Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/)」 (Visual Studio で新しい例外ヘルパーを使用する) のブログの投稿を参照してください。

## <a name="talk-to-us"></a>ご意見  
 Visual Studio チームにフィードバックを送ることにどんな意味があるのでしょうか? お客様からのフィードバックは、すべて真剣に考慮することにしています。 フィードバックによって今後の動向が左右されることになります。  

Visual Studio を向上させることができる提案がある場合、または問題を報告する場合、詳しくは「[ご意見](../ide/talk-to-us.md)」ページを参照してください。  

### <a name="report-a-problem"></a>問題を報告する  
 メッセージは、発生した問題の影響をすべて表せていない場合があります。 ハング、クラッシュ、またはその他のパフォーマンスの問題が発生した場合、**[問題の報告]** ツールを使用すると、再現コードやサポート ファイル (スクリーン ショット、トレース ファイル、ヒープ ダンプ ファイルなど) を簡単に Microsoft と共有することができます。 このツールの使用方法については、[問題を報告する方法](how-to-report-a-problem-with-visual-studio-2017.md)に関するページを参照してください。  

### <a name="track-your-issue-in-connect"></a>問題点を Connect で追跡する  
 Visual Studio に関するフィードバックの状況を追跡するには、[Connect](http://connect.microsoft.com/) にアクセスしてバグ報告をしてください。 報告したら、Connect に戻って、その状態を追跡することができます。  

## <a name="see-also"></a>関連項目  
* [Visual C++ の新機能](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [C# の新機能](https://docs.microsoft.com/en-us/dotnet/articles/csharp/csharp-7)  
* [Team Foundation Server の新機能](https://www.visualstudio.com/en-us/docs/whats-new)
* [Visual Studio のリリース ノート](https://www.visualstudio.com/news/vs2015-vs)



<!--HONumber=Feb17_HO4-->


