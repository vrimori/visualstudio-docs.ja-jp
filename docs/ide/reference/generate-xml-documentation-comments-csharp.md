---
title: "XML ドキュメントのコメントの生成 - コード生成 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2025bd2-5984-4486-a61c-0a0933a735ea
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: b0a0ec1db54f57e14ddd412248f7a396336fe009
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="generate-xml-documentation-comments-in-c"></a>XML ドキュメントのコメントの生成 (C#) #
**機能:** 選択した要素のドキュメント化に必要な、基本 XML をすぐに生成できます。 

**条件:** Sandcastle などのドキュメント ツールによって後で処理するために XML ドキュメント コメントを作成したいとき。

**理由:** 手動でコメント ブロック全体を作成できますが、基本テンプレートと追加要素を生成すると、時間の節約になり、精度が向上します。 

**方法:**

1. メソッドなど、ドキュメント化する要素の上にテキスト カーソルを置きます。

   ![ドキュメント化するメソッド](media/doc-highlight-cs.png)

1. 次に、**///** (3 つのスラッシュ) を入力します。これで、基本テンプレートと必要に応じて追加要素が自動生成されます。  たとえば、メソッドのコメントを記述するときに、**\<summary\>** タグ、メソッドに渡されるすべてのパラメーターの **\<param\>** タグ、メソッドが返す内容をドキュメント化する **\<returns\>** タグが生成されます。

   ![テンプレート](media/doc-preview-cs.png)

1. コメントを完了し、必要と思われるその他の情報を追加します。

   ![完了したコメント](media/doc-result-cs.png)

## <a name="see-also"></a>関連項目

[コード生成](../code-generation-in-visual-studio.md)  
[XML ドキュメント コメント (C# プログラミング ガイド)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
