---
title: "コンパイラ エラー CS0656 | Microsoft Docs"
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
  - "CS0656"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0656"
ms.assetid: e695280a-e75d-4e8c-aec2-1f3fb455544a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0656
コンパイラが必要とするメンバー 'object.member' がありません  
  
 次のいずれかの問題があります。  
  
-   インストールされている共通言語ランタイムが破損している。  
  
-   共通言語ランタイムにも存在する型を定義するアセンブリへの参照がある。 ただし、C\# コンパイラが予期する方法でアセンブリの型が定義されていない。  
  
 参照をチェックして、正しいバージョンの共通言語ランタイムを使用するように設定してください。