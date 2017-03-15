---
title: "リソース コンパイラ エラー RC2180 | Microsoft Docs"
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
  - "RC2180"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2180"
ms.assetid: 6d296138-7989-491e-a45b-6c3a4743116a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# リソース コンパイラ エラー RC2180
一時ファイルを開けません  
  
 リソース コンパイラまたは Visual C\+\+ は、一時ファイルを開くことができませんでした。 ディレクトリに対する書き込みアクセス許可がないか、ディレクトリが存在しないことが原因と考えられます。 リソース コンパイラまたは Visual C\+\+ が、**TMP** 環境変数で指定されたディレクトリ、または指定されていない場合は現在のディレクトリでこれらのファイルを使用しようとしています。