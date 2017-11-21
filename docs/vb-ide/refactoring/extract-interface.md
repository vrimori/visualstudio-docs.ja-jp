---
title: "インターフェイスのリファクタリング (Visual Basic) を抽出 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: db857fb1-3e22-46e2-b15a-56ef9f329235
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractinterface
dev_langs: VB
ms.openlocfilehash: 9616cae1282b992722f75eee091e2c9d271e85f6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="extract-an-interface-in-visual-basic"></a>Visual Basic では、インターフェイスを抽出します。
**新機能:**クラス、構造体またはインターフェイスから既存のメンバーを使用するインターフェイスを作成することができます。

****があるいくつかのクラス、構造体またはできてもその他のクラス、構造体またはインターフェイスで使用され、共通するメソッドを持つインターフェイスです。

**理由:**インターフェイスは、オブジェクト指向設計の優れた構築します。  さまざまな動物 (Dog、Cat、バード) が場合がありますすべて Eat、飲み物、スリープなどの一般的なメソッドのクラスを持つ想像してください。  IAnimal のようなインターフェイスを使用して、Dog、Cat、および鳥共通のこれらのメソッドには、「署名」するとできます。  

**どう：**

1. 操作を実行するクラスの名前を強調表示または同様のテキストにカーソルを置きますどこかに、クラス名にします。

   ![強調表示されたコード](media/extractinterface_highlight.png)

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + R**、し**Ctrl + I**です。  選ばれているプロファイルによってキーボード ショートカットが異なる場合があることに注意してください。
     * キーを押して**Ctrl + です。** トリガーを**クイック アクションとリファクタリング**メニュー**インターフェイスの抽出**プレビュー ウィンドウのポップアップからです。
   * **マウス**
     * 選択**編集 > リファクター > インターフェイスの抽出**です。
     * クラスの名前を右クリックし、**クイック アクションとリファクタリング**メニュー**インターフェイスの抽出**プレビュー ウィンドウのポップアップからです。

1. **インターフェイスの抽出**、ポップアップ表示されるダイアログ ボックスが要求の情報を入力:![インターフェイスの抽出](media/extractinterface_dialog.png)
   | フィールド | 説明 |
   | --- | --- |
   | **新しいインターフェイスの名前** | 作成するインターフェイスの名前。 これは既定値は*ClassName*ここで、 *ClassName*上で選択したクラスの名前を指定します。 |
   | **新しいファイル名** | インターフェイスを含む生成されるファイルの名前。 インターフェイスの名前を持つこれは既定では、*ClassName*ここで、 *ClassName*上で選択したクラスの名前を指定します。 |
   | **インターフェイスを形成するパブリック メンバーを選択します。** | インターフェイスに抽出する項目。  必要に応じて多くを選択することがあります。 |

1. **[OK]** をクリックします。

   インターフェイスは、指定した名前のファイルにすぐに作成されます。  さらに、選択したクラスがそのインターフェイスを実装するようになりました。

   ![結果として得られるクラス](media/extractinterface_class.png)
   ![結果として得られるインターフェイス](media/extractinterface_interface.png)

## <a name="see-also"></a>関連項目
[リファクタリング (Visual Basic)](../refactoring-vb.md)