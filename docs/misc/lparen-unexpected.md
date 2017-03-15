---
title: "&#39;(&#39; は無効です | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32095"
  - "bc32095"
helpviewer_keywords: 
  - "BC32095"
ms.assetid: a47ad15a-2cfc-4d17-9012-27ba85b7d783
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;(&#39; は無効です
'\(' は無効です。 インスタンス生成されないジェネリック型の配列は許可されていません。  
  
 特定のデータ型である場合を除き、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] は配列をコンパイルできません。 配列のデータ型としてジェネリック型のデータ型パラメーターを使用することはできません。  
  
 **エラー ID:** BC32095  
  
### このエラーを解決するには  
  
-   配列を使用する必要がある場合は、配列を特定のデータ型で宣言する必要があります。 データ型パラメーターを使用することはできません。  
  
-   データ型パラメーターに指定するデータ型の要素グループが必要な場合は、配列ではなくコレクションを使用する必要があります。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [NIB Visual Basic におけるコレクション](http://msdn.microsoft.com/ja-jp/8b2b7845-2251-4573-8dd3-c9f9c0a66a21)   
 [Visual Basic でのオブジェクトのグループ管理](http://msdn.microsoft.com/ja-jp/50be4910-4732-4d5f-a18a-055a162e9037)