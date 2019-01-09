---
title: '[オプション]、[テキスト エディター]、[C/C++]、[表示]'
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: mikeblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.workload:
- cplusplus
ms.openlocfilehash: c27673b8e6a5e0acce8f37fe20d675f56a62bbc6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846569"
---
# <a name="options-text-editor-cc-view"></a>[オプション]、[テキスト エディター]、[C/C++]、[表示]

これらのプロパティ ページを使用し、C または C++ でプログラムを記述する際のコード エディターの既定の動作を変更します。

このプロパティ ページにアクセスするには、**[ツール]** > **[オプション]** を選択し、**[テキスト エディター]**、**[C/C++]** を展開してから、**[表示]** を選択します。

## <a name="code-squiggles"></a>コードの波線

以下の設定を有効または無効にして、C および C++ のコードの波線をテキスト エディターで処理する方法を管理します。

- **スキップされた閲覧領域内のマクロ** - 閲覧データベースでスキップされた領域内のマクロを強調表示する方法を定義します (定義にかっこが含まれるマクロなど)。

- **constexpr に変換可能なマクロ** - `constexpr` 定義に変換できるマクロ定義を強調表示する方法を定義します。

## <a name="inactive-code"></a>[アクティブでないコード]

- **アクティブでないブロックの表示** - プリプロセッサのアクティブでないブロックが異なる色で表示されます。

- **アクティブでないコードの不透明度の無効化** - 不透明ではなく純色が、アクティブでないコード ブロックに使用されます。

- **アクティブでないコードの不透明度** - アクティブでないコード ブロックの不透明度の割合です。

## <a name="miscellaneous"></a>その他

- **コメント タスクの列挙** - 開いているソース ファイルで VS トークンをスキャンし、[タスク一覧] ウィンドウで報告します。

- **一致するトークンの強調表示** - カーソルが置かれている場所と一致する、囲んでいる中かっこまたは構文を強調表示します。

## <a name="outlining"></a>アウトライン

- **アウトラインの有効化** - ファイルが開いたときにアウトライン モードに入ります。

- **Outline Pragma Regions (プラグマ領域のアウトライン化)** - `#pragma` 領域ブロックを自動的にアウトライン化します。

- **Outline Statement Blocks (ステートメント ブロックのアウトライン化)** - ステートメント ブロックを自動的にアウトライン化します。

## <a name="see-also"></a>関連項目

- [言語固有のエディター オプションの設定](../../ide/reference/setting-language-specific-editor-options.md)
- [C++ でのリファクタリング (VC のブログ)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
