---
title: "コンパイラの警告 (レベル 1) CS1687 | Microsoft Docs"
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
  - "CS1687"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1687"
ms.assetid: f65d184f-fa1d-45d7-be7d-f439f67bace4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS1687
ソース ファイルは、PDB 内で表せる 16,707,565 行の限界を超えているため、デバッグ情報は不正確になります  
  
 PDB とデバッガーには、ファイルのサイズの上限について、何らかの制限があります。 ソース ファイルが大きすぎる場合、その制限を超えるとデバッガーは正常に機能しません。 ユーザーは `#line hidden` を使用してそのファイルのデバッグ情報を生成されないようにするか、またはファイルを複数のファイルに分割してファイルを圧縮する方法を見つける必要があります。 大きなクラスを分割するには、`partial` キーワードを使用することをお勧めします。