---
title: "Visual Studio で参照の近くに変数宣言を移動する | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: a76e6024a2b61bcae08fb8db169483bcee6e5d19
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="move-declaration-near-reference-refactoring"></a>参照の近くへの宣言の移動リファクタリング

このリファクタリングは以下に適用されます。

- C#

**機能:** 変数宣言を使用箇所の近くに移動できます。

**条件:** より狭いスコープに保持できる変数宣言があるとき。

**理由:** そのままにしておくこともできますが、読みやすさの問題または情報の隠蔽を招く可能性があります。 これは、読みやすさを向上させるためにリファクタリングするチャンスです。

## <a name="how-to"></a>方法

1. 変数宣言にカーソルを置きます。

1. 次に、以下のいずれかを実行します。

   - **キーボード**
     - 行の任意の場所で **Ctrl**+**.** キーを押すと、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[宣言を参照の近くに移動]** を選択します。
   - **マウス**
     - コードを右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[宣言を参照の近くに移動]** を選択します。

1. 変更を確認したら、**Enter** キーを押すか、メニューの [修正] をクリックすると、変更がコミットされます。

例:

```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>関連項目

- [リファクタリング](../refactoring-in-visual-studio.md)
- [変更のプレビュー](../../ide/preview-changes.md)