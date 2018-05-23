---
title: for ループを foreach ステートメントに変換するためのコードのリファクタリング
ms.date: 05/10/2018
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
ms.openlocfilehash: 34758473bcbee8ccad7d9dff9df2f1478ca1202c
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>for ループと foreach ステートメント間で変換するためのリファクタリング

これらのリファクタリングは以下に適用されます。

- C#

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>for ループを foreach ステートメントに変換する

コード内に [for](/dotnet/csharp/language-reference/keywords/for) ループがある場合、このリファクタリングを使用してそれを [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) ステートメントに変換できます。

### <a name="why-convert"></a>変換する理由

[for](/dotnet/csharp/language-reference/keywords/for) ループを [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) ステートメントに変換する理由には、次のものがあります。

- 項目にアクセスするインデックスとして使用する場合を除き、ループ内で反復回数変数を使用しない。

- コードを簡略化して、初期化子、条件、イテレーション ステートメントの論理エラーの可能性を軽減したい。

### <a name="how-to-use-it"></a>使用方法

1. `for` ループの最初の行にカーソルを置きます。

1. 行の任意の場所で **Ctrl**+**.** キーを押すと、 またはコード ファイルの余白でねじ回し ![ねじ回しアイコン](../media/screwdriver-icon.png) アイコンをクリックします。

   ![['foreach' に変換] メニュー](media/convert-to-foreach.png)

1. **['foreach' に変換]** を選択します。 または、**[変更のプレビュー]** を選択して [[変更のプレビュー]](../../ide/preview-changes.md) ダイアログを開いて **[適用]** を選択します。

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>foreach ステートメントを for ループに変換する

コード内に [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) ステートメントがある場合、このリファクタリングを使用してそれを [for](/dotnet/csharp/language-reference/keywords/for) ループに変換できます。

### <a name="why-convert"></a>変換する理由

[foreach](/dotnet/csharp/language-reference/keywords/foreach-in) ステートメントを [for](/dotnet/csharp/language-reference/keywords/for) ループに変換する理由には、次のものがあります。

- 項目にアクセスするだけでなく、ループ内で反復回数変数を使用したい。

- [多次元配列を反復処理していて](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays)、配列要素をさらに制御したい。

### <a name="how-to-use-it"></a>使用方法

1. `foreach` ステートメントの最初の行にカーソルを置きます。

1. 行の任意の場所で **Ctrl**+**.** キーを押すと、 またはコード ファイルの余白でねじ回し ![ねじ回しアイコン](../media/screwdriver-icon.png) アイコンをクリックします。

   ![['for' に変換] メニュー](media/convert-to-for.png)

1. **['for' に変換]** を選択します。 または、**[変更のプレビュー]** を選択して [[変更のプレビュー]](../../ide/preview-changes.md) ダイアログを開いて **[適用]** を選択します。

1. リファクタリングにより新しい反復回数変数が導入されるため、エディターの右上隅に **[名前を変更]** ボックスが表示されます。 変数に別の名前を選択する場合は、その名前を入力してから、**Enter** キーを押すか、**[名前を変更]** ボックスで **[適用]** を選択します。 新しい名前を選択しない場合は、**Esc** キーを押すか、**[適用]** を選択して、**[名前を変更]** ボックスを閉じます。

## <a name="see-also"></a>関連項目

- [リファクタリング](../refactoring-in-visual-studio.md)
- [変更のプレビュー](../../ide/preview-changes.md)