---
title: R Tools for Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: hero-article
ms.assetid: 11324501-ceb6-47a2-ae13-e9e992d3603e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 80a10c710aac8413bd59b53bb61de7a982c09952
ms.contentlocale: ja-jp
ms.lasthandoff: 07/12/2017

---

# Visual Studio での R の使用
<a id="working-with-r-in-visual-studio" class="xliff"></a>

R は、高い拡張性を備えた、統計コンピューティングおよびグラフィックス用の言語であり環境です。 R は GNU General Public License に基づき無料配布されており、コミュニティの強力なサポートを受けることができます。また、数学記号と式を含むプロットを出版品質で生成できる機能で知られています。 R の詳細については、[r-project.org](https://www.r-project.org/about.html) と「[An Introduction to R (R の概要)](https://cran.r-project.org/doc/manuals/r-release/R-intro.html)」をご覧ください。

R Tools for Visual Studio (RTVS) は Visual Studio 2017 と Visual Studio 2015 Update 3 以降向けの無料の[オープンソース](https://github.com/microsoft/RTVS)拡張機能であり、MIT ライセンスに基づいてリリースされています (R インタープリターのバイナリとリンクする [RHost](https://github.com/microsoft/R-Host) という名前の 2 番目のオープン ソース コンポーネントは、GNU Public License V2 に基づいてリリースされています)。

Visual Studio で R を使用するには、次の手順を実行します。

- [R Tools をインストールします](installation.md)。
- [作業の開始](getting-started-with-r.md)ガイド、および[サンプル](getting-started-samples.md)や[ヘルプ情報の入手方法](getting-started-help.md)に関するトピックをご覧ください。

次に、以下のリンクから、R 関連の機能と Visual Studio 自体の一般的な機能の詳細を確認してください。

| 機能 | 説明 | Visual Studio の一般的なドキュメント | 
| --- | --- | --- |
| [Visual Studio のプロジェクト システム](projects.md) | 関連ファイルを使いやすい構造で整理および管理し、R コード、R ドキュメント、R Markdown、SQL クエリ、ストアド プロシージャなどのアイテムに関する便利なテンプレートを活用できます。 [パッケージ マネージャー](package-manager.md)や [SQL Server integration](sql-server.md) も使用できます。  | [Visual Studio のソリューションおよびプロジェクト](../ide/solutions-and-projects-in-visual-studio.md) |
| [ワークスペース](workspaces.md) | RTVS は、ローカル ワークスペースとリモート ワークスペースへバインド可能です。これにより、ローカルで小規模なデータ セットを使用して R コードを開発してから、クラウドベースのより強力なコンピューター上で大規模なデータ セットを使用して簡単にコードを実行することができます。 | 適用なし |
| [R Tools オプション](options.md) | RTVS のさまざまな側面を制御します。 | [[オプション] ダイアログ ボックス](../ide/reference/options-dialog-box-visual-studio.md) |
| [豊富な編集、IntelliSense、コード スニペット](code-editing.md) | 構文の色分け、すべてのコードとライブラリ間での [IntelliSense](code-intellisense.md)、コードのフォーマット、シグネチャ ヘルプ、定義への移動、すべての参照の検索、[コード スニペット](code-snippets.md)などが含まれます。 | [コード エディターとテキスト エディターでのコードの作成](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown.md) | R Markdown ドキュメントを使用すると、マークダウン コード ブロック内の統合された R コードを用いてデータの結果を共有できます。 | 適用なし |
| [対話型ウィンドウ](interactive-repl.md) | R で完全な REPL エクスペリエンスを実現でき、対話型ウィンドウでソース ファイルのコードを簡単に実行可能です。 | 適用なし |
| [データの視覚化](visualizing-data.md) | プロットは R を使用する上で不可欠な部分であるため、RTVS では独立した複数のプロット ウィンドウを利用できます。各ウィンドウには、履歴とウィンドウ間のプロットの移動機能が備わっています。 プロットはビットマップ ファイルと PDF ファイルに保存でき、またビットマップやメタファイルとしてクリップボードにコピーすることもできます。  | 適用なし |
| [Variable Explorer](variable-explorer.md) | 並べ替え可能なテーブルを表示する機能と CSV へのエクスポート機能を備えており、グローバル スコープ内やパッケージ固有のスコープ内の変数を調査できます。 | 適用なし |
| [フル機能のデバッグ](debugging.md) | 対話型ウィンドウとの統合などがあります。 | [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md) |

次のビデオでも、R Tools の各機能の簡単なレビュー (5 分 48 秒) を確認できます。

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## よく寄せられる質問
<a id="frequently-asked-questions" class="xliff"></a>

**Q.RTVS は Visual Studio Express Edition で動作しますか?**

A:  いいえ。

**Q.RTVS で使用可能な R インタープリターにはどのようなものがありますか?**

A:  [CRAN R](https://cran.r-project.org/)、[Microsoft R Client、Microsoft R Server](https://msdn.microsoft.com/microsoft-r/) が使用可能です。

**Q.これらのインタープリターはどこでダウンロードできますか?**

A:  [インストール](installation.md)に関する記事をご覧ください。

**Q.RTVS で Visual Studio の拡張機能を使用できますか?**

A:  もちろん、できます。 以下に R を使用するユーザーに人気の拡張機能を示しますが、これらはごく一部です。

- [VsVim で Vim のキー バインド](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [Github](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Markdown editor によるライブ プレビュー](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

詳細については、[Visual Studio Marketplace](https://marketplace.visualstudio.com/) をご覧ください。

**Q.RTVS を Visual Studio 内にインストールするのですから、R を C# や C++ などの Microsoft 言語と合わせて簡単に使用できますか?**

A:  いいえ。 RTVS は R コードの開発ツールであり、R の標準的なネイティブ インタープリターを使用します。 R と他の言語との相互運用はサポートされていません。

**Q.RStudio に用意されている機能 X がありません。**

A:  RStudio は完成度の高いすばらしい R 用の IDE であり、長年にわたり開発されています。 作業を適切に行う上で重要な機能すべてを RTVS に搭載するように開発を進めています。 今後行う作業の優先順序を決めるために、[RTVS アンケート](https://www.surveymonkey.com/r/RTVS1)にご協力ください。

**Q.RTVS は OS X または Linux で動作しますか?**

A:  いいえ。RTVS は Visual Studio で動作するように設計されているため、Windows 限定の実装になります。 ただし、Microsoft では、人気の高い Microsoft のクロスプラットフォーム エディターである [Visual Studio Code](https://code.visualstudio.com/) をベースにした新しいツール セットの構築について検討しています。

**Q.RTVS に貢献できますか?**

A:  もちろん、できます。 ソース コードは [Github](https://github.com/microsoft/RTVS) で公開されています。 問題の追跡ツールを使用して、すでに存在するファイルに対するバグ情報とコメントをお寄せください。

このドキュメントに対する投稿も歓迎しています。&mdash;ページの右上の **[編集]** を選択してください。 また、ページの最下部から、ドキュメントに対するコメントもお寄せください。

**Q.RTVS ではソース管理システムを利用できますか?**

A:  はい。Visual Studio に統合されている任意のソース管理システムを使用できます。

**Q.RTVS は英語以外のロケールで機能しますか?**

A:  RTVS の 1.0 リリースは英語版のみです。 1.1 リリースでは、Visual Studio と同じ言語セットにローカライズされる予定です。 それまでは、[Visual Studio 2015 用の英語の言語パック](https://www.microsoft.com/download/details.aspx?id=48157)を使用するか、Visual Studio 2017 でインストーラーを実行し、**[言語パック]** タブで [英語] を選択してください。

![Visual Studio 2017 の各国対応設定](media/FAQ-international-settings.png)

**Q.RTVS で R の 32 ビット エディションを使用できますか?**

A:  いいえ。RTVS では、Windows の 64 ビット エディションで動作する R の 64 ビット エディションのみがサポートされます。

**Q.現在の Visual Studio の設定を本当に気に入っていますが、新しいデータ サイエンスの設定も試してみたいです。どうしたらいいのでしょうか?**

A:  **[ツール] > [設定のインポートとエクスポート...]** を使用して現在の Visual Studio 設定を保存し、次にデータ サイエンスの設定に切り替えます。 保存した設定を復元するには、**[設定のインポートとエクスポート...]** コマンドを再度使用します。

**Q.RTVS プロジェクトで推奨される `.gitignore` の設定はどのようなものですか?**

A:  Github に、`.gitignore` の推奨ファイルのマスター リポジトリが用意されています。 [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore) をご覧ください。

**Q.ネットワーク共有上で Visual Studio プロジェクトを保存できますか?**

A:  いいえ。Visual Studio では、ネットワーク共有からのプロジェクトの読み込みをサポートしていません。

## フィードバックをお寄せください。
<a id="send-us-your-feedback" class="xliff"></a>

1. **Github の問題**: RTVS チームへ問い合わせる場合は、[GitHub 上で問題を報告する](https://github.com/Microsoft/RTVS/issues)か、**[R Tools] > [フィードバック]** メニューを使用して行ってください。

1. **気に入った機能の報告や問題点、改善点の報告**: **[R Tools] > [フィードバック]** メニューから、フィードバックの送信と、問題の診断に役立つ RTVS ログ ファイルの添付を素早く行えます (ログは、個別に送信できるように `%temp%/RTVSlogs.zip` に書き込まれています)。**[ヘルプ] > [フィードバック] > [設定]** メニュー コマンドから、またはインストール中に [Visual Studio telemetry]\(Visual Studio テレメトリ\) をオフにした場合は、ログ機能が無効になります。

1. **電子メール**: チーム (*rtvsuserfeedback (at) microsoft.com*) 宛にフィードバックを直接送信できます。

