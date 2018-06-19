---
title: Visual Studio での一致するファイルへの型の移動リファクタリング
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 00fab87a8fed4d1dcd9b4899551d68eaab28d46a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945338"
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
     - 行の任意の場所で **Ctrl**+**.** キーを押すと、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップ から **[型を *TypeName*.cs に移動]** を選択します。ここで、*TypeName* は選択した型の名前です。
   - **マウス**
     - コードを右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップ から **[型を *TypeName*.cs に移動]** を選択します。ここで、*TypeName* は選択した型の名前です。

   ソリューションの一部として、型がその名前の新しいファイルに移動されます。

   - C#: 

    ![インラインの結果 - C#](media/movetype-result-cs.png)

   - Visual Basic: 

    ![インラインの結果 - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>関連項目

- [リファクタリング](../refactoring-in-visual-studio.md)