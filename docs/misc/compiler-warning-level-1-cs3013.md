---
title: "コンパイラの警告 (レベル 1) CS3013 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3013"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3013"
ms.assetid: 00b3bbe1-f2a0-465c-be0e-1af700c5753d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS3013
追加されたモジュールは、アセンブリに一致するように CLSCompliant 属性と共に設定されなければなりません  
  
 [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) コンパイラ オプションを使用してコンパイルされたモジュールが、[\/addmodule](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option) を使用してコンパイルに追加されました。 ただし、このモジュールの共通言語仕様 \(CLS\) への準拠が、現在のコンパイルの CLS 状態と一致しません。  
  
 CLS 準拠は、モジュール属性で示されます。 たとえば、`[module:CLSCompliant(true)]` は、モジュールが CLS に準拠していることを示し、`[module:CLSCompliant(false)]` は、モジュールが CLS に準拠していないことを示します。 既定値は、`[module:CLSCompliant(false)]` です。 CLS の詳細については、「[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)」を参照してください。