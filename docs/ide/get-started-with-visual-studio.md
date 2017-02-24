---
title: "Visual Studio 入門 | Microsoft Docs"
description: "Visual Studio の基本的な使い方について説明します。"
ms.custom: 
ms.date: 12/05/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, getting started
ms.assetid: 38e90339-1da5-410c-8ba4-437fc556cba7
caps.latest.revision: 65
author: kempb
ms.author: kempb
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
ms.sourcegitcommit: 27493b53229d9ceb6bc215fcf3d57a60fe4358b0
ms.openlocfilehash: 452f8dbd2c7eb4bcc2f0310da1f04c6dd031f629

---
# <a name="get-started-with-visual-studio"></a>Visual Studio 入門

Visual Studio は高性能のアプリ開発ツールです。 [Visual Studio](https://aka.ms/vs/15/preview/vs_enterprise) をまだインストールしていないのであれば、今すぐダウンロードし、インストールしてください。 Visual Studio をダウンロードし、設定する方法については、「[Getting Started with Visual Studio – Setting up your IDE](https://www.youtube.com/watch?v=xLCedknQkN0&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=1)」 (Visual Studio 入門 – IDE のセットアップ) という動画をご覧ください。

## <a name="visual-studio-tour"></a>Visual Studio ツアー
Visual Studio には、一連のツール ウィンドウ、メニュー、ツール バーがあります。これらはまとめて IDE (Integrated Development Environment/統合開発環境) と呼ばれています。 Visual Studio IDE は、開発作業を支援します。 頻繁に利用する IDE アイテムには次のようなものがあります。

### <a name="code-editor"></a>コード エディター
これは Visual Studio で最も頻繁に使用されるツール ウィンドウの&1; つです。このエディターで、コードを記述し、表示し、コード内を移動します。

![コード エディター](../ide/media/VSIDE_CodeWindow.png)

コード エディターには、ステートメント入力候補、構文色付け、マップ モードなど、コードを簡単に記述したり、検索したりするための便利な機能があります。 詳細については、「[Getting Started with Visual Studio - Editing and navigating your code](https://www.youtube.com/watch?v=4glwwioCVjA&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=5)」 (Visual Studio 入門 - コードの編集と移動) という動画をご覧ください。

ソリューションの種類によっては、WPF や Windows フォームなど、フォームが含まれることがあります。 その場合、この領域にはビジュアル デザイナーも表示されます。このデザイナーでは、ボタンやリスト ボックスなどのコントロールを目で確認しながらフォームに追加できます。

### <a name="solution-explorer"></a>ソリューション エクスプローラー

**ソリューション エクスプローラー**というツール ウィンドウには、コード ファイルが一覧表示されます。 ソリューション エクスプローラーを利用すれば、ファイルをソリューションやプロジェクトにまとめ、コードを整理できます。 太字のプロジェクトはスタートアップ プロジェクトと呼ばれています。 これは、ソリューションの開始時に実行される最初のコードです。 スタートアップ プロジェクトは変更できます。 詳細については、「[Getting Started with Visual Studio - Building blocks of the IDE](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK)」 (Visual Studio 入門 - IDE の構成要素) という動画をご覧ください。

![ソリューション エクスプローラーの折りたたまれているノード](../ide/media/VSIDE_SolutionExplorer2_callouts.png)

 ソリューションとプロジェクト以外に、ソリューション エクスプローラーには、プロジェクトのノードを展開したとき、各プロジェクトの全ファイルが一覧表示されます。 各プロジェクトには、1 つまたは複数のファイルが含まれています。ソース コード ファイルやリソース ファイル (画像やライブラリなど) などです。

![ソリューション エクスプローラー](../ide/media/VSIDE_SolutionExplorer3.png)

ソリューション、プロジェクト、ファイルのプロパティを見るには、ショートカット (右クリック) メニューで**プロパティ** コマンドを選択するか、メニューで **[表示]、[プロパティ] ウィンドウ**の順に選択します。

![[プロパティ] ウィンドウ](../ide/media/VSIDE_SolutionExplorer4.png)

ただし、ソリューションやプロジェクトを作成しなくてもコード記述を開始できます。 Visual Studio のコード ファイルを直接開いてください。Git リポジトリから複製されたファイルなどをすぐに編集できます。 ファイルはソリューション エクスプローラーに表示され、従来のエクスプローラーと同様に、構文色付けや基本的なステートメント入力候補などの機能が与えられます。 詳細については、「[Open Any Folder](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/)」 (フォルダーを開く) を参照してください。

### <a name="toolbar-and-menus"></a>ツール バーとメニュー
プロジェクトを実行するには、新しいソリューションを作成し、ファイルを保存し、さらに Visual Studio のツール バーやメニュー コマンドを利用します。 たとえば、コードを実行してデバッグする準備ができたら、ツール バーの **[開始]** ボタンを選択するか、メニューで **[デバッグ]、[デバッグの開始]** の順に選択します。 新しいソリューションを作成するには、**[新しいプロジェクト]** ボタンを選択するか、メニューで **[ファイル]、[新しいプロジェクト]** の順に選択します。同様の操作が他にもあります。

![Visual Studio ツール バー](../ide/media/VSIDE_SolutionExplorer5_callouts.png)

ツール バー アイコンとメニュー コマンドはコンテキスト、つまり、現在選択されている項目によって変わります。

### <a name="team-explorer"></a>チーム エクスプローラー
**チーム エクスプローラー**では、[Git](https://git-scm.com/) や [Team Foundation バージョン管理 (TFVC)](https://www.visualstudio.com/en-us/docs/tfvc/overview) など、ソース コントロール ツールに接続し、コードをローカル保存したり、ホストされるサービスで他のユーザーと共有したりできます。 作業の追跡記録などもできます。

詳細については、「[Getting Started with Visual Studio – Building blocks of the IDE](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK)」 (Visual Studio 入門 - IDE の構成要素) と「[Getting Started with Visual Studio – Opening a project from Source Control](https://www.youtube.com/watch?v=pc9vX_4RGV4&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=3)」 (Visual Studio 入門 - ソース コントロールからプロジェクトを開く) という動画をご覧ください。

![チーム エクスプローラー](../ide/media/TeamExplorer.png)

### <a name="output-window"></a>[出力] ウィンドウ
**[出力]** ウィンドウには、デバッグ メッセージ、エラー メッセージ、コンパイラの警告、公開状態メッセージなど、Visual Studio の通知が出力されます。 メッセージの種類ごとに独自のタブがあります。

![[出力] ウィンドウ](../ide/media/VSIDE_OutputWindow.png)

[出力] ウィンドウのデバッグの使用方法については、「[The Output window while debugging with Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2015/02/09/the-output-window-while-debugging-with-visual-studio/)」 (Visual Studio でデバッグするときの出力ウィンドウ) を参照してください。

## <a name="first-steps"></a>最初の手順
- **セットアップ** - Visual Studio をダウンロードし、セットアップする方法については、「[Setup & Installation](https://go.microsoft.com/fwlink/?linkid=833223)」 (セットアップとインストール) を参照してください。
- **基本** - Visual Studio のしくみについては、「[Get Started Developing with Visual Studio](../ide/get-started-developing-with-visual-studio.md)」 (Visual Studio で開発を始める) を参照してください。
- **設定** - Visual Studio の動作をカスタマイズします。 「[Visual Studio IDE のカスタマイズ](https://msdn.microsoft.com/en-us/library/mt269425.aspx)」を参照してください。
- **チュートリアル** - Visual Studio でコードを開発する方法については、「[Visual C# と Visual Basic の概要](https://msdn.microsoft.com/en-us/library/dd492171.aspx)」や「[Visual Studio 内の C++ の概要](https://msdn.microsoft.com/en-us/library/jj620919.aspx)」などのチュートリアルをご覧ください。
- **動画** - Visual Studio の他の機能や側面については、YouTube の [Microsoft Visual Studio チャネル](https://www.youtube.com/user/VisualStudio/videos)の動画や [Channel 9](https://channel9.msdn.com/Tags/visual+studio) の Visual Studio 動画をご覧ください。

## <a name="access-cloud-based-resources"></a>クラウドベース リソースにアクセスする

アプリやゲームでクラウドベースのリソースを使用する場合、[Azure サービス](https://azure.microsoft.com/en-us/services/)を追加します。 新しい Visual Studio インストーラーを利用して Azure ワークロードをインストールすると、Azure SDK for .NET がインストールされます。 インストールされるパッケージは、SDK の 2.9.5 バージョンと同じ機能レベルです。 このバージョンと将来のすべてのバージョンの Visual Studio では、Azure SDK for .NET は Visual Studio インストーラーからのみ取得できます。

Azure SDK for .NET をインストールすると、**Cloud Explorer** という名前の新しいツール ウィンドウを Visual Studio で利用できるようになります。 Cloud Explorer を利用すると、Visual Studio 内から Azure のアセットやリソースを参照し、管理できます。 特定の操作で Azure Portal が必要な場合、Cloud Explorer でリンクが提供されます。そのリンクから Azure Portal に移動できます。

![Cloud Explorer](../ide/media/VSIDE_CloudExplorer.png)

Cloud Explorer の使用方法については、「[Managing Azure resources with Cloud Explorer](https://azure.microsoft.com/en-us/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/)」 (Cloud Explorer で Azure リソースを管理する) を参照してください。
Azure SDK をインストールすると,[Visual Studio Tools for Azure](https://www.visualstudio.com/vs/azure-tools/) やその他のツールもインストールされます。

## <a name="tips-and-tricks"></a>ヒントとテクニック
Visual Studio をさらに便利に活用するためのショートカット、ヒント、テクニックは次のサイトでご確認いただけます。
- [Visual Studio 入門 - ヒントとテクニック](https://www.youtube.com/watch?v=vmXqGwn1Glk&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=4)
- [Visual Studio の生産性に関するヒント](https://msdn.microsoft.com/en-us/library/jj153218.aspx)
- [Visual Studio のヒントとテクニック](https://channel9.msdn.com/events/TechEd/2013/DEV-B353)
- [C++ デバッグのヒントとテクニック](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/C-Plus-Plus-Debugging-Tips-and-Tricks)
- [Visual Studio 入門 - Visual Studio 拡張機能のインストール](https://www.youtube.com/watch?v=MWLLQaknRZY&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=7)



<!--HONumber=Feb17_HO4-->


