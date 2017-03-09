---
title: "オプション /win32manifest が無視されました | Microsoft Docs"
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
  - "vbc2034"
  - "bc2034"
helpviewer_keywords: 
  - "BC2034"
ms.assetid: 8009553a-f6ba-4d2b-8ddd-8a9357bc928e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# オプション /win32manifest が無視されました
オプション \/win32manifest が無視されました。 このオプションはターゲットがアセンブリのときにのみ指定できます。  
  
 `/target` オプションが `module` に設定された時点で、Visual Basic コンパイラには `/win32manifest` コンパイラ オプションが既に渡されていました。  
  
 **エラー ID:** BC2034  
  
### このエラーを解決するには  
  
1.  `/win32manifest` コンパイラ オプションを削除するか、または `/target` オプションを `exe`、`winexe`、`library` のいずれかに設定します。  
  
## 参照  
 [\/target](/dotnet/visual-basic/reference/command-line-compiler/target)   
 [\/win32manifest](/dotnet/visual-basic/reference/command-line-compiler/win32manifest)   
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)