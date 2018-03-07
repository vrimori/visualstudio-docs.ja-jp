---
title: "Visual Studio でメソッドのシグネチャをリファクタリングする | Microsoft Docs"
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
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: c181eb27ccdbc2f1efb7294e1610a6055245241c
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="change-a-method-signature-refactoring"></a>メソッド シグネチャの変更リファクタリング

このリファクタリングは以下に適用されます。

- C#

- Visual Basic

**機能:** メソッドのパラメーターを削除またはその順序を変更できます。

**条件:** さまざまな場所で現在使用されているメソッドのパラメーターを移動または削除したいとき。

**理由:**パラメーターは手動で削除および順序を変更して、そのメソッドのすべての呼び出しを検索し、1 つずつ変更できますが、エラーにつながる可能性があります。  このリファクタリング ツールは、タスクを自動的に実行します。

## <a name="how-to"></a>方法

1. 変更するメソッドの名前またはその使用の 1 つを強調表示するか、内側にテキスト カーソルを置きます。

   - C#: 

    ![強調表示された C# のコード](media/changesignature-highlight-cs.png)

   - VB:

    ![強調表示された Visual Basic のコード](media/changesignature-highlight-vb.png)

1. 次に、以下のいずれかを実行します。

   - **キーボード**
     - **Ctrl + R** キーを押し、次に **Ctrl + V** キーを押します。  選ばれているプロファイルによってキーボード ショートカットが異なる場合があることに注意してください。
     - 行の任意の場所で **Ctrl**+**.** キーを押すと、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[シグネチャの変更]** を選択します。
   - **マウス**
     - **[編集] > [リファクター] > [パラメーターの削除]** の順に選択します。
     - **[編集] > [リファクター] > [パラメーター順序の再変更]** の順に選択します。
     - コードを右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[シグネチャの変更]** を選択します。

1. ポップアップ表示される **[シグネチャの変更]** ダイアログでは、右側にあるボタンを使ってメソッド シグネチャを変更できます。

   ![[シグネチャの変更] ダイアログ](media/changesignature-dialog-cs.png)

   | ボタン | 説明
   | ------ | ---
   | **上/下** | 選択したパラメーターを一覧内で上下に移動します
   | **削除**  | 選択したパラメーターを一覧から削除します
   | **復元** | 選択した、取り消したパラメーターを一覧に復元します

   > [!TIP]
   > コミットする前に[結果を確認する](../../ide/preview-changes.md)には、**[参照の変更のプレビュー]** チェック ボックスを使います。

1. 完了したら、**[OK]** ボタンをクリックして変更を実行します。

   - C#: 

    ![シグネチャ変更の結果 - C#](media/changesignature-result-cs.png)

   - Visual Basic: 

    ![シグネチャ変更の結果 - Visual Basic](media/changesignature-result-vb.png)

## <a name="see-also"></a>関連項目

- [リファクタリング](../refactoring-in-visual-studio.md)
- [変更のプレビュー](../../ide/preview-changes.md)