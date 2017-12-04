---
title: "リファクタリング (c#) - 参照の近くの宣言に移動 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: d79d55ae-f6bb-4902-8db2-e7fe01bdb0bf
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.openlocfilehash: f784ac9fec1dce1f21ba4b9f1f0e83b4b7deb001
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/29/2017
---
# <a name="move-declaration-near-reference-in-c"></a>C# で参照の近くの宣言に移動します。 #
**新機能:**近くの変数宣言をそれぞれの使用方法に移動することができます。

**より狭**いスコープに保持できる変数の宣言を持っています。

**理由:**であるが、読みやすさの問題または情報の隠蔽を招く可能性は省略できます。 これは、読みやすさを向上させるためにリファクタリングすることです。

**どう：**

1. 変数の宣言でカーソルを置きます。

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + です。** トリガーを**クイック アクションとリファクタリング**メニュー**参照の近くの宣言に移動**プレビュー ウィンドウからです。
   * **マウス**
     * コードを右クリックし、選択、**クイック アクションとリファクタリング**メニュー**参照の近くの宣言に移動**プレビュー ウィンドウのポップアップからです。

1. 変更に満足したら、キーを押して**Enter**またはメニューに修正 をクリックし、変更がコミットされます。

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
[リファクタリング (C#)](../refactoring-csharp.md)  
[変更のプレビュー](../../ide/preview-changes.md)