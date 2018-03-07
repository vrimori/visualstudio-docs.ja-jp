---
title: "Visual Studio での到達できないコードの削除リファクタリング | Microsoft Docs"
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
ms.openlocfilehash: 90ea46079e318c09ab62e27f9a75ccdd2452887d
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="remove-unreachable-code-refactoring"></a>到達できないコードの削除リファクタリング

このリファクタリングは以下に適用されます。

- C#

**機能:** 実行されないコードを削除します。

**条件:** プログラムにコード スニペットに到達するパスがなく、そのコード スニペットが不要になっているとき。

**理由:** 不必要で実行されることのないコードを削除することで、読みやすさを向上させ保守を容易にします。

## <a name="how-to"></a>方法

1. 到達できずフェードアウトされているコードの任意の場所にカーソルを置きます。

![フェードアウトされている到達できないコード](media/unreachablecode-faded-cs.png)

1. 次に、以下のいずれかを実行します。

   - **キーボード**
     - 行の任意の場所で **Ctrl**+**.** キーを押すと、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[到達できないコードを削除します]** を選択します。
   - **マウス**
     - コードを右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[到達できないコードを削除します]** を選択します。

1. 変更を確認したら、**Enter** キーを押すか、メニューの [修正] をクリックすると、変更がコミットされます。

例:

```csharp
// Before
private void Method()
{
    throw new Exception(nameof(Method));
    Console.WriteLine($"Exception for method {nameof(Method)}");
}

// Remove unreachable code

// After
private void Method()
{
    throw new Exception(nameof(Method));
}
```

## <a name="see-also"></a>関連項目

- [リファクタリング](../refactoring-in-visual-studio.md)
- [変更のプレビュー](../../ide/preview-changes.md)