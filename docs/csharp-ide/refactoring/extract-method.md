---
title: "メソッドの抽出 - リファクタリング (c#) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: d79d55ae-f6bb-4902-8db2-e7fe01bdb0bf
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractmethod
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 44a5dd2da4cd19a532e8e6cc9f21ef48b2585fe4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="extract-a-method-in-c"></a>C# でのメソッドを抽出します。 #
**新機能:**独自のメソッドにコードのフラグメントを変換することができます。

****別のメソッドから呼び出される必要があるいくつかのメソッドに既存のコードのフラグメントがあります。  

**理由:**するでしたコピー/貼り付け、そのコードが重複につながることです。  他のメソッドを自由に呼び出すことができる、独自のメソッドにそのフラグメントをリファクタリングすることをお勧めします。

**どう：**

1. 抽出するコードを強調表示します。

   ![強調表示されたコード](media/extractmethod_highlight.png)

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + R**、し**Ctrl + M**です。  選ばれているプロファイルによってキーボード ショートカットが異なる場合があることに注意してください。
     * キーを押して**Ctrl + です。** トリガーを**クイック アクションとリファクタリング**メニュー**メソッドの抽出**プレビュー ウィンドウのポップアップからです。
   * **マウス**
     * 選択**編集 > リファクター > メソッドの抽出**です。
     * コードを右クリックし **リファクター > 抽出 > メソッドの抽出**です。
     * コードを右クリックし、選択、**クイック アクションとリファクタリング**メニュー**メソッドの抽出**プレビュー ウィンドウのポップアップからです。

   メソッドはすぐに作成されます。  ここでは、新しい名前を入力するだけでメソッドを今すぐ変更できます。

   > [!TIP]
   > コメントおよびこの新しい名前を使用するには、その他の文字列を更新することもだけでなく[変更のプレビュー](../../ide/preview-changes.md)保存前に、チェック ボックスを使用して、**の名前を変更**上部に表示されるボックス、IDE の右。

   ![メソッドの名前を変更します。](media/extractmethod_rename.png)

1. 変更に満足したら、をクリックして、**適用**ボタンまたはキーを押して**Enter**し、変更がコミットされます。

## <a name="see-also"></a>参照  
[リファクタリング (C#)](../refactoring-csharp.md)  
[変更のプレビュー](../../ide/preview-changes.md)