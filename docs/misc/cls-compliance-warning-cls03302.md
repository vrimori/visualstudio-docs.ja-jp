---
title: "CLS 準拠の警告 CLS03302 | Microsoft Docs"
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
  - "CLS03302"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03302"
ms.assetid: 3b99e64b-d5cb-4eb8-81b5-fd96992f2c10
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS03302
イベントは、特定の名前付けパターンに従わなくてはいけない  
  
 イベントは、特定の名前付けパターンに従う必要があります。イベントのアクセサー関数の名前はイベント名と同じにします \(先頭に **raise\_**、**remove\_**、または **add\_** を付ける\)。  
  
 **specialname** 属性は、適切な名前比較で無視され、識別子規則に従う必要があります。  
  
 CLS 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 \(MSIL アセンブリ言語を使用した\) 次の関数の宣言では、CLS03302 の考えられる原因を示しています。  
  
```  
.method public specialname instance void add_MyEventaaa(class MyAssemblyDelegate __unnamed000) cil managed { } // end of method One::add_MyEvent .method public specialname instance void remove_MyEventaaa(class MyAssemblyDelegate __unnamed000) cil managed { } // end of method One::remove_MyEvent .method public specialname instance void raise_MyEventaaa(object __unnamed000, class [mscorlib]System.EventArgs __unnamed001) cil managed { } // end of method One::raise_MyEvent .event specialname MyAssemblyDelegate MyEvent { .addon instance void One::add_MyEventaaa(class MyAssemblyDelegate) .removeon instance void remove_MyEventaaa(class MyAssemblyDelegate) .fire instance void raise_MyEventaaa(object, class [mscorlib]System.EventArgs) } // end of event One::MyEvent } // end of class One  
```  
  
 アクセサー メソッドの名前が、イベントの名前と異なることに注意してください。  すべてのイベントのアクセサー名が必ず名前付けパターンに従うことにより CLS03302 を解決することができます。