---
title: "CLS 準拠の警告 CLS02809 | Microsoft Docs"
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
  - "CLS02809"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02809"
ms.assetid: a6e7b8e5-1587-437e-9d07-8a32fc5c4842
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS02809
プロパティは、特定の名前付けパターンに従わなくてはいけない  
  
 プロパティは、特定の名前付けパターンに従う必要があります。プロパティのアクセサー関数の名前はプロパティ名と同じにします \(先頭に **get\_** または **set\_** を付ける\)。  
  
 **specialname** 属性は、適切な名前比較で無視され、識別子規則に従う必要があります。  
  
 CLS 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 \(MSIL アセンブリ言語を使用した\) 次の関数の宣言では、CLS02809 の考えられる原因を示しています。  
  
```  
.method public specialname instance void set_MyPropertya(int32 __unnamed000) cil managed { } // end of method One::set_MyProperty .method public specialname instance int32 get_MyPropertya() cil managed { } // end of method One::get_MyProperty .property instance int32 MyProperty() { .get instance int32 One::get_MyPropertya() .set instance void One::set_MyPropertya(int32) } // end of property One::MyProperty  
```  
  
 アクセサー メソッドの名前が、プロパティの名前と異なることに注意してください。  すべてのプロパティ名が必ず名前付けパターンに従うことにより CLS02809 を解決することができます。