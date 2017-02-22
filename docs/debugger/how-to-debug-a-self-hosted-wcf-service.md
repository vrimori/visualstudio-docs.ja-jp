---
title: "方法 : セルフホストされている WCF サービスをデバッグする | Microsoft Docs"
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
  - "デバッグ, WCF"
  - "WCF, デバッグ"
  - "WCF, 自己ホスト サービス"
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : セルフホストされている WCF サービスをデバッグする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*セルフホストされているサービス*は、IIS 内部で実行されていない WCF サービス、WCF サービス ホスト、または [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 開発サーバーです。  セルフホストされている WCF をデバッグする最も簡単な方法は、**\[デバッグ\]** メニューの **\[デバッグ開始\]** をクリックしたときにクライアントとサーバーの両方を起動するよう、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を構成することです。  
  
 NT サービスなど、この方法で起動できないプロセス内部で WCF サービスがセルフホストされている場合、この手法は使用できません。  代わりに、次の方法のいずれかを使用できます。  
  
-   ホスト プロセスにデバッガーを手動でアタッチします。  詳細については、「[実行中のプロセスへのアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)」を参照してください。  
  
     または  
  
-   クライアントでデバッグを開始し、次にサービスへの呼び出しにステップ インします。  これを行うには、app.config ファイルでデバッグを有効にする必要があります。  詳細については、「[WCF デバッグの制約](../debugger/limitations-on-wcf-debugging.md)」を参照してください。  
  
### Visual Studio からクライアントとホストの両方を起動するには  
  
1.  クライアント プロジェクトとサーバー プロジェクトの両方を含む [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューションを作成します。  
  
2.  ソリューションを構成して、**\[デバッグ\]** メニューの **\[開始\]** をクリックしたときにクライアント プロセスとサーバー プロセスの両方を起動します。  
  
    1.  **ソリューション エクスプローラー**でソリューション名を右クリックします。  
  
    2.  **\[スタートアップ プロジェクトの設定\]** をクリックします。  
  
    3.  **\[ソリューション \<name\> プロパティ\]** ダイアログ ボックスで、**\[マルチ スタートアップ プロジェクト\]** を選択します。  
  
    4.  **\[マルチ スタートアップ プロジェクト\]** グリッドのサーバー プロジェクトに対応する行で、**\[アクション\]** をクリックし、**\[開始\]** を選択します。  
  
    5.  クライアント プロジェクトに対応する行で、**\[アクション\]** をクリックし、**\[開始\]** を選択します。  
  
    6.  **\[OK\]** をクリックします。  
  
## 参照  
 [WCF サービスのデバッグ](../debugger/debugging-wcf-services.md)   
 [WCF デバッグの制約](../debugger/limitations-on-wcf-debugging.md)   
 [方法 : WCF サービスにステップ インする](../debugger/how-to-step-into-wcf-services.md)