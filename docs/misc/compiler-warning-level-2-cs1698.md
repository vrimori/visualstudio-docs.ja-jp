---
title: "コンパイラの警告 (レベル 2) CS1698 | Microsoft Docs"
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
  - "CS1698"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1698"
ms.assetid: 65cac5d0-e045-40f9-911c-1bf50e710b18
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 2) CS1698
循環アセンブリ参照 'AssemblyName1' は、出力アセンブリ名 'AssemblyName2' に対応していません。 'AssemblyName1' への参照を追加するか、または出力アセンブリ名が一致するように変更してください。  
  
 CS1698 は、アセンブリ参照が正しくない場合に発生します。 これは、参照アセンブリが再コンパイルされた場合に、発生する可能性があります。 解決するには、それ自体が、参照しているアセンブリの依存関係にあるアセンブリを置き換えないでください。  
  
## 使用例  
  
```  
// CS1698_a.cs // compile with: /target:library /keyfile:mykey.snk [assembly:System.Reflection.AssemblyVersion("2")] public class CS1698_a {}  
```  
  
## 使用例  
  
```  
// CS1698_b.cs // compile with: /target:library /reference:CS1698_a.dll /keyfile:mykey.snk public class CS1698_b : CS1698_a {}  
```  
  
## 使用例  
 次の例では CS1698 が生成されます。  
  
```  
// CS1698_c.cs // compile with: /target:library /out:cs1698_a.dll /reference:cs1698_b.dll /keyfile:mykey.snk // CS1698 expected [assembly:System.Reflection.AssemblyVersion("3")] public class CS1698_c : CS1698_b {} public class CS1698_a {}  
  
```