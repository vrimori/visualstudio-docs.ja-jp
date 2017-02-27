---
title: "検索式の高度な検索演算子 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ヘルプ ビューアー 2.0, 検索 (コードを)"
  - "ヘルプ ビューアー 2.0, 検索 (コードをプログラミング言語別に)"
  - "ヘルプ ビューアー 2.0, 検索 (キーワードの)"
  - "ヘルプ ビューアー 2.0, 検索 (タイトルを)"
  - "検索 (コードを) [ヘルプ ビューアー 2.0]"
  - "検索 (タイトルを) [ヘルプ ビューアー 2.0]"
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# 検索式の高度な検索演算子
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

高度な検索演算子を使用すると、簡単な検索式からより複雑な検索式を作成することによって、コンテンツの検索を絞り込むことができます。  次の表に示すように、これらの演算子はクエリが実行されるコンテキストを制限します。  
  
> [!WARNING]
>  検索エンジンで認識されるように、高度な検索演算子は末尾にコロンを付け、コロンの前に間のスペースを入れずに入力する必要があります。  
  
|検索内容|使用|例|結果|  
|----------|--------|-------|--------|  
|トピックのタイトルに含まれる用語|title:|title:binaryreader|タイトルに「binaryreader」を含むトピック。|  
|コード例に含まれる用語|code:|code:readdouble|コード例に「readdouble」含むトピック。|  
|特定のプログラミング言語の例に含まれる用語|code:vb:|code:vb:string|Visual Basic の例に「string」を含むトピック。|  
|特定のインデックスのキーワードに関連付けられたトピック|keyword:|keyword:readbyte|インデックスのキーワード「readbyte」に関連付けられたトピック。|  
  
 code: 演算子を使用すると、複数のプログラミング言語に関するコンテンツを検索できますが、特定のプログラミング言語でマークされたコンテンツの結果のみが返されます。  次の表は、この演算子がサポートするプログラミング言語の一覧を示しています。  
  
|プログラミング言語|使用|  
|---------------|--------|  
|Visual Basic|code:vb<br /><br /> または<br /><br /> code:visualbasic|  
|C\#|code:c\#<br /><br /> または<br /><br /> code:csharp|  
|C\+\+|code:cpp<br /><br /> または<br /><br /> code:C\+\+<br /><br /> または<br /><br /> code:cplusplus|  
|F\#|code:f\#<br /><br /> または<br /><br /> code:fsharp|  
|JavaScript|code:javascript<br /><br /> または<br /><br /> code:js|  
|XAML|code:xaml|  
  
## 参照  
 [検索式の論理演算子](../ide/logical-operators-in-search-expressions.md)   
 [フルテキスト検索のヒント](../ide/full-text-search-tips.md)