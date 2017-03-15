---
title: "プロジェクトには既にアセンブリ &lt;assemblyidentity&gt; への参照が指定されています | Microsoft Docs"
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
  - "bc32208"
  - "vbc32208"
helpviewer_keywords: 
  - "BC32208"
ms.assetid: a9f73a2c-5135-4315-bf2c-710ef216095d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# プロジェクトには既にアセンブリ &lt;assemblyidentity&gt; への参照が指定されています
プロジェクトには既にアセンブリ \<assemblyidentity\> への参照が指定されています。 '\<filepath\>' への 2 番目の参照を追加することはできません。  
  
 プロジェクトが、同じアセンブリへの参照を複数作成しています。  
  
 アセンブリ ID には、アセンブリの名前、バージョン、公開キー \(存在する場合\)、およびカルチャが含まれます。  
  
 このエラーが発生する原因の 1 つは、元の参照とは異なるファイル パスによって別のアセンブリのコピーが参照されていることです。  
  
 **エラー ID:** BC32208  
  
### このエラーを解決するには  
  
-   2 番目の参照を削除します。 同じアセンブリを参照しているため、この参照は必要ありません。  
  
## 参照  
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [壊れた参照のトラブルシューティング](../ide/troubleshooting-broken-references.md)