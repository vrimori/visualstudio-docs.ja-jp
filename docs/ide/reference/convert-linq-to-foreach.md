---
title: LINQ クエリを foreach ステートメントに変換するためのコードのリファクタリング
ms.date: 05/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e3e4e448931e028c53d62c534e2785e4f026a7ec
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268328"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>LINQ を foreach ステートメントに変換するためのリファクタリング

このリファクタリングは、[LINQ クエリ構文](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq)を [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) ステートメントに変換するために使います。

このリファクタリングは以下に適用されます。

- C#

## <a name="how-to-use-it"></a>使用方法

1. `from` で始まる LINQ クエリ全体を選びます。

   > [!NOTE]
   > このリファクタリングは、クエリ構文で表されている LINQ クエリの変換にのみ使用でき、メソッド構文には使用できません。

1. 行の任意の場所で **Ctrl**+**.** キーを押すと、 またはコード ファイルの余白でねじ回し ![ねじ回しアイコン](../media/screwdriver-icon.png) アイコンをクリックします。

   ![LINQ から foreach への変換クイック アクション メニュー](media/convert-linq-to-foreach.png)

1. **['foreach' に変換]** を選択します。 または、**[変更のプレビュー]** を選択して [[変更のプレビュー]](../../ide/preview-changes.md) ダイアログを開いて **[適用]** を選択します。

> [!NOTE]
> C# の場合、これらのリファクタリングによって生成されるコードでは、`foreach` ループのイテレーション変数には明示的な型または [var](/dotnet/csharp/language-reference/keywords/var) が使われます。 生成されるコードが明示的または暗黙的のどちらになるかは、スコープ内にのコード スタイルの設定によって決まります。 これらの特定のコード スタイルの設定は、コンピューター レベルの **[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[コード スタイル]** > **[全般]** > **[\'var' を優先]** で、またはソリューション レベルの [EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types) ファイルで構成します。 コード スタイルの設定を **[オプション]** で変更した場合、変更を有効にするにはコード ファイルを開きなおします。

## <a name="see-also"></a>関連項目

- [LINQ](/dotnet/standard/using-linq)
- [リファクタリング](../refactoring-in-visual-studio.md)
- [変更のプレビュー](../../ide/preview-changes.md)