---
title: "フィールドのプロパティへのリファクター (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 010a297745ed6028f7ee127fffc210097d6d26f5
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2018
---
# <a name="encapsulate-a-field-in-visual-basic"></a>フィールドのカプセル化 (Visual Basic)

**機能:** フィールドをプロパティに変換し、そのフィールドのすべての使用を、新しく作成したプロパティを使用するように更新できます。

**条件:** フィールドをプロパティに移動し、そのフィールドへのすべての参照を更新したいとき。  

**理由:** 他のクラスにフィールドへのアクセスを許可しますが、これらのクラスに直接アクセス権を持たせたくはありません。  プロパティ内にフィールドをラップすることによって、たとえば、割り当てられる値を検証するコードを記述できます。

**方法:**

1. カプセル化するフィールドの名前を強調表示するか、名前の内側にテキスト カーソルを置きます。

   ![強調表示されたコード](media/encapsulate-highlight-vb.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + R** キーを押し、次に **Ctrl + E** キーを押します。  選ばれているプロファイルによってキーボード ショートカットが異なる場合があることに注意してください。
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップからどちらかの **[フィールドのカプセル化]** エントリを選択します。
   * **マウス**
     * **[編集] > [リファクター] > [フィールドのカプセル化]** の順に選択します。
     * コードを右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップからどちらかの **[フィールドのカプセル化]** エントリを選択します。

   選択ツール | 説明
   --------- | -----------
   **フィールドのカプセル化 (およびプロパティを使用します)** | プロパティでフィールドをカプセル化し、生成されたプロパティを使用するようにフィールドのすべての使用を更新します。
   **フィールドのカプセル化 (ただし、フィールドを継続して使用します)** | プロパティでフィールドをカプセル化しますが、フィールドのすべての使用については手を加えずに残します。

   プロパティはすぐに作成され、選択されている場合、フィールドへの参照が更新されます。

   > [!TIP]
   > ポップアップ ウィンドウの [**[変更のプレビュー]**](../../ide/preview-changes.md) リンクを使用すると、コミットする前に、結果を確認できます。

   ![プロパティのカプセル化の結果](media/encapsulate-result-vb.png)

## <a name="see-also"></a>関連項目

[リファクタリング](../refactoring-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)