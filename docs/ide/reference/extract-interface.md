---
title: "Visual Studio でのインターフェイスの抽出リファクタリング | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: e735b194da008de83fddac564194f8bb008c66bb
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="extract-an-interface-refactoring"></a>インターフェイスの抽出リファクタリング

このリファクタリングは以下に適用されます。

- C#

- Visual Basic

**機能:** クラス、構造体、またはインターフェイスから既存のメンバーを使用するインターフェイスを作成できます。

**条件:** 共通のものにして、他のクラス、構造体、またはインターフェイスで使用できるメソッドを持つクラス、構造体、またはインターフェイスがいくつかあるとき。

**理由:**インターフェイスは、オブジェクト指向設計の優れた構成要素であるため。 さまざまな動物のクラス (Dog、Cat、Bird) があり、これらすべてが Eat、Drink、Sleep などの共通メソッドを持つとします。 IAnimal のようなインターフェイスを使用すると、Dog、Cat、Bird に、これらのメソッド共通の "シグネチャ" を持たせることができます。

## <a name="how-to"></a>方法

1. 操作を実行するクラスの名前を強調表示するか、クラス名のどこかにテキスト カーソルを置きます。

   - C#: 

    ![強調表示されたコード - C#](media/extractinterface-highlight-cs.png)

   - Visual Basic: 

    ![強調表示されたコード - Visual Basic](media/extractinterface-highlight-vb.png)

1. 次に、以下のいずれかを実行します。

   - **キーボード**
     - **Ctrl + R** キーを押し、次に **Ctrl + I** キーを押します。 選ばれているプロファイルによってキーボード ショートカットが異なる場合があることに注意してください。
     - 行の任意の場所で **Ctrl**+**.** キーを押すと、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[インターフェイスの抽出]** を選択します。
   - **マウス**
     - **[編集] > [リファクター] > [インターフェイスの抽出]** の順に選択します。
     - クラスの名前を右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[インターフェイスの抽出]** を選択します。

1. 表示される **[インターフェイスの抽出]** ダイアログ ボックスで、必要な情報を入力します。

   ![インターフェイスの展開](media/extractinterface-dialog-cs.png)

   | フィールド | 説明 |
   | --- | --- |
   | **新しいインターフェイス名** | 作成するインターフェイスの名前。 既定値は I*ClassName*。ここで、*ClassName* は上で選択したクラスの名前になります。 |
   | **新しいファイル名** | インターフェイスを含んで生成されるファイルの名前。 インターフェイス名と同様に、既定値は I*ClassName*。ここで、*ClassName* は上で選択したクラスの名前です。 |
   | **インターフェイスを形成するパブリック メンバーを選択する** | インターフェイスに抽出する項目。 選択できる数に制限はありません。 |

1. **[OK]**をクリックします。

   指定した名前のファイルにインターフェイスが作成されます。 さらに、選択したクラスにそのインターフェイスが実装されます。

   - C#: 

    ![結果のクラス - C#](media/extractinterface-class-cs.png)
    ![結果のインターフェイス - C#](media/extractinterface-interface-cs.png)

   - Visual Basic: 

    ![結果のクラス - Visual Basic](media/extractinterface-class-vb.png)
    ![結果のインターフェイス - Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>関連項目

[リファクタリング](../refactoring-in-visual-studio.md)