---
title: "クライアント側スクリプトのデバッグ | Microsoft Docs"
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
  - "デバッグ [Visual Studio]、クライアント側のスクリプト"
  - "クライアント側のスクリプト、デバッグ"
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# クライアント側スクリプトのデバッグ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio デバッガーには、ASP.NET ページ内のクライアント側スクリプトのエラーを検出および修正するための包括的なデバッグ環境が用意されています。  
  
## スクリプト ドキュメントを開く  
 **ソリューション エクスプローラー**では、閲覧できるサーバー側およびクライアント側のスクリプト ドキュメントのリストを表示できます。**ソリューション エクスプローラー**で、任意のスクリプト ドキュメントを開くことができます。 詳細については、「[方法 : スクリプト ドキュメントを表示する](../debugger/how-to-view-script-documents.md)」を参照してください。  
  
## ブレークポイントのマップ  
 Visual Studio では、サーバー側コードを直接デバッグすることはできませんが、サーバー側ファイルにブレークポイントを設定できます。 Visual Studio では、設定されたブレークポイントがクライアント側ファイルの対応する場所に自動的にマップされ、マップされたブレークポイントがクライアント側コードに作成されます。  
  
## 手動または自動によるスクリプトへのアタッチ  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でスクリプトをデバッグするには、デバッグするスクリプトにデバッガーをアタッチする必要があります。 これは手動で行うことも、自動的に行うこともできます。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デバッガー インターフェイスを使用して、アタッチする実行中のスクリプト プロセスを選択することにより、手動でアタッチできます。 詳細については、「[方法 : スクリプトにアタッチする](../debugger/how-to-attach-to-script.md)」を参照してください。  
  
 次のいずれかの状況が発生すると、デバッガーは自動的にスクリプトにアタッチされます。  
  
-   スクリプトに設定されているブレークポイントにヒットした。  
  
-   スクリプト コード内の VBScript `Stop` ステートメントまたは JScript `debugger` ステートメントにヒットした。  
  
-   ブラウザーまたはサーバーが、スクリプト内で構文エラーまたはランタイム エラーを検出した。 これが発生すると、ダイアログ ボックスが表示され、デバッグを開始できます。  
  
 手動でスクリプトにアタッチした場合、そのスクリプト プロセスは、何らかの理由で停止するまで、引き続き実行されます。**\[デバッグ\]** メニューの **\[中断\]** を選択することによって、プロセスを停止できます。  
  
 デバッガーが自動的にアタッチされると、スクリプトの実行は、ブレークポイント、`Stop` ステートメント、`debugger` ステートメント、またはエラーが発生した行、あるいは Internet Explorer でデバッグを開始するように選択した位置で停止します。  
  
 この時点で、通常のデバッガー機能を使用してデバッグを開始できます。 たとえば、**\[ステップ\]** コマンドを使用すると、コードを行単位で継続して実行できます。**\[呼び出し履歴\]** ウィンドウを使用して、スクリプトのフローの表示と制御を行うことができます。 変数ウィンドウまたは**イミディエイト** ウィンドウを使用して、変数およびプロパティの表示または変更を行うことができます。  
  
## スクリプト デバッグのための強化されたエラー メッセージ  
 Visual Studio では、一般的なスクリプトのデバッグ問題を示すエラー メッセージが強化されています。 これらのメッセージは、Internet Explorer に手動でアタッチした場合のみ表示されます。 Internet Explorer が自動的に開かれたときにエラー状態が検出される場合は、手動でアタッチするとエラー メッセージが表示されます。  
  
## AJAX スクリプト アプリケーションのデバッグ  
 AJAX 対応の Web アプリケーションではスクリプト コードを頻繁に使用するため、デバッグは困難になる可能性があります。 AJAX をデバッグする手法の詳細については、次を参照してください。  
  
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md)。  
  
## 参照  
 [ASP.NET アプリケーションおよび AJAX アプリケーションのデバッグ](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [スクリプト デバッグの制約](../debugger/limitations-on-script-debugging.md)   
 [ウィンドウ](../Topic/Variable%20Windows.md)   
 [イミディエイト ウィンドウ](../ide/reference/immediate-window.md)   
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md)