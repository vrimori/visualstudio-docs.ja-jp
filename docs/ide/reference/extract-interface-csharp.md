---
title: "インターフェイスの抽出 (C#) | Microsoft Docs"
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
f1_keywords: vs.csharp.refactoring.extractinterface
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 0e763bacb6d900fea251b3c41d33fb464479f2c4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="extract-an-interface-in-c"></a>インターフェイスの抽出 (C#) #

**機能:** クラス、構造体、またはインターフェイスから既存のメンバーを使用するインターフェイスを作成できます。

**条件:** 共通のものにして、他のクラス、構造体、またはインターフェイスで使用できるメソッドを持つクラス、構造体、またはインターフェイスがいくつかあるとき。

**理由:**インターフェイスは、オブジェクト指向設計の優れた構成要素であるため。  さまざまな動物のクラス (Dog、Cat、Bird) があり、これらすべてが Eat、Drink、Sleep などの共通メソッドを持つとします。  IAnimal のようなインターフェイスを使用すると、Dog、Cat、Bird に、これらのメソッド共通の "シグネチャ" を持たせることができます。

**方法:**

1. 操作を実行するクラスの名前を強調表示するか、クラス名のどこかにテキスト カーソルを置きます。

   ![強調表示されたコード](media/extractinterface-highlight-cs.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + R** キーを押し、次に **Ctrl + I** キーを押します。  選ばれているプロファイルによってキーボード ショートカットが異なる場合があることに注意してください。
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[インターフェイスの抽出]** を選択します。
   * **マウス**
     * **[編集] > [リファクター] > [インターフェイスの抽出]** の順に選択します。
     * クラスの名前を右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[インターフェイスの抽出]** を選択します。

1. ポップアップされた **[インターフェイスの抽出]** ダイアログ ボックスで、求められた情報を入力します。![インターフェイスの抽出](media/extractinterface-dialog-cs.png)
   | フィールド | 説明 |
   | --- | --- |
   | **新しいインターフェイス名** | 作成するインターフェイスの名前。 既定値は I*ClassName*。ここで、*ClassName* は上で選択したクラスの名前になります。 |
   | **新しいファイル名** | インターフェイスを含んで生成されるファイルの名前。 インターフェイス名と同様に、既定値は I*ClassName*。ここで、*ClassName* は上で選択したクラスの名前です。 |
   | **インターフェイスを形成するパブリック メンバーを選択する** | インターフェイスに抽出する項目。  選択できる数に制限はありません。 |

1. **[OK]**をクリックします。

   インターフェイスが、指定した名前のファイルにすぐに作成されます。  さらに、選択したクラスにそのインターフェイスが実装されます。

   ![結果として得られるクラス](media/extractinterface-class-cs.png)
   ![結果として得られるインターフェイス](media/extractinterface-interface-cs.png)

## <a name="see-also"></a>関連項目

[リファクタリング](../refactoring-in-visual-studio.md)