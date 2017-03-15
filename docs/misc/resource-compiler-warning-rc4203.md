---
title: "リソース コンパイラの警告 RC4203 | Microsoft Docs"
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
  - "RC4203"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC4203"
ms.assetid: f0547f65-3f6e-4105-86a0-69e66c2dfdae
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# リソース コンパイラの警告 RC4203
VIRTKEY が指定されずに Shift キーまたは Ctrl キーが使用されています  
  
 アクセラレータ テーブル リソース内では、Shift キーや Ctrl キーには VIRTKEY を指定する必要があります。 Shift キーと Ctrl キーは VIRTKEY 型のアクセラレータの中でフラグ ビットとして示されるため、VIRTKEY から独立して存在することはできません。