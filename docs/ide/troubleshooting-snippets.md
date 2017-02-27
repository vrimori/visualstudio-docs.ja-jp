---
title: "スニペットのトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense コード スニペット, トラブルシューティング"
  - "トラブルシューティング (IntelliSense コード スニペットの)"
  - "トラブルシューティング (Visual Basic), IntelliSense コード スニペット"
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# スニペットのトラブルシューティング
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

IntelliSense コード スニペットに伴う問題は、通常は 2 つの問題が原因で発生します。1 つはスニペット ファイルの破損、もう 1 つはスニペット ファイルの不適切な内容です。  
  
## 一般的な問題  
  
### スニペットは、ファイル エクスプローラーから Visual Studio のソース ファイルにドラッグすることはできません  
  
-   スニペット ファイルの XML が破損している可能性があります。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の **\[XML エディター\]** を使用すると、XML の構造の問題を特定できます。  
  
-   スニペット ファイルがスニペットのスキーマにのっとっていない可能性があります。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の **\[XML エディター\]** を使用すると、XML の構造の問題を特定できます。  
  
### コードに、強調表示されていないコンパイラ エラーがある  
  
-   プロジェクト参照が不足している可能性があります。  スニペットについてのドキュメントを調べてください。  参照がコンピューター上にない場合は、インストールする必要があります。  通常は、スニペットを挿入すると、必要な参照がプロジェクトに追加されます。  スニペットに参照情報がない場合は、スニペットの作成者に対して、エラーとして報告できます。  
  
-   変数が未定義の可能性があります。  通常は、スニペット内の未定義の変数は強調表示されます。  そうなっていない場合は、スニペットの作成者に対して、エラーとして報告できます。  
  
## 参照  
 [コード スニペット](../ide/code-snippets.md)