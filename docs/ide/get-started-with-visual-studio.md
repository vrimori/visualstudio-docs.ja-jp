---
redirect_url: /visualstudio/ide/visual-studio-ide
ms.openlocfilehash: 5f1fa39d6e6cde1664a8aaa34aed7cba726b1d56
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="get-started-with-visual-studio"></a>Visual Studio 入門
Visual Studio は高性能のアプリ開発ツールです。 [Visual Studio](https://www.visualstudio.com/vs/) をまだインストールしていないのであれば、今すぐダウンロードし、インストールしてください。 Visual Studio をダウンロードし、設定する方法については、「[Getting Started with Visual Studio – Setting up your IDE](https://www.youtube.com/watch?v=xLCedknQkN0&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=1)」 (Visual Studio 入門 – IDE のセットアップ) という動画をご覧ください。

## <a name="visual-studio-tour"></a>Visual Studio ツアー
Visual Studio には、一連のツール ウィンドウ、メニュー、ツール バーがあります。これらはまとめて IDE (Integrated Development Environment/統合開発環境) と呼ばれています。 Visual Studio IDE は、開発作業を支援します。 頻繁に利用する IDE アイテムには次のようなものがあります。

### <a name="code-editor"></a>コード エディター
これは Visual Studio で最も頻繁に使用されるツール ウィンドウの 1 つです。このエディターで、コードを記述し、表示し、コード内を移動します。

![コード エディター](../ide/media/VSIDE_CodeWindow.png)

コード エディターには、ステートメント入力候補、構文色付け、マップ モードなど、コードを簡単に記述したり、検索したりするための便利な機能があります。 詳細については、「[Getting Started with Visual Studio - Editing and navigating your code](https://www.youtube.com/watch?v=4glwwioCVjA&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=5)」 (Visual Studio 入門 - コードの編集と移動) という動画をご覧ください。

ソリューションの種類には、*フォーム*と呼ばれるウィンドウ (Windows Presentation Foundation (WPF) フォーム、Windows フォーム、Extensible Application Markup Language (XAML) フォームなど) などがあります。 その場合、この領域にはビジュアル デザイナーも表示されます。このデザイナーでは、アプリの実行時にボタンやリスト ボックスなどのコントロールを、ユーザーが操作するフォームにドロップ アンド ドロップできます。

### <a name="solution-explorer"></a>ソリューション エクスプローラー
**ソリューション エクスプローラー**というツール ウィンドウには、コード ファイルが一覧表示されます。 ソリューション エクスプローラーを利用すれば、ファイルをソリューションやプロジェクトにまとめ、コードを整理できます。 太字のプロジェクトは*スタートアップ プロジェクト*と呼ばれています。 これは、ソリューションの開始時に実行される最初のコードです。 スタートアップ プロジェクトは変更できます。 詳細については、「[Getting Started with Visual Studio - Building blocks of the IDE](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK)」 (Visual Studio 入門 - IDE の構成要素) という動画をご覧ください。

![ソリューション エクスプローラーの折りたたまれているノード](../ide/media/VSIDE_SolutionExplorer2_callouts.png)

 ソリューションとプロジェクト以外に、ソリューション エクスプローラーには、プロジェクトのノードを展開したとき、各プロジェクトの全ファイルが一覧表示されます。 各プロジェクトには、1 つまたは複数のファイルが含まれています。ソース コード ファイルやリソース ファイル (画像やライブラリなど) などです。

![ソリューション エクスプローラー](../ide/media/VSIDE_SolutionExplorer3.png)

ソリューション、プロジェクト、ファイルのプロパティを見るには、ショートカット (右クリック) メニューで**プロパティ** コマンドを選択するか、メニューで **[表示]、[プロパティ] ウィンドウ**の順に選択します。

![[プロパティ] ウィンドウ](../ide/media/VSIDE_SolutionExplorer4.png)

ただし、ソリューションやプロジェクトを作成しなくてもコード記述を開始できます。 Visual Studio のコード ファイルを直接開いてください。Git リポジトリから複製されたファイルなどをすぐに編集できます。 ファイルはソリューション エクスプローラーに表示され、従来のエクスプローラーと同様に、構文色付けや基本的なステートメント入力候補などの機能が与えられます。 詳しくは、「[プロジェクトまたはソリューションを使用せずに Visual Studio でコードを開発する](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)」をご覧ください。

### <a name="toolbar-and-menus"></a>ツール バーとメニュー
プロジェクトを実行するには、新しいソリューションを作成し、ファイルを保存し、さらに Visual Studio のツール バーやメニュー コマンドを利用します。 たとえば、コードを実行してデバッグする準備ができたら、ツール バーの **[開始]** ボタンを選択するか、メニューで **[デバッグ]、[デバッグの開始]** の順に選択します。 新しいソリューションを作成するには、**[新しいプロジェクト]** ボタンを選択するか、メニューで **[ファイル]、[新しいプロジェクト]** の順に選択します。同様の操作が他にもあります。

![Visual Studio ツール バー](../ide/media/VSIDE_SolutionExplorer5_callouts.png)

ツール バー アイコンとメニュー コマンドはコンテキスト、つまり、現在選択されている項目によって変わります。 ほぼすべてのコマンドに、キーボード コマンドを使用して、またマウスを使用してアクセスできます。

### <a name="team-explorer"></a>チーム エクスプローラー
**チーム エクスプローラー**では、[Git](https://git-scm.com/) や [Team Foundation バージョン管理 (TFVC)](https://www.visualstudio.com/en-us/docs/tfvc/overview) など、ソース コントロール ツールに接続し、コードをローカル保存したり、ホストされるサービスで他のユーザーと共有したりできます。 作業の追跡記録などもできます。

詳細については、「[Getting Started with Visual Studio – Building blocks of the IDE](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK)」 (Visual Studio 入門 - IDE の構成要素) と「[Getting Started with Visual Studio – Opening a project from Source Control](https://www.youtube.com/watch?v=pc9vX_4RGV4&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=3)」 (Visual Studio 入門 - ソース コントロールからプロジェクトを開く) という動画をご覧ください。

![チーム エクスプローラー](../ide/media/TeamExplorer.png)

### <a name="output-window"></a>[出力] ウィンドウ
**[出力]** ウィンドウには、デバッグ メッセージ、エラー メッセージ、コンパイラの警告、公開状態メッセージなど、Visual Studio の通知が出力されます。 メッセージの種類ごとに独自のタブがあります。

![[出力] ウィンドウ](../ide/media/VSIDE_OutputWindow.png)

[出力] ウィンドウのデバッグの使用方法については、「[The Output window while debugging with Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2015/02/09/the-output-window-while-debugging-with-visual-studio/)」 (Visual Studio でデバッグするときの出力ウィンドウ) を参照してください。

## <a name="first-steps"></a>最初の手順
- **全体像の把握** - Visual Studio の数多くの主要な機能の概要について、ツアーをご覧ください。 [Visual Studio IDE 機能ツアー](../ide/visual-studio-ide.md)を見る。
- **セットアップ** - Visual Studio をダウンロードしてインストールする方法については、「[Visual Studio 2017 のインストール](../install/install-visual-studio.md)」を参照してください。
- **基本** - Visual Studio のしくみについては、「[Get Started Developing with Visual Studio](../ide/get-started-developing-with-visual-studio.md)」 (Visual Studio で開発を始める) を参照してください。
- **設定** - Visual Studio の動作をお好みに合わせてカスタマイズする方法をご覧ください。 「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。
- **チュートリアル** - Visual Studio でコードを開発する方法については、「[Visual C# と Visual Basic の概要](../ide/getting-started-with-visual-csharp-and-visual-basic.md)」や「[Visual Studio 内の C++ の概要](../ide/getting-started-with-cpp-in-visual-studio.md)」などのチュートリアルをご覧ください。
- **動画** - Visual Studio の他の機能や側面については、YouTube の [Microsoft Visual Studio チャネル](https://www.youtube.com/user/VisualStudio/videos)の動画、[Channel 9](https://channel9.msdn.com/Tags/visual+studio) の Visual Studio 動画、または [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!jobf=Developer) をご覧ください。

## <a name="access-cloud-based-resources"></a>クラウドベース リソースにアクセスする
アプリやゲームでクラウドベースのリソースを使用する場合、[Azure サービス](https://azure.microsoft.com/en-us/services/)を追加します。 新しい Visual Studio インストーラーを利用して **Azure 開発**ワークロードをインストールすると、Azure SDK for .NET がインストールされます。 インストールされるパッケージは、SDK の 2.9.5 バージョンと同じ機能レベルです。 このバージョンと将来のすべてのバージョンの Visual Studio では、Azure SDK for .NET は Visual Studio インストーラーからのみ取得できます。

Azure 開発ワークロードをインストールすると、**Cloud Explorer** という名前の新しいツール ウィンドウを Visual Studio で利用できるようになります。 Cloud Explorer を利用すると、Visual Studio 内から Azure のアセットやリソースを参照し、管理できます。 特定の操作で Azure Portal が必要な場合、Cloud Explorer でリンクが提供されます。そのリンクから Azure Portal に移動できます。

![Cloud Explorer](../ide/media/VSIDE_CloudExplorer.png)

Cloud Explorer の使用方法については、「[Managing Azure resources with Cloud Explorer](https://azure.microsoft.com/en-us/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/)」 (Cloud Explorer で Azure リソースを管理する) を参照してください。
Azure 開発ワークロードをインストールすると [Visual Studio Tools for Azure](https://www.visualstudio.com/vs/azure-tools/) やその他の関連ツールもインストールされます。

## <a name="tips-and-tricks"></a>ヒントとテクニック
Visual Studio をさらに便利に活用するためのショートカット、ヒント、テクニックは次のサイトでご確認いただけます。
- [Visual Studio 入門 - ヒントとテクニック](https://www.youtube.com/watch?v=vmXqGwn1Glk&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=4)
- [Visual Studio の生産性に関するヒント](../ide/productivity-tips-for-visual-studio.md)
- [Visual Studio のヒントとテクニック](https://channel9.msdn.com/events/TechEd/2013/DEV-B353)
- [C++ デバッグのヒントとテクニック](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/C-Plus-Plus-Debugging-Tips-and-Tricks)
- [Visual Studio の特に役立つ (ただし、十分に活用されていない) ヒント [Scott Hanselman のブログ]](https://www.hanselman.com/blog/VisualStudiosMostUsefulAndUnderusedTips.aspx)
- [Visual Studio 入門 - Visual Studio 拡張機能のインストール](https://www.youtube.com/watch?v=MWLLQaknRZY&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=7)
