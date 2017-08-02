---
title: "Visual Studio 2017 の新機能 | Microsoft Docs"
ms.custom: 
ms.date: 04/06/2017
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 8bf0b097be929b30627e0f1139c6e0b145933ab4
ms.openlocfilehash: 28c6a166a423b3341ae32676830861eaa78cb40d
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# <a name="what39s-new-in-visual-studio-2017"></a>Visual Studio 2017 の新機能
すべての開発、すべてのアプリ、すべてのプラットフォームにおいて、他に類を見ない生産性を実現します。 Visual Studio 2017 を利用し、Android、iOS、Windows、Linux、Web、クラウド向けのアプリを開発します。 短期間でプログラミングできて、デバッグや診断も簡単に行えます。テストを頻繁に行うことで、自信をもってリリースできます。 独自の拡張機能を開発することで Visual Studio を拡張し、カスタマイズすることもできます。 今回の新しいリリースでは、バージョン管理を使用した、迅速で、効率的な共同作業が可能になりました。

> [!NOTE]
> Visual Studio 2017 の新機能の一覧については、「[リリース ノート](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes)」をご覧ください。

変更を行った基本的な概要は、次のとおりです。

* **パフォーマンスと生産性**。 最新のモバイル、クラウド、デスクトップの開発機能だけでなく、全体的な取得、パフォーマンス、開発者の生産性エクスペリエンス全般を改善しました。 Visual Studio の起動が以前と比較してより高速になり、より応答性が向上し、メモリーの消費量が少なくなりました。
* **基本の再定義**。 新しいセットアップ エクスペリエンスにより、必要なものを必要なタイミングでより短い時間でインストールできるようになりました。 大規模なソリューションやプロジェクトの読み込む場合でも、複数のフォルダーや単一のファイルのコードを操作する場合でも、Visual Studio の起動がより高速になりました。 さらに Visual Studio は、特に DevOps を大事にするチームにとって、全体像を把握するのに役立ちます。
* **Azure によるクラウド アプリの開発**。 Microsoft Azure を使用するクラウド ファーストのアプリを簡単に作成できる Azure ツールのビルトイン スイート。 Visual Studio を使用すれば、Azure でアプリとサービスを構成、ビルド、デバッグ、パッケージ化、デプロイするのが容易になります。
* **モバイル アプリの開発**。 Visual Studio 2017 では Xamarin が導入されています。これにより、1 つのコア コードベースとスキル セットを使用することでマルチプラットフォームのモバイル要件が統合され、短期間で成果を出すことができます。 既存のチーム、テクノロジへの投資、C# コードをモバイル対応にして、コンシューマー グレードのエクスペリエンスを予定より早くかつ予算以内で提供します。 モバイル ライフサイクルのすべてのステップを加速させ、ワールドクラスのコンシューマー エクスペリエンスまたは従業員の生産性向上を支援するアプリのポートフォリオを提供します。

ここからは、最も注目に値する変更点の一部について詳しく説明します。

## <a name="performance-improvements"></a>パフォーマンスの向上

### <a name="a-new-setup-experience"></a>新しいセットアップ エクスペリエンス  
[Visual Studio 2017 をダウンロードする](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)または [Visual Studio のシステム要件を確認する](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 Visual Studio により、必要な機能だけを必要なタイミングでより簡単により短い時間でインストールできます。 また、アンインストールも正常に行われます。

 Visual Studio をインストールするときに確認できる最も重要な変更は、新しいセットアップ エクスペリエンスです。 **[ワークロード]** タブには、共通のフレームワーク、言語、プラットフォーム別にグループ化されたインストール オプションが表示されます。 .NET デスクトップ開発から Windows、Linux、iOS での C++ アプリケーション開発まで、すべてを網羅します。   

 ![Visual Studio 2017 のセットアップ ダイアログ](~/docs/install/media/vs2017-workloads.PNG "Visual Studio 2017 のセットアップ画面")

必要なワークロードを選択し、必要に応じてそれらを変更します。

ワークロードを使用する代わりに、独自のコンポーネントを選択するには、 インストーラーから **[個別のコンポーネント]** タブを選択するだけです。 また、Windows の言語オプションを変更することなく、言語パックをインストールする場合は、 インストーラーの **[言語パック]** タブを選択します。  

ステップ バイ ステップの手順を含む、新しいインストール エクスペリエンスについて詳しくは、マイクロソフトの [Visual Studio のインストール](../install/install-visual-studio.md)に関するページをご覧ください。

### <a name="start-visual-studio-faster"></a>Visual Studio の起動の高速化
Visual Studio の新しいパフォーマンス センターは、IDE の起動時間を最適化するのに役立ちます。 パフォーマンス センターでは、IDE の起動を遅くしている可能性のある拡張機能やツール ウィンドウをすべて一覧表示します。 拡張機能を起動するタイミングや、ツール ウィンドウを起動時に開くかどうかを指定して、起動時のパフォーマンスを向上させるために使用することができます。

### <a name="decrease-solution-load-time"></a>ソリューションの読み込み時間の短縮
ソリューションに多数のプロジェクトが含まれていても、一度にすべてのファイルやプロジェクトを操作する必要があるとは限りません。 ここでは、Visual Studio がすべてのプロジェクトを読み込むのを待たずに、編集やデバッグを行えるようになりました。 マネージ プロジェクトでこれを試すには、[ツール]、[オプション]、[プロジェクトおよびソリューション] の順に選択して、**[Lightweight Solution load]** (ライトウェイト ソリューション ロード) をオンにします。

  ![Visual Studio 2017 の [オプション] ダイアログ ボックス](~/docs/ide/media/vs2017ide-LightweightSolutionLoad.PNG "Visual Studio 2017 - [オプション] ダイアログ ボックス - ライトウェイト ソリューション ロード")

### <a name="faster-on-demand-loading-of-extensions"></a>拡張機能のオンデマンド読み込みの高速化
Visual Studio では、独自およびサードパーティの拡張機能が IDE の起動時ではなく必要に応じて読み込まれるように取り組みを進めています。 どの拡張機能が起動、ソリューションの読み込み、および入力パフォーマンスに影響があるかについて関心をお持ちですか? この情報については、[ヘルプ]、[Visual Studio のパフォーマンスの管理] の順に選択して確認することができます。

  ![Visual Studio 2017 の [オプション] ダイアログ ボックス](~/docs/ide/media/vs2017ide-manage-vs-perf.png "Visual Studio 2017 の [ヘルプ] ダイアログ ボックス - パフォーマンス管理")

## <a name="productivity-improvements"></a>生産性の向上

### <a name="sign-in-across-multiple-accounts"></a>複数のアカウント間のサインイン  
チーム エクスプローラー、Azure Tools、Windows ストアでの発行で使用するユーザー アカウントを共有できるように、Visual Studio で新しい ID サービスを導入しました。

また、より長い時間サインインしたままにできます。 Visual Studio に 12 時間ごとにサインインを求められることはなくなりました。 詳細については、「[Fewer Visual Studio Sign-in Prompts](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/)」 (Visual Studio のサインインの確認メッセージを減らす) のブログの投稿を参照してください。

### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>[拡張機能マネージャーのローミング] で拡張機能を管理する
Visual Studio にサインインすると、お気に入りの拡張機能を使用して、各開発環境を容易に設定できるようになりました。 新しい [拡張機能マネージャーのローミング] は、クラウドに同期されたリストを作成することで、お気に入りの拡張機能をすべて追跡します。  

Visual Studio の拡張機能の一覧を表示するには、[ツール]、[拡張機能と更新プログラム] の順にクリックし、[拡張機能マネージャーのローミング] をクリックします。

![Visual Studio 2017 - [拡張機能と更新プログラム] ダイアログ](~/docs/ide/media/vs2017ide-extensions-and-updates.png "Visual Studio 2017 - Tools > Extensions and Updates dialog")

[拡張機能マネージャーのローミング] では、インストールするすべての拡張機能を追跡しますが、どの拡張機能をローミング リストに追加するかを選択することができます。

![Visual Studio 2017 - [拡張機能と更新プログラム] ダイアログ](~/docs/ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 - Roaming Extension Manager")

[拡張機能マネージャーのローミング] を使用する場合、リストに次の 3 つの種類のアイコンが表示されます。
* ![ローミング済みアイコン](~/docs/ide/media/vs2017ide-roamedicon.png "ローミング済みアイコン") "***ローミング済み***": ローミング リストにあり、このコンピューターにはインストールされていない拡張機能を示します。
  (これらの拡張機能は、**[ダウンロード]** ボタンでインストールできます。)
* ![ローミングおよびインストール済みアイコン](~/docs/ide/media/vs2017ide-roamedinstalledicon.png "ローミングおよびインストール済みアイコン") "***ローミングおよびインストール済み***": ローミング リストにあり、お使いの開発環境にインストールされているすべての拡張機能を示します。
  (ローミングしない場合は、**[ローミングの停止]** ボタンで削除することができます。)
* ![インストール済みアイコン](~/docs/ide/media/vs2017ide-installedicon.png "インストール済みアイコン") "***インストール済み***": この環境にインストールされ、ローミング リストにはないすべての拡張機能を示します。
  (**[ローミングの開始]** ボタンを使用して、拡張機能をローミング リストに追加できます。)

サインイン中にダウンロードした拡張機能は、**ローミングおよびインストール済み**としてリストに追加され、ローミング リストに表示されます。これにより、どのコンピューターからでもアクセスできるようになります。

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>ライブ アーキテクチャの依存関係検証とライブ単体テストのエクスペリエンス

Visual Studio は依存関係検証ダイアグラム (別名レイヤー ダイアグラム) を使用することで、コード エディターにコードを入力して、リアルタイムでアーキテクチャの依存関係ルールの違反を 確認できるようになりました。

エラーは [エラー一覧] に表示され、テキスト エディターでは波線でこの違反の正確な場所が示されます。 これにより、不要な依存関係を導入する可能性を低減できます。

![ライブ アーキテクチャの検証](~/docs/ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "Live Architecture Dependency validation")

#### <a name="live-unit-testing"></a>ライブ単体テスト

Visual Studio Enterprise 2017 では、ライブ単体テストを実行することで、コーディング中にエディターで単体テストの結果とコード カバレッジをライブで確認できます。 これは .NET Framework の C# プロジェクトと Visual Basic プロジェクトで機能し、MSTest、xUnit、および NUnit の 3 つのテスト フレームワークをサポートします。

![ライブ単体テスト](~/docs/ide/media/lut-codewindow.png "Visual Studio の Enterprise エディションの新しいライブ単体テスト機能の例")

詳しくは、ブログの投稿「[Live Unit Testing in Visual Studio 2017 Enterprise](https://blogs.msdn.microsoft.com/visualstudio/2017/03/09/live-unit-testing-in-visual-studio-2017-enterprise/)」(Visual Studio 2017 Enterprise でのライブ単体テスト) をご覧ください。

### <a name="devops"></a>DevOps
#### <a name="redgate-data-tools"></a>Redgate Data Tools:
DevOps 機能を SQL Server データベース開発に拡張するために、Visual Studio 2017 の次のエディションで Redgate Data Tools が利用できるようになりました。

Visual Studio 2017 Enterprise に付属:
- [Redgate ReadyRoll Core](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) は、移行スクリプトの開発、ソース管理によるデータベースの変更管理、アプリケーション変更と並行した SQL Server データベース変更の配置の安全な自動化に役立ちます。
- [Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) を利用すると、インテリジェントなコード入力候補機能により、SQL を短時間で正確に記述できます。 SQL Prompt は、データベース、システム オブジェクト、キーワードをオートコンプリートし、入力と同時に列の入力候補を提案します。 列の名前やエイリアスを覚える必要がないため、結果として、間違いが少なく、読みやすいコードが完成します。

Visual Studio 2017 のすべてのエディションに付属:
- [Redgate SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) では、複数のデータベースから SQL のフラグメントやオブジェクトをすばやく見つけることができ、生産性が向上します。

詳しくは、ブログの投稿「[Visual Studio 2017 Redgate Data Tools](https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/redgate-data-tools-in-visual-studio-2017/)」をご覧ください。

### <a name="visual-studio-ide-enhancements"></a>Visual Studio IDE の拡張機能
#### <a name="interact-with-git"></a>Git との連携
Visual Studio でプロジェクトを操作する際に、コードを迅速にセットアップしてコミットし、Git サービスにコードを公開できます。 また、IDE の右下隅のボタンからメニュー クリックを使用して、Git リポジトリを管理することもできます。

![Visual Studio 2017 と Git ダイアログのやり取り](~/docs/ide/media/vsIDE-GitInteraction.png "Visual Studio IDE の Git ツール")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>構造ビジュアライザーを使用したコードの表示と移動
構造ビジュアライザーは、構造のガイド線 (別名 インデント ガイド) をコードに描きます。 これらを使用することで、スクロールすることなく現在作業しているコード ブロックを視覚化して検出できます。 行にカーソルを置くとツールチップが表示され、そのブロックの開始地点とその親を確認できます。 TextMate 文法を介してサポートされるすべての言語のほか、C#、Visual Basic、XAML で使用できます。

![Visual Studio 2017 の構造ビジュアライザー](~/docs/ide/media/vsIDE-StructureVisualizer.png "Visual Studio の構造体ビジュアライザー")

#### <a name="experience-improved-navigation-controls"></a>エクスペリエンスが改善されたナビゲーション コントロール:
より確実に混乱なく A から B に移動できるようにナビゲーション エクスペリエンスを更新しました。

* **ジャンプ** (Ctrl + F12) &ndash; 任意の基本データ型やメンバーから各種実装に移動します。

* **すべてにジャンプ** (Ctrl + T または Ctrl + ,) &ndash; 任意のファイル/型/メンバー/シンボル宣言に直接移動します。 結果の一覧をフィルターしたり、クエリ構文 (例: ファイルは “f searchTerm”、型は “t searchTerm” など) を使用したりできます。

 ![[すべてにジャンプ] の機能強化](~/docs/ide/media/vs2017ide-navigation-go-to.png "強化された [すべてにジャンプ] 機能")

* **すべての参照の検索 (Shift+F12)** &ndash; 構文の色づけにより、[すべての参照の検索] の結果をプロジェクト、定義、パスの組み合わせでグループ化できます。 また、結果を "ロック" して元の結果を失うことなく別の参照を検索できます。

 ![新しい [すべての参照の検索] ツール](~/docs/ide/media/vs2017ide-find-all-references.png "新しい [すべての参照の検索] ツールの例")

* **インデント ガイド** &ndash; 灰色の縦の点線がコード内のランドマークとしての役割を果たし、ビューのフレーム内のコンテキストを提供します。 これらはおすすめの Productivity Power Tools で認識できます。

新しい生産性向上機能について詳しくは、[Visual Studio 2017 での生産性向上](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/productivity-in-visual-studio-2017-rc/)に関する Mark Wilson-Thomas のブログ投稿をご覧ください。

### <a name="visual-c"></a>Visual C++
Visual Studio には、C++ Core ガイドラインの配信、C++11 および C++ 機能の拡張サポートを追加することによるコンパイラの更新、C++ ライブラリへの機能の追加および更新など、いくつかの改善が加えられています。 また、C++ IDE やインストールのワークロードなどのパフォーマンスも改善しました。

同時に 250 以上のバグを修正し、コンパイラおよびツールの問題をレポートしてきました。その多くは [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect") を通じてお客様から寄せられたものです。

詳しくは、[Visual 2017 での Visual C++ の新機能](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)に関するページをご覧ください。  

### <a name="debugging-and-diagnostics"></a>デバッグと診断

#### <a name="run-to-click"></a>クリックで実行

デバッグ中に必要な行に止まるためにブレークポイントを設定することなく、簡単に前方にスキップできるようになりました。 デバッガーが停止した場合は、カーソルを合わせているコード行の横に表示されるアイコンをクリックします。 次にコード パスでその地点に到達すると、その行でコードが実行されて停止します。

![Visual Studio 2017 のデバッグ - クリックで実行](~/docs/ide/media/vs2017ide-RunToClick.png "Visual Studio 2017 のデバッグと診断のクリックで実行")

#### <a name="the-new-exception-helper"></a>新しい例外ヘルパー

新しい例外ヘルパーを使用すると、例外情報を一目で確認できます。 情報はコンパクトな形式で表示され、内部の例外に簡単にアクセスできます。 NullReferenceException を診断するときに、例外ヘルパー内の null をすばやく確認できます。

![新しい例外ヘルパー ダイアログ](~/docs/ide/media/vs2017ide-ExceptionHelper.png "新しい例外ヘルパー ダイアログ")

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
* [C# の新機能](https://docs.microsoft.com/en-us/dotnet/csharp/csharp-7)  
* [Team Foundation Server の新機能](https://www.visualstudio.com/en-us/docs/whats-new)
* [Visual Studio のリリース ノート](https://www.visualstudio.com/news/vs2015-vs)

