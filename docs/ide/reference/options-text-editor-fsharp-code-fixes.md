---
title: '[オプション]、[テキスト エディター]、[F#]、[コード修正]'
ms.date: 01/16/2019
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9345cf5d608ec8b69d88ac1c1644510f105337fd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947076"
---
# <a name="options-text-editor-f-code-fixes"></a>[オプション]、[テキスト エディター]、[F#]、[コード修正]

**[コード修正]** オプション ページを使用して、コード エラーを識別し、ソリューションを提供するために役立つ設定を指定します。 このオプション ページにアクセスするには、**[ツール]** > **[オプション]** を選び、さらに **[テキスト エディター]** > **[F#]** > **[コード修正]** の順に選びます。

## <a name="code-fixes"></a>コード修正

- **名前を単純化する (不要な修飾子を削除する)**

   このチェック ボックスをオンすると、完全修飾名の修飾が不要な場合 (頻繁に使用される名前空間のメンバーなど) に、名前が単純化されます。

- **Open ステートメントを常に最上位レベルに配置する**

   このチェック ボックスをオンにしているときに、コード内に Open ステートメントを入力すると、それが最上位レベルで配置されます。

- **未使用の Open ステートメントを削除する**

   このチェック ボックスをオンにすると、現在のファイル内の使用されていない Open ステートメントが削除されます。

- **未使用の値を解析して修正を提案する**

   このチェック ボックスをオンにすると、コード内の使用されていない値が認識されます。 その後、未使用の値をポイントすると、値を使用できる方法が推奨されます。

## <a name="see-also"></a>関連項目

- [[全般]、[環境]、[オプション] ダイアログ ボックス](../../ide/reference/general-environment-options-dialog-box.md)
- [CodeLens によるコード変更とその他の履歴の検索](../../ide/find-code-changes-and-other-history-with-codelens.md)