---
title: "インターフェイスの抽出 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 98a3a96357eb6e7391eb92bd0ac3a53dd00f09f5
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2018
---
# <a name="extract-an-interface-in-visual-basic"></a>インターフェイスの抽出 (Visual Basic)

**機能:** クラス、構造体、またはインターフェイスから既存のメンバーを使用するインターフェイスを作成できます。

**条件:** 共通のものにして、他のクラス、構造体、またはインターフェイスで使用できるメソッドを持つクラス、構造体、またはインターフェイスがいくつかあるとき。

**理由:**インターフェイスは、オブジェクト指向設計の優れた構成要素であるため。  さまざまな動物のクラス (Dog、Cat、Bird) があり、これらすべてが Eat、Drink、Sleep などの共通メソッドを持つとします。  IAnimal のようなインターフェイスを使用すると、Dog、Cat、Bird に、これらのメソッド共通の "シグネチャ" を持たせることができます。  

**方法:**

1. 操作を実行するクラスの名前を強調表示するか、クラス名のどこかにテキスト カーソルを置きます。

   ![強調表示されたコード](media/extractinterface-highlight-vb.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + R** キーを押し、次に **Ctrl + I** キーを押します。  選ばれているプロファイルによってキーボード ショートカットが異なる場合があることに注意してください。
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[インターフェイスの抽出]** を選択します。
   * **マウス**
     * **[編集] > [リファクター] > [インターフェイスの抽出]** の順に選択します。
     * クラスの名前を右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[インターフェイスの抽出]** を選択します。

1. ポップアップされた **[インターフェイスの抽出]** ダイアログ ボックスで、求められた情報を入力します。![インターフェイスの抽出](media/extractinterface-dialog-vb.png)
   | フィールド | 説明 |
   | --- | --- |
   | **新しいインターフェイス名** | 作成するインターフェイスの名前。 既定値は I*ClassName*。ここで、*ClassName* は上で選択したクラスの名前になります。 |
   | **新しいファイル名** | インターフェイスを含んで生成されるファイルの名前。 インターフェイス名と同様に、既定値は I*ClassName*。ここで、*ClassName* は上で選択したクラスの名前です。 |
   | **インターフェイスを形成するパブリック メンバーを選択する** | インターフェイスに抽出する項目。  選択できる数に制限はありません。 |

1. **[OK]**をクリックします。

   インターフェイスが、指定した名前のファイルにすぐに作成されます。  さらに、選択したクラスにそのインターフェイスが実装されます。

   ![結果として得られるクラス](media/extractinterface-class-vb.png)
   ![結果として得られるインターフェイス](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>関連項目

[リファクタリング](../refactoring-in-visual-studio.md)