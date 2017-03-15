---
title: "コンパイラ エラー CS2021 | Microsoft Docs"
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
  - "CS2021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2021"
ms.assetid: 8379d77e-6586-4e43-9aab-7cdf3ffecf51
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS2021
ファイル名 'file' が長すぎるか無効です  
  
 C\# コンパイラに渡されるすべてのファイル名の長さは、`_MAX_PATH` \(Windows のヘッダー ファイルで定義されている\) を超えないようにする必要があります。 次の場合に、コンパイラはこのエラーを生成します。  
  
-   ファイル名 \(パスを含む\) が `_MAX_PATH` より長い。  
  
-   ファイル名に無効な文字が含まれている。  
  
-   ワイルドカードが許可されていないファイル名 \(リソース ファイル名など\) に、ワイルドカードが含まれている。