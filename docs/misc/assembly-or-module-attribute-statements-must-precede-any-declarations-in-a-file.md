---
title: "Assembly または Module 属性ステートメントは、ファイル内では宣言の前に記述しなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30637"
  - "bc30637"
helpviewer_keywords: 
  - "BC30637"
ms.assetid: 80242581-fa8a-4903-9395-6f7ad1610231
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Assembly または Module 属性ステートメントは、ファイル内では宣言の前に記述しなければなりません
グローバル属性は、ソース ファイルの先頭で `Option` ステートメントと `Imports` ステートメントよりも後、かつその他のステートメントよりも前に宣言する必要があります。  
  
 **エラー ID:** BC30637  
  
### このエラーを解決するには  
  
1.  `<Module:>` や `<Assembly:>` などのグローバル属性をソース ファイルの先頭に配置します。  
  
## 参照  
 [ビルド内にありません: Visual Basic における属性](http://msdn.microsoft.com/ja-jp/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [ビルド内にありません: Visual Basic におけるグローバル属性](http://msdn.microsoft.com/ja-jp/253a32d8-1531-4504-b687-088554ab71d2)