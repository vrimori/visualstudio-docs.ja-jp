---
title: "/moduleassemblyname オプションは &#39;module&#39; 型のターゲットをビルドするときのみ指定できます | Microsoft Docs"
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
  - "bc2030"
  - "vbc2030"
helpviewer_keywords: 
  - "BC2030"
ms.assetid: 2ebc577b-3464-40cc-8788-9fc9d3b4f928
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /moduleassemblyname オプションは &#39;module&#39; 型のターゲットをビルドするときのみ指定できます
`/target` オプションが `module` 以外の値に設定されているのに、Visual Basic コンパイラに `/moduleassemblyname` コンパイラ オプションが渡されました。  
  
 **エラー ID:** BC2030  
  
### このエラーを解決するには  
  
1.  `/moduleassemblyname` コンパイラ オプションを削除するか、`/target` オプションを `module` に設定します。  
  
## 参照  
 [\/target](/dotnet/visual-basic/reference/command-line-compiler/target)   
 [\/moduleassemblyname](/dotnet/visual-basic/reference/command-line-compiler/moduleassemblyname)   
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)