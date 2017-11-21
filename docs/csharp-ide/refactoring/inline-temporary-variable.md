---
title: "インラインの一時変数のリファクタリング (c#) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0182179f-f74f-47a2-a1dc-b60c86f9abaf
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e6e9ed28a42aa3d7521a059b668eed8ae1d28b8e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="inline-a-temporary-variable-with-c"></a>一時変数にインラインで (C#) #
**新機能:**する一時変数の使用を削除し、代わりに実際のコードに置き換えることができます。

****一時変数の使用により、コードの理解が困難になります。  

**理由:**一時変数を削除することによりコードを特定の状況で読みやすくします。

**どう：**

1. 強調表示またはインライン展開を解除する一時変数内のテキストのカーソルを置きます。

   ![強調表示されたコード](media/inline_highlight.png)

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + です。** トリガーを**クイック アクションとリファクタリング**メニュー**インライン一時変数**プレビュー ウィンドウのポップアップからです。
   * **マウス**
     * コードを右クリックし、選択、**クイック アクションとリファクタリング**メニュー**インライン一時変数**プレビュー ウィンドウのポップアップからです。

   変数は削除されますされ、その用途がすぐに、変数の値で置き換えられます。

   ![Inline 結果](media/inline_result.png)

## <a name="see-also"></a>関連項目  
[リファクタリング (C#)](../refactoring-csharp.md)