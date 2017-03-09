---
title: "この継承では、&lt;type1&gt; &#39;&lt;typename1&gt;&#39; とその入れ子になった &lt;type2&gt; &#39;&lt;typename2&gt;&#39; の間で循環依存関係が発生します | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30907"
  - "bc30907"
helpviewer_keywords: 
  - "BC30907"
ms.assetid: 17d4f938-5895-4d33-943e-8abf0ceacdc9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# この継承では、&lt;type1&gt; &#39;&lt;typename1&gt;&#39; とその入れ子になった &lt;type2&gt; &#39;&lt;typename2&gt;&#39; の間で循環依存関係が発生します
継承構造の結果として、入れ子になったクラス間で循環依存の関係が生じます。つまり、2 つのクラスが相互に継承し合います。  
  
 次のコードによって、このエラー メッセージが生成される可能性があります。  
  
```  
Public Class c1 Inherits c3.c4 Public Class c2 End Class End Class Public Class c3 Inherits c1.c2 Public Class c4 End Class End Class  
```  
  
 前述のコードでは、クラス `c1` はクラス `c4` を継承しますが、`c4` は `c3` 内で入れ子になっていて、これは `c2` を継承し、さらにこれは `c1` 内で入れ子になっています。  
  
 **エラー ID:** BC30907  
  
### このエラーを解決するには  
  
-   継承構造を変更して、循環依存の関係をなくします。  
  
## 参照  
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)