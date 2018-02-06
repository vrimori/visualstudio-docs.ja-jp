---
title: "一時変数の値への置換 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 626224e8ed90196294f7b3ded245bb5272f70595
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="inline-a-temporary-variable-with-c"></a>インラインの一時変数 (C#) #

**機能:** 一時変数を削除し、代わりにその値に置換できます。

**条件:** 一時変数の使用により、コードの理解が困難になったとき。

**理由:** 一時変数を削除すると、コードが読みやすくなることがあるため。

**方法:**

1. インライン化する一時変数を強調表示するか、一時変数の内側にテキスト カーソルを置きます。

   ![強調表示されたコード](media/inline-highlight-cs.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーします。
   * **マウス**
     * コードを右クリックして **[クイック アクションとリファクタリング]** メニューを選択します。

1. [プレビュー] ウィンドウ ポップアップから **[インラインの一時変数]** を選択します。

   変数が削除され、その使用箇所が変数の値に即座に置き換えられます。

   ![インラインの結果](media/inline-result-cs.png)

## <a name="see-also"></a>関連項目

[リファクタリング](../refactoring-in-visual-studio.md)