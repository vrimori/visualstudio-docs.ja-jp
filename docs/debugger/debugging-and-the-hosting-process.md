---
title: "プロセスのデバッグとホスト | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "デバッグ [Visual Studio], ホスト プロセス"
  - "ホスト プロセス"
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# プロセスのデバッグとホスト
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio のホスト プロセスでは、デバッガーのパフォーマンスを向上させ、部分信頼のデバッグやデザイン時の式の評価など、新しいデバッガー機能が使用できるようになりました。 必要に応じてホスト プロセスを無効にすることもできます。 詳細については、「[方法 : ホスト プロセスを無効にする](../ide/how-to-disable-the-hosting-process.md)」を参照してください。 次のセクションでは、ホスト プロセスがある場合とない場合のデバッグの違いについて説明します。  
  
## 部分信頼のデバッグと ClickOnce のセキュリティ  
 部分信頼のデバッグにはホスト プロセスが必要です。 ホスト プロセスを無効にすると、**\[プロジェクトのプロパティ\]** の **\[セキュリティ\]** ページで部分信頼が有効になっている場合でも、部分信頼のデバッグは機能しません。 詳細については、次のトピックを参照してください。[方法 : ホスト プロセスを無効にする](../ide/how-to-disable-the-hosting-process.md) および[方法 : 部分信頼アプリケーションをデバッグする](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## デザイン時の式評価  
 デザイン時の式では、常にホスト プロセスが使用されます。**\[プロジェクトのプロパティ\]** でホスト プロセスを無効にすると、クラス ライブラリ プロジェクトでデザイン時の式の評価も無効になります。 他のプロジェクトの種類では、デザイン時の式の評価は無効になりません。 代わりに、Visual Studio で実際の実行可能ファイルが起動され、ホスト プロセスを使用せずにデザイン時の評価に使用されます。 この違いがあるため、結果も異なる可能性があります。  
  
## AppDomain.CurrentDomain.FriendlyName の違い  
 `AppDomain.CurrentDomain.FriendlyName` は、ホスト プロセスが有効かどうかによって異なる結果を返します。 ホスト プロセスを有効にして `AppDomain.CurrentDomain.FriendlyName` を呼び出すと、*app\_name*`.vhost.exe` が返されます。 ホスト プロセスを無効にして呼び出した場合は、*app\_name*`.exe` が返されます。  
  
## Assembly.GetCallingAssembly\(\).FullName の違い  
 `Assembly.GetCallingAssembly().FullName` は、ホスト プロセスが有効かどうかによって異なる結果を返します。 ホスト プロセスを有効にして `Assembly.GetCallingAssembly().FullName` を呼び出すと、`mscorlib` が返されます。 ホスト プロセスを無効にして `Assembly.GetCallingAssembly().FullName` を呼び出すと、アプリケーション名が返されます。  
  
## 参照  
 [ホスト プロセス \(vshost.exe\)](../ide/hosting-process-vshost-exe.md)   
 [方法 : 部分信頼アプリケーションをデバッグする](../debugger/how-to-debug-a-partial-trust-application.md)   
 [方法 : ホスト プロセスを無効にする](../ide/how-to-disable-the-hosting-process.md)