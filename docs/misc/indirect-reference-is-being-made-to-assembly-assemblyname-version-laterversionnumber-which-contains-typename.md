---
title: "&#39;&lt;typename&gt;&#39; を含むアセンブリ &lt;assemblyname&gt; のバージョン &lt;laterversionnumber&gt; に対して間接参照が行われています | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32207"
  - "bc32207"
helpviewer_keywords: 
  - "BC32207"
ms.assetid: a3de74b5-bedd-4e36-b379-485e4b3903f7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; を含むアセンブリ &lt;assemblyname&gt; のバージョン &lt;laterversionnumber&gt; に対して間接参照が行われています
'\<typename\>' を含むアセンブリ \<assemblyname\> のバージョン \<laterversionnumber\> に対して間接参照が行われています。 このプロジェクトは、\<assemblyname\> の以前のバージョンのバージョン \<earlierversionnumber\> を参照します。 '\<typename\>' を使用するには、バージョン \<laterversionnumber\> 以上の \<assemblyname\> への参照に置き換える必要があります。  
  
 式により、同じアセンブリの以前のバージョンを参照する別のプロジェクトを間接的に参照できます。  
  
 通常、アセンブリの最新バージョンのみを使用する必要があります。  
  
 **エラー ID:** BC32207  
  
### このエラーを解決するには  
  
1.  問題の型名を使用して、同じアセンブリを参照するプロジェクトを特定します。  
  
2.  他のプロジェクトが参照するアセンブリのバージョンを特定し、同じバージョンを参照するようにプロジェクトを変更します。  
  
## 参照  
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [壊れた参照のトラブルシューティング](../ide/troubleshooting-broken-references.md)