---
title: "フィールド、プロパティ、またはローカル - コード生成 (c#) を生成します |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c11888e0-31b1-44cc-9037-98d3f8b3623b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 85d15d28fae994f029e678183d2f08d561c70f1d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-field-property-or-local-in-c"></a>C# でのフィールド、プロパティ、またはローカルを生成します。 #
**新機能:**すぐに以前に宣言されていないフィールド、プロパティ、またはローカルのコードを生成することができます。 

****入力中に、新しいフィールド、プロパティ、またはローカルを導入して、自動的に正しく宣言します。  

**理由:**が、この機能は、宣言を生成し、自動的に入力し、使用する前に、フィールド、プロパティ、またはローカルを宣言することができます。 

**どう：**

1. 行にカーソルを置いて、ローカルのフィールドを使用したことを示す赤い波線やがまだ存在しないプロパティがある場合。

   ![強調表示されたコード](media/field_highlight.png)

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + です。** トリガーに、**クイック アクションとリファクタリング**メニュー**フィールド/プロパティ/ローカルの生成**プレビュー ウィンドウのポップアップからです。
   * **マウス**
     * 右クリックし、選択、**クイック アクションとリファクタリング**メニュー**フィールド/プロパティ/ローカルの生成**プレビュー ウィンドウのポップアップからです。
     * 赤の波線をポイントし、をクリックします ![電球](media/bulb.png) 表示されるアイコン。
     * をクリックします ![電球](media/bulb.png) テキストのカーソルは赤の波線では、行に既に存在する場合、左余白に表示されるアイコン。

   ![フィールド/プロパティ/ローカルのプレビューを生成します。](media/field_preview.png)

   >[!TIP]
   >使用して、 [**変更のプレビュー** ](../../ide/preview-changes.md)をすべての選択内容を確定する前に行われる変更を表示するプレビュー ウィンドウの下部にあるリンクします。

1. フィールド、プロパティ、またはローカルは、その使用法から推論された型に自動的に作成されます。

   ![フィールド/プロパティ/ローカルの結果を生成します。](media/field_result.png)

## <a name="see-also"></a>参照  
[コード生成 (C#)](../code-generation-csharp.md)  
[変更のプレビュー](../../ide/preview-changes.md) 
