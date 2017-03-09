---
title: "[Microsoft Visual Studio デバッガー (例外がスローされました)] ダイアログ ボックス | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.exceptions.thrown"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "[Microsoft Visual Studio デバッガー (例外がスローされました)] ダイアログ ボックス"
  - "例外の処理、デバッグ中"
  - "デバッガー、例外"
  - "例外のスロー、デバッグ中"
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# [Microsoft Visual Studio デバッガー (例外がスローされました)] ダイアログ ボックス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プログラムに例外が発生しました。  このダイアログ ボックスには、スローされた例外の種類が報告されます。  コードでは、この例外を処理する必要があります。  この例外を処理するには、次のオプションから選択できます。  
  
 **Break**  
 デバッガーの実行を中断できます。  中断するまで、例外ハンドラーは起動されません。  中断した位置から継続すると、例外ハンドラーが起動されます。  
  
 **Continue**  
 実行が継続され、例外ハンドラーによって例外が処理されます。  このオプションは、特定の種類の例外に対しては使用できません。  **\[継続\]** によってアプリケーションは実行を継続できます。  ネイティブ アプリケーションでは、例外が再スローされます。  マネージ アプリケーションでは、プログラムが終了するか、または例外がホスト アプリケーションによって処理されます。  
  
> [!NOTE]
>  未処理の例外がマネージ コードで発生した後には実行を継続できません。  マネージ コードで未処理の例外が発生した後に **\[継続\]** をクリックすると、デバッグが停止します。  
  
 **Ignore**  
 実行が継続されますが、例外ハンドラーは起動されません。  例外ハンドラーが起動されないため、例外やエラーなどが続けて発生することがあります。  このオプションは、特定の種類の例外に対しては使用できません。  
  
## 参照  
 [デバッガーでの例外の管理](../debugger/managing-exceptions-with-the-debugger.md)   
 [例外の推奨事項](../Topic/Best%20Practices%20for%20Exceptions.md)   
 [Exception Handling](/visual-cpp/windows/exception-handling-cpp-component-extensions)