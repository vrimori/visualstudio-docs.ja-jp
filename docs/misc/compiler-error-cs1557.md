---
title: "コンパイラ エラー CS1557 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1557"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1557"
ms.assetid: 1615e028-aeb7-4788-bd87-8e49e502d698
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1557
'class' は別の出力ファイルに含まれているため、Main メソッドに対して使うことはできません。  
  
 複数の出力ファイル コンパイルで 1 つの出力ファイルに関して [\/main](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) コンパイラ オプションが指定されました。 しかし、\/main コンパイルのソース コードでクラスが見つからず、コンパイルの他のいずれかの出力ファイルのソース コード ファイルで見つかりました。