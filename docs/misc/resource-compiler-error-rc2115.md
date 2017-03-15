---
title: "リソース コンパイラ エラー RC2115 | Microsoft Docs"
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
  - "RC2115"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2115"
ms.assetid: 1b90feb0-f1fb-4f3c-8a9a-c44f9f8dc366
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# リソース コンパイラ エラー RC2115
コントロールにはテキスト文字列または序数が必要です  
  
 **DIALOG** ステートメント内の CONTROL ステートメントの *text* フィールドは、テキスト文字列か、コントロールの型への序数参照のいずれかである必要があります。 序数を使用する場合は、コントロールの `#define` ステートメントがあることを確認します。