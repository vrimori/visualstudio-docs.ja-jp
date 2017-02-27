---
title: "[デバッグ セッションで実行可能] ダイアログ ボックス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.exefordebug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "実行可能ファイル、デバッグ時の指定"
  - "DLL, デバッグ"
  - "デバッガー、[デバッグ セッションで実行可能] ダイアログ ボックス"
  - "[デバッグ セッションで実行可能] ダイアログ ボックス"
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# [デバッグ セッションで実行可能] ダイアログ ボックス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このダイアログ ボックスは、ダイナミック リンク ライブラリ \(DLL: Dynamic\-Link Library\) をデバッグするときに、実行可能ファイルが指定されていない場合に表示されます。  Visual Studio では、DLL を直接起動できません。  代わりに、指定した実行可能ファイルが起動されます。  DLL は、実行可能ファイルから呼び出されたときにデバッグできます。  
  
 **\[実行可能ファイル名\]**  
 デバッグ中の DLL を呼び出す実行可能ファイルへのパス名を入力します。  
  
 **\[プロジェクトにアクセスする URL \(ATL Server のみ\)\]**  
 ATL Server の DLL をデバッグする場合は、プロジェクトが存在する URL を入力します。  
  
 URL を入力すると、これらの設定がプロジェクトの \[プロパティ ページ\] に格納されるため、後続のデバッグ セッションで設定を再入力する必要がなくなります。  設定変更が必要な場合は \[プロパティ ページ\] を開いて値を変更できます。  デバッグ セッションで実行可能ファイルを指定する方法の詳細については、「[DLL のデバッグ](../Topic/How%20to:%20Debug%20Native%20DLLs.md)」を参照してください。  
  
## 参照  
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)