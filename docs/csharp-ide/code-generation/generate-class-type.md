---
title: "クラスまたは型のコード生成 (c#) を生成します |Microsoft ドキュメント"
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
ms.openlocfilehash: b6825be5447718e47f7145b0b3b16ec6d0ee076c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-class-or-type-in-c"></a>クラスまたは型を生成する (C#) #
**新機能:**すぐにクラスまたは型のコードを生成することができます。 

****する新しいクラスまたは型を紹介し、自動的に正しく宣言します。  

**理由:**が、この機能は、クラスを生成または型が自動的には、使用する前に、クラスまたは型を宣言することができます。 

**どう：**

1. 行にカーソルを置いてがまだ存在しないクラスを使用したことを示す赤い波線がある場合。

   ![強調表示されたコード](media/class_highlight.png)

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + です。** トリガーを**クイック アクションとリファクタリング**メニューとウィンドウのプレビュー ポップアップからのオプションのいずれかを選択します。
   * **マウス**
     * 右クリックし、選択、**クイック アクションとリファクタリング**メニューとウィンドウのプレビュー ポップアップからのオプションのいずれかを選択します。
     * 赤の波線をポイントし、をクリックします ![電球](media/bulb.png) 表示されるアイコン。
     * をクリックします ![電球](media/bulb.png) テキストのカーソルは赤の波線では、行に既に存在する場合、左余白に表示されるアイコン。

   ![クラスのプレビューを生成します。](media/class_preview.png)

   選択ツール | 説明
   --- | ---
   クラスの生成*TypeName*' で新しいファイル | という名前のクラスを作成*TypeName*という名前のファイルで*TypeName*.cs または .vb
   クラスの生成*TypeName*' | という名前のクラスを作成*TypeName*現在のファイルです。
   入れ子になったクラスの生成*TypeName*' | という名前のクラスを作成*TypeName*現在のクラス内で入れ子にします。
   新しい型を生成してください. | すべてのプロパティを指定すると、新しいクラスまたは構造体を作成します。

   >[!TIP]
   >使用して、 [**変更のプレビュー** ](../../ide/preview-changes.md)をすべての選択内容を確定する前に行われる変更を表示するプレビュー ウィンドウの下部にあるリンクします。

1. 選択した場合、**新しい型を生成しています.**項目 ダイアログ ボックスがポップアップするいくつかの操作を実行することができます。

   ![型を生成します。](media/class_newtype.png)

   選択ツール | 説明
   --- | ---
   アクセス | セットの種類が*既定*、*内部*または*パブリック*アクセスします。
   種類 | これは、として設定できます。*クラス*または*構造体*です。
   名前 | これは変更できませんし、既に入力した名前になります。
   プロジェクト | ソリューションに複数のプロジェクトがある場合、クラス/構造体にする場所を選択できます。
   ファイル名 | 新しいファイルを作成することも、種類を既存のファイルを追加することができます。

1. クラス/構造体は、その使用法から推論コンス トラクターで自動的に作成されます。

   ![クラスの結果を生成します。](media/class_result.png)

## <a name="see-also"></a>関連項目  
[コード生成 (C#)](../code-generation-csharp.md)  
[変更のプレビュー](../../ide/preview-changes.md)