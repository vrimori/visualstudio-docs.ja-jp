---
title: "コンパイラの警告 (レベル 1) CS3014 | Microsoft Docs"
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
  - "CS3014"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3014"
ms.assetid: 6825b42f-1820-4265-b8d8-9b3387d7c130
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS3014
アセンブリに CLSCompliant 属性が含まれていないため、'member' には CLSCompliant 属性が必要ありません。  
  
 共通言語仕様 \(CLS\) への準拠が指定されていないソース コード ファイルで、ファイル内の構成体が CLS 準拠としてマークされました。 これは認められていません。 この警告を解決するには、ファイルにアセンブリ レベルの CLS 準拠属性を追加します \(次の例では、アセンブリ レベル属性を含む行をコメント解除します\)。 CLS 準拠の詳細については、「[CLS準拠コードの記述](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)」および「[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)」を参照してください。  
  
## 使用例  
 次の例では、CS3014 が生成されます。  
  
```  
// CS3014.cs using System; // [assembly:CLSCompliant(true)] public class I { [CLSCompliant(true)]   // CS3014 public void M() { } public static void Main() { } }  
```