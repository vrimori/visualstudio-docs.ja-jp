---
title: "検索式の高度な検索演算子 | Microsoft Docs"
ms.custom: 
ms.date: 06/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 07ff2413503209d6ade252ac89dbfbe2589e7e85
ms.openlocfilehash: 7ad9c78134c337445a3e9180ad27234b7bcb07cc
ms.contentlocale: ja-jp
ms.lasthandoff: 06/02/2017

---
# <a name="advanced-search-operators-in-search-expressions"></a>検索式の高度な検索演算子
ヘルプ ビューアーで高度な検索演算子を使用すると、より単純な検索式からより複雑な検索式を作成し、コンテンツの検索を絞り込むことができます。 次の表にあるとおり、演算子はクエリが実行されるコンテキストを制限します。  

> [!WARNING]
>  高度な検索演算子を入力するときは、検索エンジンに認識させるために最後にコロンを付け、コロンの前にはスペースを入れません。  

|検索対象|用途|例|結果|  
|-------------------|---------|-------------|------------|  
|トピックのタイトルの言葉|title:|title:binaryreader|タイトルに "binaryreader" が含まれるトピック。|  
|コード サンプルの言葉|code:|code:readdouble|コード サンプルに "readdouble" が含まれるトピック。|  
|特定のプログラミング言語のサンプルの言葉|code:vb:|code:vb:string|Visual Basic サンプルに "string" が含まれるトピック。|  
|特定のインデックス キーワードに関連付けられているトピック。|keyword:|keyword:readbyte|"readbyte" というインデックス キーワードに関連付けられているトピック。|  

 code: 演算子を利用して任意のいくつかのプログラミング言語に関するコンテンツを検索できますが、特定のプログラミング言語でマークアップされているコンテンツのみ、結果が返されます。 次の表は、この演算子が対応しているプログラミング言語を一覧にまとめたものです。  

|プログラミング言語|用途|  
|--------------------------|---------|  
|Visual Basic|code:vb<br /><br /> または<br /><br /> code:visualbasic|  
|C#|code:c#<br /><br /> または<br /><br /> code:csharp|  
|C++|code:cpp<br /><br /> または<br /><br /> code:c++<br /><br /> または<br /><br /> code:cplusplus|  
|F#|code:f#<br /><br /> または<br /><br /> code:fsharp|  
|JavaScript|code:javascript<br /><br /> または<br /><br /> code:js|  
|XAML|code:xaml|  

## <a name="see-also"></a>関連項目  
 [検索式の論理演算子](../ide/logical-operators-in-search-expressions.md)   
 [フルテキスト検索のヒント](../ide/full-text-search-tips.md)

