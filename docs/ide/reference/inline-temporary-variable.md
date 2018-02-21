---
title: "Visual Studio で一時変数をその値と置き換える | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: b66236847e597aeddb4e6f09c27e64e717fdb7d9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="inline-a-temporary-variable-refactoring"></a>一時変数のインライン化リファクタリング

このリファクタリングは以下に適用されます。

- C#

- Visual Basic

**機能:** 一時変数を削除し、代わりにその値に置換できます。

**条件:** 一時変数の使用により、コードの理解が困難になったとき。

**理由:** 一時変数を削除すると、コードが読みやすくなることがあるため。

## <a name="how-to"></a>方法

1. インライン化する一時変数を強調表示するか、一時変数の内側にテキスト カーソルを置きます。

   - C#: 

    ![強調表示されたコード - C#](media/inline-highlight-cs.png)

   - Visual Basic: 

    ![強調表示されたコード - Visual Basic](media/inline-highlight-vb.png)

1. 次に、以下のいずれかを実行します。

   - **キーボード**
     - **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーします。
   - **マウス**
     - コードを右クリックして **[クイック アクションとリファクタリング]** メニューを選択します。

1. [プレビュー] ウィンドウ ポップアップから **[インラインの一時変数]** を選択します。

   変数が削除されて、その使用箇所が変数の値に置き換えられます。

   - C#: 

    ![インラインの結果 - C#](media/inline-result-cs.png)

   - Visual Basic: 

    ![インラインの結果 - Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>関連項目

[リファクタリング](../refactoring-in-visual-studio.md)