---
title: "ASP.NET アプリケーションおよび AJAX アプリケーションのデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッグ [ASP.NET], ASP.NET のデバッグの概要"
  - "デバッグ (ASP.NET Web アプリケーションを)"
  - "デバッグ, WCF"
  - "WCF, デバッグ"
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ASP.NET アプリケーションおよび AJAX アプリケーションのデバッグ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションのデバッグ方法は、Windows フォームなど、他の Windows アプリケーションの場合と似ています。どちらのアプリケーションも、コントロールとイベントが関係するためです。  ただし、これらのアプリケーションには基本的な違いもあります。  
  
-   状態の追跡は、Web アプリケーションの方が複雑です。  
  
-   Windows アプリケーションでは、ほとんどの場合、デバッグ対象のコードは 1 か所にあります。Web アプリケーションでは、クライアント側とサーバー側の両方に存在することがあります。  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] コードはすべてサーバーにありますが、クライアント側に JavaScript や [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コードが存在することがあります。  
  
## このセクションの内容  
 [ASP.NET のデバッグの準備](../debugger/preparing-to-debug-aspnet.md)  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションのデバッグを有効にするために必要な手順について説明します。  
  
 [Web アプリケーションのデバッグ](../debugger/debugging-web-applications.md)  
 AJAX 対応のスクリプト アプリケーションなどの [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションをデバッグする方法について説明します。  
  
## 関連項目  
 [デバッガーでの例外の管理](../debugger/managing-exceptions-with-the-debugger.md)  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] の例外のデバッグ時に "マイ コードのみ" を有効にする必要がある理由について説明します。  
  
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md)  
 AJAX コードをデバッグするのに役立つ方法とツールについて説明します。  
  
 [IntelliTrace の使用](../debugger/intellitrace.md)  
 アプリケーションの状態の履歴を記録して確認する IntelliTrace を使用することで、アプリケーションの頻繁な再起動がなくなり、コードのデバッグ時間を短縮します。  アプリケーションの実行中に発生するイベントや呼び出しに関する情報を確認し、それらのポイントに合わせてデバッグを開始することができます。  Visual Studio Ultimate が必要です。  
  
## 参照  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [Web アプリケーションとスクリプトのデバッグ](../debugger/debugging-web-applications-and-script.md)   
 [デバッグの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [デバッガーの基本事項](../debugger/debugger-basics.md)