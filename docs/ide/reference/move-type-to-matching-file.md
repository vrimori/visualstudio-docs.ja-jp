---
title: "Visual Studio での一致するファイルへの型の移動リファクタリング | Microsoft Docs"
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
ms.openlocfilehash: 62187c88fa2d2cf7ecf1b358fa0c03416be449a8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>一致するファイルへの型の移動リファクタリング

このリファクタリングは以下に適用されます。

- C#

- Visual Basic

**機能:** 選択した型を同じ名前の別のファイルに移動できます。

**条件:** 同じファイルに複数のクラス、構造体、インターフェイスなどがあり、分離したいとき。

**理由:** 同じファイルに複数の型を配置すると、これらの型を検索しづらくなります。 型を同じ名前のファイルに移動することで、コードが読みやすくナビゲートしやすくなります。

## <a name="how-to"></a>方法

1. 移動する型の名前を強調表示するか、名前の内側にテキスト カーソルを置きます。

   - C#: 

    ![強調表示されたコード - C#](media/movetype-highlight-cs.png)

   - Visual Basic: 

    ![強調表示されたコード - Visual Basic](media/movetype-highlight-vb.png)

1. 次に、以下のいずれかを実行します。

   - **キーボード**
     - **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップ から **[型を *TypeName*.cs に移動]** を選択します。ここで、*TypeName* は選択した型の名前です。
   - **マウス**
     - コードを右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップ から **[型を *TypeName*.cs に移動]** を選択します。ここで、*TypeName* は選択した型の名前です。

   ソリューションの一部として、型がその名前の新しいファイルに移動されます。

   - C#: 

    ![インラインの結果 - C#](media/movetype-result-cs.png)

   - Visual Basic: 

    ![インラインの結果 - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>関連項目

[リファクタリング](../refactoring-in-visual-studio.md)