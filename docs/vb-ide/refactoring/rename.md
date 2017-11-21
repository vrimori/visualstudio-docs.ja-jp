---
title: "名前の変更 - (Visual Basic) をリファクタリング |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abf1565b-c7b7-4d45-b3d3-a438a836c70e
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.rename
dev_langs: VB
ms.openlocfilehash: 35313f036e1f324d3f8908a4527cd3a2ad64ae52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="rename-a-code-symbol-in-visual-basic"></a>Visual Basic のコードのシンボルの名前変更します。
**新機能:**フィールド、ローカル変数、メソッド、名前空間、プロパティや種類などのコードのシンボルの識別子の名前を変更することができます。

****安全なものをすべてのインスタンスを検索し、新しい名前をコピー/貼り付けをしなくても名前を変更します。  

**理由:**コピーし、プロジェクト全体で、新しい名前を貼り付けることがそうなエラーが発生します。  このリファクタリング ツールには、正確に名前変更操作が実行されます。

**どう：**

1. 強調表示や、カーソルを置き、テキストを変更する項目の内部。

   ![強調表示されたコード](media/rename_highlight.png)

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + R**、し**Ctrl + R**です。  選ばれているプロファイルによってキーボード ショートカットが異なる場合があることに注意してください。
   * **マウス**
     * 選択**編集 > リファクター > の名前を変更**です。
     * コードを右クリックし **の名前を変更**です。

1. 新しい名前を入力するだけで、項目の名前を変更します。

   ![アニメーションの名前を変更します。](media/rename_rename.png)

   > [!TIP]
   > コメントおよびこの新しい名前を使用するには、その他の文字列を更新することもだけでなく[変更のプレビュー](../../ide/preview-changes.md)保存前に、チェック ボックスを使用して、**の名前を変更**上部に表示されるボックス、IDE の右。

1. 変更に満足したら、をクリックして、**適用**ボタンまたはキーを押して**Enter**し、変更がコミットされます。

> [!NOTE]
> 競合が発生するが既に存在する名前を使用する場合、**の名前を変更**ボックス、IDE で警告が表示されます。
>
> ![名前変更の競合](media/rename_conflict.png)

## <a name="see-also"></a>関連項目  
[リファクタリング (Visual Basic)](../refactoring-vb.md)  
[変更のプレビュー](../../ide/preview-changes.md)