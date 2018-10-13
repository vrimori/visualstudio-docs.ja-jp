---
title: 検索式の高度な検索演算子 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 706d6d89d46a1e5db4f94c2e7d5e35ace73e1bac
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178003"
---
# <a name="advanced-search-operators-in-search-expressions"></a>検索式の高度な検索演算子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

高度な検索演算子を使用すると、単純なからより複雑な検索式を作成してコンテンツの検索を調整できます。 次の表にあるとおり、演算子はクエリが実行されるコンテキストを制限します。  
  
> [!WARNING]
>  高度な検索演算子を入力するときは、検索エンジンに認識させるために最後にコロンを付け、コロンの前にはスペースを入れません。  
  
|検索対象|使用|例|結果|  
|-------------------|---------|-------------|------------|  
|トピックのタイトルの言葉|title:|title:binaryreader|タイトルに"binaryreader"が含まれているトピック。|  
|コード サンプルの言葉|code:|code:readdouble|コード サンプルに "readdouble" が含まれるトピック。|  
|特定のプログラミング言語のサンプルの言葉|code:vb:|code:vb:string|Visual Basic の例では、"string"が含まれるトピック。|  
|特定のインデックス キーワードに関連付けられているトピック。|keyword:|keyword:readbyte|"Readbyte という"インデックス キーワードに関連付けられているトピック。|  
  
 code: 演算子を利用して任意のいくつかのプログラミング言語に関するコンテンツを検索できますが、特定のプログラミング言語でマークアップされているコンテンツのみ、結果が返されます。 次の表は、この演算子が対応しているプログラミング言語を一覧にまとめたものです。  
  
|プログラミング言語|使用|  
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



