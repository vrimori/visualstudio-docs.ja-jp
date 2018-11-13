---
title: C# エディターの書式設定オプション
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 542d14e5913b1537d5e5e6aabb7264cd15add793
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220522"
---
# <a name="options-text-editor-c-code-style-formatting"></a>[オプション]、[テキスト エディター]、[C#]、[コード スタイル]、[書式設定]

**[書式設定]** オプション ページを使って、コード エディターでのコード書式設定オプションを設定します。 このオプション ページにアクセスするには、**[ツール]** > **[オプション]** の順に選択します。 **[オプション]** ダイアログ ボックスで、**[テキスト エディター]** > **[C#]** > **[コード スタイル]** > **[書式設定]** の順に選択します。

## <a name="general-page"></a>[全般] ページ

### <a name="general-settings"></a>全般設定

これらの設定は、コード エディターで書式設定オプションがコードに適用される*タイミング* に影響します。

|group1|説明|
|-----------|-----------------|
|**入力時にオートフォーマットする**|オフにすると、**[; でステートメントをオートフォーマットする]** および **[} でブロックをオートフォーマットする]** オプションが無効になります。|
|**; でステートメントをオートフォーマットする**|オンにすると、入力時に、ステートメントがエディター用に選択された書式オプションに従って書式設定されます。|
|**} でブロックをオートフォーマットする**|オンにすると、エディター用に選択した書式オプションに従って、コード ブロックの記述後すぐにコード ブロックへ書式が適用されます。|
|**戻り時にオートフォーマットする**|オンにすると、**Enter** キーを押したときに、テキストがエディター用に選択された書式オプションに合わせて書式設定されます。|
|**貼り付け時にオートフォーマットする**|オンにすると、エディターに貼り付けされたテキストが、エディター用に選択された書式オプションに合わせて書式設定されます。|

### <a name="format-document-settings"></a>[ドキュメントのフォーマット] 設定

これらの設定では、ファイルで追加のコード クリーンアップを実行するように **[ドキュメントのフォーマット]** コマンドを構成します。 これらの設定を適用する方法の詳細については、「[Format Document command](../code-styles-and-quick-actions.md#format-document-command)」 ([ドキュメントのフォーマット] コマンド) を参照してください。

|group1|説明|対応する EditorConfig と [ツール] > [オプション] ルール|
|-----------|-----------------|-----------------|-----------------|
|**すべての C# 書式ルールを適用 (インデント、折り返し、スペースの設定)**|**[ドキュメントのフォーマット]** コマンドでは通常、書式設定に関する問題が修正されます。 この設定を変更することはできません。| [主な EditorConfig オプション](../../ide/create-portable-custom-editor-options.md)<br/>[.NET EditorConfig の書式設定オプション](../../ide/editorconfig-code-style-settings-reference.md#formatting-conventions)<br/><br/>**[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[書式設定]** > **[インデント]** または **[改行]** または **[行間]** または **[折り返し]**|
|**書式設定中に追加のコード クリーンアップを実行する**|選択すると、**Edit.FormatDocument** コマンドで以下に指定されたルールに対して修正が適用されます。| N/A |
|**不要な using の削除**|選択すると、**Edit.FormatDocument** がトリガーされたときに不要な `using` ディレクティブが削除されます。| N/A |
|**using の並べ替え**|選択すると、**Edit.FormatDocument** がトリガーされたときに `using` ディレクティブが並べ替えられます。| dotnet_sort_system_directives_first<br/><br/>**[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[詳細]** > **[using の並べ替えのとき、最初に 'System' ディレクティブを配置する]** |
|**単一行のコントロール ステートメント用のかっこの追加と削除**|選択すると、**Edit.FormatDocument** がトリガーされたときに、単一行のコントロール ステートメントのかっこが追加または削除されます。| csharp_prefer_braces<br/><br/>**[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[コード スタイル]** > **[コード ブロックの優先順位]** > **[波かっこを優先します]** |
|**アクセシビリティ修飾子の追加**|選択すると、**Edit.FormatDocument** がトリガーされたときに、不足しているアクセシビリティ修飾子が追加されます。| dotnet_style_require_accessibility_modifiers |
|**アクセシビリティ修飾子の並べ替え**|選択すると、**Edit.FormatDocument** がトリガーされたときに、アクセシビリティ修飾子が並べ替えられます。| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**式/ブロック本体の初期設定の適用**|選択すると、**Edit.FormatDocument** がトリガーされたときに、式形式のメンバーがブロック本体に変換されるか、その逆の変換が行われます。| [式形式のメンバーの EditorConfig オプション](../../ide/editorconfig-code-style-settings-reference.md#expression_bodied_members)<br/><br/>**[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[コード スタイル]** > **[式の優先順位]** > **[メソッドに式本体を使用する]、[コンストラクターに式本体を使用する] など** |
|**暗黙的/明示的な型の初期設定の適用**|選択すると、**Edit.FormatDocument** がトリガーされたときに、`var` が明示的な型に変換されるか、その逆の変換が行われます。| [明示的な型の Core EditorConfig オプション](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types)<br/><br/>**[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[コード スタイル]** > **['var' を優先]** |
|**インラインの 'out' 変数の初期設定の適用**|選択すると、**Edit.FormatDocument** がトリガーされたときに、可能な場合は `out` 変数がインライン化されます。| csharp_style_inlined_variable_declaration<br/><br/>**[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[コード スタイル]** > **[変数の優先順位]** > **[インライン変数宣言を優先する]** |
|**言語/フレームワークの種類の初期設定の適用**|選択すると、**Edit.FormatDocument** がトリガーされたときに、言語の種類がフレームワークの種類に変換されるか、その逆の変換が行われます。| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[コード スタイル]** > **[定義済みの型の設定]** |
|**オブジェクト/コレクションの初期化の設定の適用**|選択すると、**Edit.FormatDocument** がトリガーされたときに、可能な場合はオブジェクトとコレクションの初期化子が使用されます。| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[コード スタイル]** > **[式の優先順位]** > **[オブジェクト初期化子を優先する]** または **[コレクション初期化子を優先する]** |
|**'this.' 修飾子の初期設定の適用**|選択すると、**Edit.FormatDocument** がトリガーされたときに `this.` の初期設定が適用されます。| [this. 修飾子の EditorConfig オプション](../../ide/editorconfig-code-style-settings-reference.md#this_and_me)<br/><br/>**[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[コード スタイル]** > **['this.' の優先]** |
|**可能な場合はプライベート フィールドを読み取り専用にする**|選択すると、**Edit.FormatDocument** がトリガーされたときに、可能な場合はプライベート フィールドが `readonly` になります。| dotnet_style_readonly_field<br/><br/>**[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[コード スタイル]** > **[フィールドの設定]** > **[読み取り専用を優先します]** |
|**不要なキャストを削除する**|選択すると、**Edit.FormatDocument** がトリガーされたときに、可能な場合は不要なキャストが削除されます。| N/A |
|**未使用の変数を削除する**|選択すると、**Edit.FormatDocument** がトリガーされたときに、未使用の変数が削除されます。| N/A |

![Visual Studio での C# 用のコード クリーンアップ設定](media/format-document-settings.png)

## <a name="preview-windows"></a>プレビュー ウィンドウ

**[インデント]**、**[改行]**、**[行間]**、および **[折り返し]** の各サブページには、下部にプレビュー ウィンドウが表示されます。 プレビュー ウィンドウでは、オプション適用時の状態が表示されます。 プレビュー ウィンドウを使用するには、書式オプションを選択します。 プレビュー ウィンドウに、選択したオプションを適用した例が表示されます。 ラジオ ボタンまたはチェック ボックスを選んで設定を変更すると、プレビュー ウィンドウが更新され、新しい設定が反映されます。

## <a name="indentation-remarks"></a>インデントに関するコメント

各言語の **[タブ]** ページのインデント オプションでは、行の最後で **Enter** キーを押したときにコード エディターでカーソルがどこに配置されるかということだけを決定します。 **[書式設定]** のインデント オプションは、たとえば、**[貼り付け時にオート フォーマットする]** チェック ボックスがオンになっている間にコードをファイルに貼り付けるときなど、コードが自動的に書式設定される場合に適用されます。また、フォーマットされるブロックを手動で入力する場合にも適用されます。

## <a name="see-also"></a>関連項目

- [[全般] ([オプション] ダイアログ ボックス - [環境])](../../ide/reference/general-environment-options-dialog-box.md)