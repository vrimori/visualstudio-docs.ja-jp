---
title: '[オプション]、[テキスト エディター]、[基本] (Visual Basic) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89b73138617583b621b33b31525e3b2f9c89e9e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="options-text-editor-basic-visual-basic"></a>[オプション]、[テキスト エディター]、[基本] (Visual Basic)
**[オプション]** (**[ツール]** メニュー) ダイアログ ボックスの **[テキスト エディター]** フォルダーにある **[Basic]** フォルダーの **[VB 固有]** プロパティ ページでは、次のプロパティを指定します。  
  
 **[End コンストラクトの自動挿入]**  
 たとえば、プロシージャ宣言の最初の行として `Sub Main—` を入力し、Enter キーを押すと、対応する `End Sub` 行がテキスト エディターに追加されます。 同様に、[For](/dotnet/visual-basic/language-reference/statements/for-next-statement) ループを追加すると、対応する `Next` ステートメントがテキスト エディターに追加されます。 このオプションをオンにすると、コード エディターで自動的に End 構造が追加されます。  
  
 **[コードの再フォーマット]**  
 必要に応じてコードの書式が再設定されます。 このオプションをオンにすると、コード エディターによって次の処理が行われます。  
  
-   コードを正しいタブ位置に揃える。  
  
-   キーワード、変数、およびオブジェクトの大文字と小文字の区別を修正する。  
  
-   `Then` ステートメントの `If...Then` が欠けていた場合に補う。  
  
-   関数呼び出しにかっこを追加する。  
  
-   文字列の右引用符が欠けていた場合に補う。  
  
-   指数表記の書式を正す。  
  
-   日付の書式を正す。  
  
**[アウトライン モードを有効にする]**  
ファイルをコード エディターで開くときに、ドキュメントをアウトライン モードで表示できます。 詳細については、「[アウトライン](../../ide/outlining.md)」を参照してください。 このオプションをオンにすると、ファイルを開くときにアウトライン表示機能が有効になります。  
  
**[Interface と MustOverride メンバーの自動挿入]**  
クラスの `Implements` ステートメントまたは `Inherits` ステートメントをコミットすると、実装またはオーバーライドする必要があるメンバーのそれぞれのプロトタイプがテキスト エディターに自動的に挿入されます。  
  
**[プロシージャ行の区切り文字を表示する]**  
テキスト エディターに、プロシージャのスコープが表示されます。 プロジェクトの .vb ソース ファイルで、次の表に示す場所に線が表示されます。  
  
|.vb ソース ファイル内の場所|線が表示される場所の例|  
|---------------------------------|------------------------------|  
|ブロック宣言構造の後|-   クラス、構造体、モジュール、インターフェイス、または列挙型の最後<br />-   プロパティ、関数、または sub の後<br />-   プロパティの get 句と set 句の間は対象外|  
|一連の単一行構造|-   import ステートメントの後、クラス ファイルの型定義の前<br />-   クラスで宣言されている変数の後、プロシージャの前|  
|単一行宣言|-   Import ステートメント、Inherits ステートメント、変数宣言、イベント宣言、デリゲート宣言、および DLL の Declare ステートメントの後|  
  
**[エラー修正候補を有効にする]**  
一般的なエラーの解決方法がテキスト エディターに表示され、適切な修正方法を選択できます。修正方法を選択するとコードに適用されます。  
  
**[参照とキーワードの強調表示を有効にする]**  
テキスト エディターでは、`If..Then`、`While...End While`、`Try...Catch...Finally` などの句のシンボルのすべてのインスタンス、またはすべてのキーワードを強調表示できます。 強調表示された参照間またはキーワード間を移動するには、Ctrl キーと Shift キーを押しながら下方向キーを押すか、Ctrl キーと Shift キーを押しながら上方向キーを押します。  
  
## <a name="see-also"></a>参照  
[[全般]、[環境]、[オプション] ダイアログ ボックス](../../ide/reference/general-environment-options-dialog-box.md)   
[[オプション]、[テキスト エディター]、[すべての言語]、[タブ]](../../ide/reference/options-text-editor-all-languages-tabs.md)