---
title: "プロジェクト &#39;&lt;projectname&gt;&#39; にはアセンブリ &#39;&lt;assemblyname&gt;&#39; のバージョン &#39;&lt;versionnumber1&gt;&#39; への参照が必要ですが、アセンブリ &#39;&lt;assemblyname&gt;&#39; のバージョン &#39;&lt;versionnumber2&gt;&#39; を参照します (Visual Basic エラー) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32209"
  - "bc32209"
helpviewer_keywords: 
  - "BC32209"
ms.assetid: fe50736b-444f-4e40-8f80-9760ff13a153
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# プロジェクト &#39;&lt;projectname&gt;&#39; にはアセンブリ &#39;&lt;assemblyname&gt;&#39; のバージョン &#39;&lt;versionnumber1&gt;&#39; への参照が必要ですが、アセンブリ &#39;&lt;assemblyname&gt;&#39; のバージョン &#39;&lt;versionnumber2&gt;&#39; を参照します (Visual Basic エラー)
プロジェクトは、他の場所で定義されているアセンブリへの間接参照を行いますが、プロジェクトには、それ以降のバージョンのアセンブリへの直接参照も含まれています。  
  
 コンパイラが間接参照を使用するようコードを許可した場合、以前のバージョンではなく以降のバージョンで定義されている型およびプログラミング要素にアクセスすることはできません。  
  
 **エラー ID:** BC32209  
  
### このエラーを解決するには  
  
-   以前のバージョンのアセンブリへの間接参照を削除し、以降のバージョンへの直接参照を使用します。  
  
## 参照  
 [共通言語ランタイムのアセンブリ](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [NIB: 名前空間およびコンポーネントの参照](http://msdn.microsoft.com/ja-jp/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)   
 [NIB: 参照の管理](http://msdn.microsoft.com/ja-jp/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)