---
title: "デバッグの準備 : ASP.NET Web アプリケーション | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "デバッグ [Visual Studio], Web アプリケーション"
  - "デバッグ (ASP.NET Web アプリケーションを)"
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# デバッグの準備 : ASP.NET Web アプリケーション
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] の Web サイト テンプレートを使用して Web フォーム アプリケーションを作成します。  このテンプレートを使用して Web サイトを作成する場合、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] はデバッグ用に既定の設定を作成します。  **\[プロジェクトのプロパティ\]** ダイアログ ボックスでは、Web ページをスタート ページにするかどうかを指定できます。  この既定の設定を使用して [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web サイトのデバッグを開始すると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は Internet Explorer を起動し、デバッガーを [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセス \(aspnet\_wp.exe または w3wp.exe\) にアタッチします。  詳細については、「[システム要件](../debugger/aspnet-debugging-system-requirements.md)」を参照してください。  
  
### Web フォーム アプリケーションを作成するには  
  
1.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、\[Web サイト\] をクリックします。  
  
2.  **\[新しい Web サイト\]** ダイアログ ボックスで、**\[[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web サイト\]** を選択します。  
  
3.  **\[OK\]** をクリックします。  
  
### Web フォームをデバッグするには  
  
1.  関数とイベント ハンドラーに 1 つ以上のブレークポイントを設定します。  
  
     詳細については、「[Breakpoints and Tracepoints](http://msdn.microsoft.com/ja-jp/fe4eedc1-71aa-4928-962f-0912c334d583)」を参照してください。  
  
2.  ブレークポイントに達したら、関数内のコードをステップ実行します。  問題が特定されるまでコードの実行を確認します。  
  
     詳細については、「[Stepping](http://msdn.microsoft.com/ja-jp/8791dac9-64d1-4bb9-b59e-8d59af1833f9)」および「[Web アプリケーションとスクリプトのデバッグ](../debugger/debugging-web-applications-and-script.md)」を参照してください。  
  
## 既定の構成の変更  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で作成された既定のデバッグ構成とリリース構成を変更する必要がある場合は、構成を変更できます。  詳細については、「[方法 : デバッグ構成とリリース構成を設定する](../debugger/how-to-set-debug-and-release-configurations.md)」を参照してください。  
  
#### 既定のデバッグ構成を変更するには  
  
1.  **ソリューション エクスプローラー**で Web サイトを右クリックし、**\[プロパティ ページ\]** をクリックして **\[プロパティ ページ\]** ダイアログ ボックスを開きます。  
  
2.  **\[開始オプション\]** をクリックします。  
  
3.  **\[開始動作\]** で、最初に表示する Web ページを設定します。  
  
4.  **\[デバッガー\]** で、**\[ASP.NET デバッグ\]** チェック ボックスがオンになっていることを確認します。  
  
     詳細については、「[Web プロジェクトのプロパティ ページ設定](../debugger/property-pages-settings-for-web-projects.md)」を参照してください。  
  
## 参照  
 [デバッグの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [デバッガーの基本事項](../debugger/debugger-basics.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [マネージ コードのデバッグ](../debugger/debugging-managed-code.md)