---
title: "ローカル変数にコード生成 (c#) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1490d6ac-ed56-4d03-95db-c23f23cba70d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: c52a29cb3dd408dacb805479b9680873abb047d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="introduce-a-local-variable-in-c"></a>C# でのローカル変数を導入します。 #
**新機能:**すぐに既存の式を置換するローカル変数を生成することができます。

****簡単に再利用できるよう後で、ローカル変数を使用した場合のコードがあります。  

**理由:**でしたコピーして貼り付けるコードは、複数回、さまざまな場所で使用するが、1 回の操作を実行、ローカル変数に結果を格納およびローカル変数 throughought を使用する方がよいでしょう。 

**どう：**

1. 新しいローカル変数に代入する式を強調表示します。

   ![強調表示されたコード](media/local_highlight.png)

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + です。** トリガーを**クイック アクションとリファクタリング**メニュー **ローカル (のすべての出現数) を導入します '*式*' * * プレビュー ウィンドウのポップアップから場所*式*を強調表示されているコードに示します。
   * **マウス**
     * 右クリックし、選択、**クイック アクションとリファクタリング**メニュー **ローカル (のすべての出現数) を導入します '*式*' * * プレビュー ウィンドウのポップアップからここで*式*を強調表示されているコードに示します。
     * をクリックします ![電球](media/bulb.png) テキストのカーソルは赤の波線では、行に既に存在する場合、左余白に表示されるアイコン。

   ![ローカル プレビューを導入します。](media/local_preview.png)

   >[!TIP]
   >使用して、 [**変更のプレビュー** ](../../ide/preview-changes.md)をすべての選択内容を確定する前に行われる変更を表示するプレビュー ウィンドウの下部にあるリンクします。

1. ローカル変数は、その使用法から推論された型に自動的に作成されます。  入力することで、新しいローカル変数の新しい名前を付けます。

   ![ローカルの結果を導入します。](media/local_result.png)

   >[!NOTE]
   >使用することができます、 **.. のすべての出現しています.**メニュー オプションを選択した式が見つかると、強調表示されている具体的には、1 つだけでなくのすべてのインスタンスを置き換えます。

## <a name="see-also"></a>参照  
[コード生成 (C#)](../code-generation-csharp.md)  
[変更のプレビュー](../../ide/preview-changes.md) 
