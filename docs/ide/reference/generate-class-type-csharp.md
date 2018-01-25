---
title: "クラスまたは型の生成 - コード生成 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: ebc361fe-d9b1-4c7a-ae28-5e71b5775460
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vsl.GenerateFromUsage
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 87ef385a7e9edf9f975eb579bfab292039d60fa2
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-class-or-type-in-c"></a>クラスまたは型の生成 (C#) #
**機能:** クラスまたは型のコードをすぐに生成できます。 

**条件:** 新しいクラスまたは型を導入し、自動的に適切に宣言したいとき。  

**理由:** クラスまたは型は使用する前に自分で宣言できますが、この機能ではクラスまたは型が自動的に生成されます。 

**方法:**

1. まだ存在しないクラスを使用したことを示す赤い波線がある行にカーソルを置きます。

   ![強調表示されたコード](media/class-highlight-cs.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップからオプションのいずれかを選択します。
   * **マウス**
     * 右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップからオプションのいずれかを選択します。
     * 赤い波線をポイントし、表示された ![電球](media/bulb-cs.png) アイコンをクリックします。
     * テキスト カーソルが既に赤の波線が表示されている行にある場合は、左余白に表示されている ![電球](media/bulb-cs.png) アイコンをクリックします。

   ![クラス生成のプレビュー](media/class-preview-cs.png)

   選択ツール | 説明
   --- | ---
   Generate class '*TypeName*' in new file\(クラス 'TypeName' を新しいファイルに生成\) | *TypeName* という名前のクラスを *TypeName*.cs/.vb という名前のファイルに作成します。
   Generate class '*TypeName*'\(クラス 'TypeName' の生成\) | *TypeName* という名前のクラスを現在のファイルに作成します。
   Generate nested class '*TypeName*'\(入れ子になったクラス 'TypeName' の生成\) | 現在のクラス内に入れ子になった *TypeName* という名前のクラスを作成します。
   新しい型の生成... | 指定したすべてのプロパティを持つ新しいクラスまたは構造体を作成します。

   >[!TIP]
   >プレビュー ウィンドウの下部にある [**[変更のプレビュー]** ](../../ide/preview-changes.md) リンクを使用すると、選択を行う前に、行われるすべての変更を確認できます。

1. **[新しい型の生成...]** 項目を選択した場合、ダイアログ ボックスがポップアップし、いくつかの追加操作を実行できます。

   ![型の生成](media/class-newtype-cs.png)

   選択ツール | 説明
   --- | ---
   アクセス | 型に *[既定]*、*[内部]*、または *[パブリック]* アクセスを設定します。
   種類 | *[クラス]* または *[構造体]* として設定できます。
   name | 変更できません。入力済みの名前になります。
   プロジェクト | ソリューションに複数のプロジェクトがある場合、クラス/構造体を置くプロジェクトを選択できます。
   ファイル名 | 新しいファイルを作成することも、既存のファイルに型を追加することもできます。

1. クラス/構造体と、その使用から推論されたコンストラクターが、自動的に作成されます。

   ![クラス生成の結果](media/class-result-cs.png)

## <a name="see-also"></a>関連項目

[コード生成](../code-generation-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)