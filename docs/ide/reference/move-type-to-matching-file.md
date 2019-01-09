---
title: 一致するファイルへの型の移動リファクタリング
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 793ae8f86bf4c4641a3170cde011a3912d0d38ef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870548"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>一致するファイルへの型の移動リファクタリング

このリファクタリングは以下に適用されます。

- C#

- Visual Basic

**機能:** 選択した型を同じ名前の別のファイルに移動できます。

**条件:** 同じファイルに複数のクラス、構造体、インターフェイスなどがあり、分離したいとき。

**理由:** 同じファイルに複数の型を配置すると、これらの型を検索しづらくなります。 型を同じ名前のファイルに移動することで、コードが読みやすくナビゲートしやすくなります。

## <a name="how-to"></a>方法

1. 定義されている型の名前の中にカーソルを配置します。 次に例を示します。

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. 次に、以下のいずれかを実行します。

   - 行の任意の場所で **Ctrl**+**.** キーを押すと、
   - 型名を右クリックして **[クイック アクションとリファクタリング]** を選択します。

1. メニューから **[型を *TypeName*.cs に移動]** を選択します。*TypeName* は選択した型の名前です。

   型と同じ名前を持つプロジェクト内の新しいファイルに型が移動されます。

   - C#: 

      ![インラインの結果 - C#](media/movetype-result-cs.png)

   - Visual Basic: 

      ![インラインの結果 - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>関連項目

- [リファクタリング](../refactoring-in-visual-studio.md)
