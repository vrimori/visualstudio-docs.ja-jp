---
redirect_url: /visualstudio/ide/logical-operators-in-search-expressions
ms.openlocfilehash: fe896af873197c95a4b226396e0b6333fdc40cfa
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2017
---
タイトル: "検索式の高度な検索演算子 | Microsoft Docs" ms.custom: "" ms.date: "06/02/2017" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-help-viewer" ms.tgt_pltfrm: "" ms.topic: "article" helpviewer_keywords: 
  - "ヘルプ ビューアー、検索 (キーワードの)"
  - "ヘルプ ビューアー、検索 (コードを)"
  - "ヘルプ ビューアー、検索 (コードをプログラミング言語別に)"
  - "ヘルプ ビューアー、検索 (タイトルを)"
  - "検索 (コードを) [ヘルプ ビューアー]"
  - "検索 (タイトルを) [ヘルプ ビューアー]" ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e caps.latest.revision: 9 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="advanced-search-operators-in-search-expressions"></a>検索式の高度な検索演算子
ヘルプ ビューアーで高度な検索演算子を使用すると、コンテンツの検索を絞り込むことができます。トピック内で検索語句を探す場所を指定します。 次の表は、利用できる 4 つの高度な検索演算子をまとめたものです。

|検索対象|用途|例|結果|  
|-------------------|---------|-------------|------------|  
|トピックのタイトルの言葉|title:|title:binaryreader|タイトルに "binaryreader" が含まれるトピック。|  
|コード サンプルの言葉|code:|code:readdouble|コード サンプルに "readdouble" が含まれるトピック。|  
|特定のプログラミング言語のサンプルの言葉|code:vb:|code:vb:string|Visual Basic コード サンプルに "string" が含まれるトピック。|  
|特定のインデックス キーワードに関連付けられているトピック。|keyword:|keyword:readbyte|"readbyte" というインデックス キーワードに関連付けられているトピック。|  

> [!WARNING]
>  高度な検索演算子を入力するときは、検索エンジンに認識させるために最後にコロンを付け、コロンの前にはスペースを入れません。    

## <a name="programming-languages-for-code-examples"></a>コード例のプログラミング言語
code: 演算子を利用して任意のいくつかのプログラミング言語に関するコンテンツを検索できますが、あるプログラミング言語ラベルでマークアップされているコンテンツのみ、結果が返されます。 特定のプログラミング言語に対して例を返すには、次のプログラミング言語値のいずれかを使用します。  

|プログラミング言語|検索演算子構文|  
|--------------------|---------|  
|Visual Basic|code:vb<br/>code:visualbasic|  
|C#|code:c#<br/>code:csharp|  
|C++|code:cpp<br/>code:c++<br/>code:cplusplus|  
|F#|code:f#<br/>code:fsharp|  
|JavaScript|code:javascript<br/>code:js|  
|XAML|code:xaml|
