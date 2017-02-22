---
title: "方法: Web アプリケーションをデバッグする | Microsoft Docs"
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
  - "ASP.NET Web フォーム, デバッグ"
  - "ASP.NET, デバッグ (Web アプリケーションを)"
  - "デバッグ (ASP.NET Web アプリケーションを), 開発中"
  - "Web サービス, デバッグ"
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法: Web アプリケーションをデバッグする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で Web アプリケーションを開発する際の主要なテクノロジです。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デバッガーには、ローカルまたはリモート サーバーで [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションをデバッグするための強力なツールが用意されています。  ここでは、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] プロジェクトを開発中にデバッグする方法について説明します。  運用サーバーに既に配置済みの [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションをデバッグする方法については、「[配置した Web アプリケーションのデバッグ](../debugger/debugging-deployed-web-applications.md)」を参照してください。  
  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションをデバッグするには  
  
-   適切なアクセス許可が必要です。  詳細については、「[システム要件](../debugger/aspnet-debugging-system-requirements.md)」を参照してください。  
  
-   [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] デバッグを **\[プロジェクトのプロパティ\]** で有効にしておく必要があります。  
  
-   アプリケーションの構成ファイル \(Web.config\) をデバッグ モードに設定する必要があります。  デバッグ モードの [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] では、動的に生成されたファイル用のシンボルが生成され、デバッガーの [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションへのアタッチが可能になります。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、プロジェクトを Web プロジェクト テンプレートから作成した場合は、デバッグ開始時にこの処理が自動的に実行されます。  
  
-   詳細については、「[方法 : .NET アプリケーションのデバッグを有効にする](../debugger/how-to-enable-debugging-for-aspnet-applications.md)」を参照してください。  
  
### 開発時に Web アプリケーションをデバッグするには  
  
1.  **\[デバッグ\]** メニューの **\[開始\]** をクリックして、Web アプリケーションのデバッグを開始します。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、Web アプリケーション プロジェクトのビルド、必要に応じたアプリケーションの配置、ローカルでデバッグしている場合に ASP.NET 開発サーバーの起動、および [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスへのアタッチを実行します。  
  
2.  デバッガーを使用して、ほかのアプリケーションの場合と同様に、ブレークポイントの設定と解除、ステップの実行、およびその他のデバッグ処理を行います。  
  
     詳細については、「[デバッガーの基本事項](../debugger/debugger-basics.md)」を参照してください。  
  
3.  デバッグ セッションを終了するには、**\[デバッグ\]** メニューの **\[デバッグの停止\]** をクリックするか、Internet Explorer の **\[ファイル\]** メニューの **\[閉じる\]** をクリックします。  
  
## 参照  
 [Web アプリケーションとスクリプトのデバッグ](../debugger/debugging-web-applications-and-script.md)   
 [ASP.NET アプリケーションおよび AJAX アプリケーションのデバッグ](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [方法 : .NET アプリケーションのデバッグを有効にする](../debugger/how-to-enable-debugging-for-aspnet-applications.md)