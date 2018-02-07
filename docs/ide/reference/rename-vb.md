---
title: "名前の変更のリファクター (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0f9421ed314dc513d5e8af30bad907766342300a
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2018
---
# <a name="rename-a-code-symbol-in-visual-basic"></a>コード シンボルの名前の変更 (Visual Basic)

**概要:** フィールド、ローカル変数、メソッド、名前空間、プロパティ、型などのコード シンボルの識別子の名前を変更します。

**タイミング:** すべてのインスタンスを検索して新しい名前をコピー/貼り付けすることなく、安全に名前を変更したいとき。

**理由:** プロジェクト全体で新しい名前をコピーおよび貼り付けることは、エラーにつながる可能性があるため。  このリファクタリング ツールでは、正確に名前変更操作が実行されます。

**方法:**

1. 名前を変更する項目を強調表示するか、項目の内側にテキスト カーソルを置きます。

   ![強調表示されたコード](media/rename-highlight-vb.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + R** キーを押し、次に **Ctrl + R** キーを押します。  選ばれているプロファイルによってキーボード ショートカットが異なる場合があることに注意してください。
   * **マウス**
     * **[編集] > [リファクター] > [名前の変更]** の順に選択します。
     * コードを右クリックし **[名前の変更]** を選択します。

1. 新しい名前を入力して、項目の名前を変更します。

   ![名前の変更アニメーション](media/rename-rename-vb.png)

   > [!TIP]
   > この新しい名前を使用するコメントなどの文字列も更新できます。また、IDE の右上に表示される **[名前の変更]** ボックス内のチェックボックスを使用して、保存前に[変更をプレビュー](../../ide/preview-changes.md)することもできます。

1. 変更を確認したら、**[適用]** ボタンをクリックするか **Enter** キーを押すと、変更がコミットされます。

> [!NOTE]
> 競合が発生する可能性がある既存の名前を使うと、IDE の **[名前の変更]** ボックスに警告が表示されます。
>
> ![名前変更の競合](media/rename-conflict-vb.png)

## <a name="see-also"></a>関連項目

[リファクタリング](../refactoring-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)