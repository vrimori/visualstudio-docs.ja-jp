---
title: "到達できないコードのリファクタリング (c#) を削除する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: e57db74ea431d9090df1dc34fd3cff3cf03dd475
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="remove-unreachable-code-in-c"></a>到達できないコードを削除する (C#) #
**新機能:**実行されないコードを削除します。

****プログラムには、そのコード スニペットを不要なため、コード スニペットのパスがありません。

**理由:**は余分なコードを削除することで読みやすさと保守容易性が向上し、実行されることはありません。

**どう：**

1. Out あせてコードに到達できないで任意の場所にカーソルを配置します。

![フェードの制御が渡らないコード](media/unreachablecode_faded.png)  

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + です。** トリガーに、**クイック アクションとリファクタリング**メニュー**到達できないコードを削除する**プレビュー ウィンドウのポップアップからです。
   * **マウス**
     * コードを右クリックし、選択、**クイック アクションとリファクタリング**メニュー**到達できないコードを削除**プレビュー ウィンドウのポップアップからです。

1. 変更に満足したら、キーを押して**Enter**またはメニューに修正 をクリックし、変更がコミットされます。

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

## <a name="see-also"></a>参照  
[リファクタリング (C#)](../refactoring-csharp.md)  
[変更のプレビュー](../../ide/preview-changes.md)