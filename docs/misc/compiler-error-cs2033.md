---
title: "コンパイラ エラー CS2033 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS2033"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2033"
ms.assetid: edb5784a-5195-4f72-b73d-d1ec9ed3766e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS2033
同じ短いファイル名を使用している長いファイル名が既に存在するとき、短いファイル名 'filename' を作成することはできません  
  
 名前が 8 文字を超える任意の C\# ファイルをコンパイルします。 次に、最初に作成したファイルの名前から先頭の数文字を使って \(先頭の 6 文字に "~1" を付けるなど\)、別のファイルをコンパイルします。 2 回目のコンパイルで、このエラーが生成されます。  
  
 このエラーを解決するには、短い方のファイル名を変更して、長い方のファイル名と競合しないようにします。