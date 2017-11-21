---
title: "XML ドキュメント コメント - コード生成 (Visual Basic) を生成します |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2025bd2-5984-4486-a61c-0a0933a735ea
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1291667c7acb47abe543d275549179abea0c8467
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="generate-xml-documentation-comments-in-visual-basic"></a>Visual Basic で XML ドキュメント コメントを生成します。
**新機能:**すぐに、選択した要素をドキュメントに XML が必要な情報を生成することができます。 

**** Sandcastle などのドキュメント ツールによって後で処理するための XML ドキュメント コメントを作成します。

**理由:**でした手動で全体のコメント ブロック自分で作成した、ただし、これは、時間を節約し、基本テンプレートと追加の要素を生成して精度を向上させます。 

**どう：**

1. メソッドなど、ドキュメント化要素の上、テキストのカーソルを置きます。

   ![ドキュメントにメソッド](media/doc_highlight.png)

1. 次に、入力**''** (3 つの一重引用符) が自動作成される基本テンプレートと他の要素に応じて。  たとえば、メソッドのコメントを記述するときに生成されます、 **\<概要\>**タグだけでなく、  **\<param\>** されているすべてのパラメーターのタグメソッドに渡されると**\<を返します\>**タグをドキュメントのメソッドが返されます。

   ![テンプレート](media/doc_preview.png)

1. コメントを完了し、必要と思われるその他の情報を追加します。

   ![完了したコメント](media/doc_result.png)

## <a name="see-also"></a>関連項目
[XML (Visual Basic) で、コードの説明](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)  
[コード生成 (Visual Basic)](../code-generation-vb.md) 