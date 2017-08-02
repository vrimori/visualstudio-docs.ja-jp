---
title: "方法 : OnStart メソッドをデバッグする | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "OnStart メソッド"
  - "デバッグ [Visual Studio], Windows サービス"
  - "デバッグ (マネージ コードを), OnStart メソッド"
  - "デバッグ (Windows サービス アプリケーションを), OnStart メソッド"
  - "Windows サービス アプリケーション, デバッグ"
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : OnStart メソッドをデバッグする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows サービスをデバッグするには、サービスを起動し、デバッガーをサービス プロセスにアタッチします。 詳細については、「[方法 : Windows サービス アプリケーションをデバッグする](../Topic/How%20to:%20Debug%20Windows%20Service%20Applications.md)」を参照してください。 ただし、Windows サービスの <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> メソッドをデバッグするには、メソッド内部からデバッガーを起動する必要があります。  
  
1.  `OnStart()` メソッドの始めに、呼び出しを <xref:System.Diagnostics.Debugger.Launch%2A> に追加します。  
  
    ```c#  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2.  サービスを開始します \(`net start` を使うか、**\[サービス\]** ウィンドウで開始することができます\)。  
  
     次のようなダイアログ ボックスが表示されます。  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3.  **\[はい、\<サービス名\> をデバッグします\]** を選びます。  
  
4.  \[Just\-In\-Time デバッガー\] ウィンドウで、デバッグに使う Visual Studio のバージョンを選びます。  
  
     ![JustInTimeDebugger](~/debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  Visual Studio の新しいインスタンスが開始し、`Debugger.Launch()` メソッドで実行が停止します。  
  
## 参照  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [マネージ コードのデバッグ](../debugger/debugging-managed-code.md)