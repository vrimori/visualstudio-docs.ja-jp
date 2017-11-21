---
title: "Field - リファクタリング (c#) をカプセル化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 39a9ed11-363f-4dda-af3b-0affe6db1d42
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.encapsulatefield
dev_langs: csharp
ms.openlocfilehash: f934d33d2c7bdc698b00305f3c86f904eae99e33
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="encapsulate-a-field-in-c"></a>C# でのフィールドのカプセル化します。 #
**新機能:**がプロパティにフィールドを有効にして、新しく作成されたプロパティを使用するには、そのフィールドのすべての使用状況を更新することができます。

****プロパティ、フィールドに移動し、そのフィールドにすべての参照を更新します。  

**理由:**フィールドに他のクラスのアクセスを許可しますが、直接アクセスする権限がこれらのクラスをしたくないです。  プロパティ内のフィールドをラップすることによって割り当てられる値を検証するコードを記述することもできます。

**どう：**

1. 強調表示またはカーソルを置き、テキスト内をカプセル化するフィールドの名前。

   ![強調表示されたコード](media/encapsulate_highlight.png)

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + R**、し**Ctrl キーを押しながら E キーを押し**です。  選ばれているプロファイルによってキーボード ショートカットが異なる場合があることに注意してください。
     * キーを押して**Ctrl + です。** トリガーを**クイック アクションとリファクタリング** メニューのいずれかを選択し、**フィールドのカプセル化**プレビュー ウィンドウのポップアップからのエントリ。
   * **マウス**
     * 選択**編集 > リファクター > フィールドをカプセル化**です。
     * コードを右クリックし、選択、**クイック アクションとリファクタリング** メニューのいずれかを選択して**フィールドのカプセル化**プレビュー ウィンドウのポップアップからのエントリ。

   選択ツール | 説明
   --------- | -----------
   **フィールドのカプセル化 (およびプロパティを使用)** | プロパティ、フィールドをカプセル化し、生成されるプロパティを使用するフィールドのすべての使用状況の更新
   **フィールドのカプセル化 (ただし、まだフィールドを使用)** | プロパティ、フィールドをカプセル化がフィールドのすべての使用状況を手を加えずに残ります

   プロパティはすぐに作成されたおよび選択されている場合、フィールドへの参照に更新されます。

   > [!TIP]
   > 使用して、 [**変更のプレビュー** ](../../ide/preview-changes.md)にコミットする前に、結果を確認するポップアップ ウィンドウにリンクします。

   ![プロパティの結果をカプセル化します。](media/encapsulate_result.png)

## <a name="see-also"></a>関連項目  
[リファクタリング (C#)](../refactoring-csharp.md)  
[変更のプレビュー](../../ide/preview-changes.md)