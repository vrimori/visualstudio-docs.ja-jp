---
title: "例外のトラブルシューティング : System.DivideByZeroException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DivideByZeroException クラス"
ms.assetid: ddc79201-3ba1-455f-8496-edaad792ccf1
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.DivideByZeroException
整数または 10 進値を 0 で除算しようとすると、<xref:System.DivideByZeroException> 例外がスローされます。  
  
## 関連するヒント  
 **除算を実行する前に、分母の値が 0 でないことを確認します。**  
 浮動小数点値を 0 で除算すると、IEEE 算術規則に従って、その結果は正の無限大、負の無限大、または非数 \(NaN\) になります。 浮動小数点演算で例外がスローされることはありません。  
  
## 参照  
 <xref:System.DivideByZeroException>   
 [Arithmetic Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators)   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)