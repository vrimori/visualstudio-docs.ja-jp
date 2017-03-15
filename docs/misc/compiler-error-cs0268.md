---
title: "コンパイラ エラー CS0268 | Microsoft Docs"
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
  - "CS0268"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0268"
ms.assetid: a4faca71-8b4a-4f22-a89e-59d92ced48cb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0268
インポートされた型 'type' は無効です。 この型には循環する基底クラスの依存関係が含まれています。  
  
 このエラーは、別の言語からインポートされた型に、循環する基底クラスの依存関係が含まれている場合に発生します。 このような型は、C\# プログラムでは使用できません。 このエラーを解決するには、参照アセンブリまたはモジュールで他の言語からインポートされた型を確認します。