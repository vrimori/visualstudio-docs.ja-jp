---
title: "Visual Studio の R Tools オプション | Microsoft Docs"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
ms.topic: article
ms.assetid: 554dc602-ecad-4cd0-8e6f-a60bb8a2328f
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
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
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 9b680c73d54c9809e3f4c46dc2841f1f320e4af9
ms.contentlocale: ja-jp
ms.lasthandoff: 05/12/2017

---


# <a name="r-tools-for-visual-studio-options"></a>R Tools for Visual Studio オプション
 
設定には **[R Tools]、[オプション]** メニューの順に選択してアクセスできます。あるいは、**[ツール]、[オプション]** の順に選択し、**[R Tools]** までスクロールしてください。
 
  ![R Tools のオプション ダイアログ](~/docs/rtvs/media/options-dialog.png)

次のセクションでは、このページで利用できるさまざまなオプションについて説明します。

> [!Note]
> **[ツール]、[オプション]** メニューの順に選択してオプションにアクセスするときは、場合によっては、下部にある **[すべての設定を表示]** ボックスを選択しないと **[R Tools]** ページが表示されません。

<a name="data-scientist-layout"</a>

**[R Tools] には、[データ サイエンスの設定]** という特別なメニュー項目もあります。データ サイエンティストのニーズに合わせて最適に作られたレイアウトで Visual Studio IDE が構成されます。 具体的には、このオプションで [[インタラクティブ]](interactive-repl.md)、[[変数エクスプローラー]](variable-explorer.md)、[[ワークスペース]](workspaces.md) というウィンドウが開きます。

![Visual Studio のデータ サイエンティスト ウィンドウ レイアウト](~/docs/rtvs/media/installation-data-scientist-layout-result.png)

> [!Important]      
> 後で他の Visual Studio 設定に戻るには、最初に **[ツール]、[設定のインポートとエクスポート]** コマンドを使用します。**[選択された環境設定をエクスポート]** を選択し、ファイル名を指定します。 これらの設定を復元するには、同じコマンドを使用し、**[選択された環境設定をインポート]** を選択します。 データ サイエンティスト レイアウトを変更し、後でそれに戻る場合、同じコマンドを使用することもできます (**[データ サイエンスの設定]** コマンドを直接使用するのではなく)。

## <a name="debugging"></a>デバッグ

これらのオプションにより、[変数エクスプローラー](variable-explorer.md)と、ウォッチやローカルのような、デバッガー ツール ウィンドウにおける値の処理方法が制御されます (「[デバッグ](debugging.md)」を参照してください)。

| オプション | 既定値 | 説明 | 
| --- | --- | --- |
| アクティブなバインドを評価 | `True` | `True` の場合、変数やプロパティを調べるとき、必ず最新の日付値が表示されるようにします。 式の実装方法によっては、式を評価すると思わぬ結果が引き出される可能性があるというリスクがあります。 |
| ドット プレフィックス付き変数を表示 | `False` | `.` がプレフィックスとして付いている変数を表示するかどうかを指定します。 |

## <a name="general"></a>全般

| オプション | 既定値 | 説明 | 
| --- | --- | --- |
| アンケート/ニュース チェック | `Once a week` | R Tools でニュースとアンケートの更新をサーバーに確認する頻度を指定します。 | 

## <a name="help"></a>ヘルプ

| オプション | 既定値 | 説明 | 
| --- | --- | --- |
| F1 Web ブラウザー | `Internal` | Ctrl + F1 を使用し、用語を探すときのヘルプの表示方法を制御します。 `Internal` に設定すると、Visual Studio のツール ウィンドウ内にヘルプが表示されます。 `External` に設定すると、既定の Web ブラウザーにヘルプが表示されます。 | 
| F1 Web 検索文字列 | `R site:stackoverflow.com` | エディターで、ある用語の上で Ctrl + F1 を押したときに検索用語が検索エンジンに渡される方法を制御します。 既定では、文字列は `R site:stackoverflow.com` です。これは `R` を検索用語に追加します。 `site:stackoverflow.com` は検索エンジンへのディレクティブであり、`stackoverflow.com` ドメイン内のページに検索範囲を絞るように伝えます。 | 
| R ヘルプ ブラウザー | `Automatic` | F1、`?` または `??` を使用し、R ドキュメントを探すときのヘルプの表示方法を制御します。 `Automatic` に設定すると、ヘルプが該当するウィンドウで表示されます。 たとえば、HTML ヘルプは Visual Studio ツール ウィンドウ内に表示され、PDF は既定の PDF プログラムに表示されます。 `External` に設定すると、既定の Web ブラウザーにヘルプが表示されます。 |

## <a name="history"></a>履歴

| オプション | 既定値 | 説明 | 
| --- | --- | --- |
| 履歴を常に保存 | `True` | プロジェクトを閉じたとき、RTVS が作業ディレクトリの `.RHistory` ファイルにコマンド履歴を書き込むかどうかを制御します。 プロジェクトを保存せずに終了した場合にも履歴が書き込まれることにご注意ください。 |
| 検索フィルターのリセット | `True` | R 履歴ダイアログのフィルター条件に部分文字列が一致するコマンドのみを表示するように履歴ウィンドウでコマンド履歴をフィルター処理できるかどうかを決定します。 この設定により、新しいコマンドを実行したとき、あるいは新しいプロジェクトに切り替え、別の `.RHistory` ファイルの読み込みをトリガーしたとき、履歴の検索フィルターをリセットするかどうかが決定されます。 既定の設定である `True` を指定した場合、フィルター セットを付けてコマンドを実行したとき、予想外の結果の表示が最小限に抑えられます。今しがた実行したコマンドが履歴に表示されないので、不思議に思うことになります。 |
| 複数行選択を使用 | `True` | 履歴の複数行ステートメントを 1 回のクリックで選択できるかどうかを指定します。 また、インタラクティブな Windows で、行ではなくステートメントで上下矢印を動かすことができます。 |

## <a name="html"></a>HTML

| オプション | 既定値 | 説明 | 
| --- | --- | --- |
| HTML ページ ブラウザー | `External` | `ggvis` プロットのようなコンテンツや `shiny` アプリケーションを表示する場所を決定します。 `Internal` では、Visual Studio のツール ウィンドウ内に HTML 出力が表示されます。`External` では、既定のブラウザーに HTML 出力が表示されます。 | 

## <a name="logging"></a>ログの記録

| オプション | 既定値 | 説明 | 
| --- | --- | --- |
| イベントを記録する | `Normal` | RTVS 診断に使用するログ記録の詳細度を制御します。 既定値の `Normal` の場合、`TEMP` ディレクトリにログ ファイルが作成されます。 `Traffic` に設定すると、すべてのコマンドとセッションにおける応答が RTVS により記録されます。 コンピューターに残しておくようなログ ファイルですが、RTVS の問題の診断に役に立つ場合があります。 |

## <a name="markdown"></a>Markdown

| オプション | 既定値 | 説明 | 
| --- | --- | --- |
| マークダウン プレビュー ブラウザー | `External` | RMarkdown HTML 出力が表示される場所を決定します。 `Internal` の場合、Visual Studio のツール ウィンドウ内に RMarkdown HTML ドキュメントが表示されます。`External` の場合、既定のブラウザーを利用して RMarkdown HTML が表示されます。 | 

## <a name="r-engine"></a>R エンジン

| オプション | 既定値 | 説明 | 
| --- | --- | --- |
| コード ページ | `(OS Default)` | R のコード ページ (ロケール) を設定します。既定では、オペレーティング システムの基礎ロケールが使用されます。 | 
| CRAN ミラー | `(Use .Rprofile)` | パッケージ インストールに既定の CRAN ミラーを設定します。 既定の設定の `Use .Rprofile` の場合、`.RProfile` ファイルの CRAN ミラー設定を順守します。 ドロップダウン リストの CRAN ミラーの一覧から選択すれば、既定の設定をオーバーライドできます。 |
| 作業ディレクトリ | ユーザー固有フォルダー | 現在の作業ディレクトリを設定します。通常、プロジェクトを開いたときに設定されます。 |

## <a name="workspace"></a>ワークスペース

| オプション | 既定値 | 説明 | 
| --- | --- | --- |
| プロジェクトを開くときにワークスペースを読み込む | `No` | `Yes` に設定すると、プロジェクトを開いたとき、`.RData` ファイルからグローバル環境にセッション データが読み込まれます。 |
| リセット時にワークスペースを保存するためのダイアログを表示 | `Yes` | `No` に設定すると、インタラクティブな Window の [リセット] ボタンをクリックしたとき、ワークスペースを保存するように求められなくなります。 |
| プロジェクトを閉じるときにワークスペースを保存 | `No` | `Yes` に設定すると、プロジェクトを閉じたとき、`.RData` ファイルにグローバル環境が保存されます。 |
| ワークスペースを切り替える前に確認ダイアログを表示する | `Yes` | `No` に設定すると、ワークスペースを切り替えるとき、ユーザーに確認が求められません。 「[ワークスペースの切り替え](workspaces.md#switching-between-workspaces)」をご覧ください。 |
 
