---
title: "メソッド シグネチャのリファクター (C#) | Microsoft Docs"
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
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 44aaf3f4a570600b715d6d54f5fd80da84611b94
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2018
---
# <a name="change-a-method-signature-in-c"></a>メソッド シグネチャの変更 (C#) #

**機能:** メソッドのパラメーターを削除またはその順序を変更できます。

**条件:** さまざまな場所で現在使用されているメソッドのパラメーターを移動または削除したいとき。  

**理由:**パラメーターは手動で削除および順序を変更して、そのメソッドのすべての呼び出しを検索し、1 つずつ変更できますが、エラーにつながる可能性があります。  このリファクタリング ツールは、タスクを自動的に実行します。

**方法:**

1. 変更するメソッドの名前またはその使用の 1 つを強調表示するか、内側にテキスト カーソルを置きます。

   ![強調表示されたコード](media/changesignature-highlight-cs.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + R** キーを押し、次に **Ctrl + V** キーを押します。  選ばれているプロファイルによってキーボード ショートカットが異なる場合があることに注意してください。
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[シグネチャの変更]** を選択します。
   * **マウス**
     * **[編集] > [リファクター] > [パラメーターの削除]** の順に選択します。
     * **[編集] > [リファクター] > [パラメーター順序の再変更]** の順に選択します。
     * コードを右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[シグネチャの変更]** を選択します。

1. ポップアップ表示される **[シグネチャの変更]** ダイアログでは、右側にあるボタンを使ってメソッド シグネチャを変更できます。

   ![[シグネチャの変更] ダイアログ](media/changesignature-dialog-cs.png)

   | ボタン | 説明
   | ------ | ---
   | **上/下** | 選択したパラメーターを一覧内で上下に移動します
   | **削除**  | 選択したパラメーターを一覧から削除します
   | **復元** | 選択した、取り消したパラメーターを一覧に復元します

   > [!TIP]
   > [**[参照の変更のプレビュー]**](../../ide/preview-changes.md) チェックボックスを使用すると、コミットする前に、結果を確認できます。

1. 完了したら、**[OK]** ボタンをクリックして変更を実行します。

   ![シグネチャ変更の結果](media/changesignature-result-cs.png)

## <a name="see-also"></a>関連項目

[リファクタリング](../refactoring-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)