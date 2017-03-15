---
title: "JIT の最適化とデバッグ | Microsoft Docs"
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
  - "デバッグ [Visual Studio], 最適化されたコード"
  - "最適化されたコード, デバッグ"
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# JIT の最適化とデバッグ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

マネージ アプリケーションをデバッグするとき、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、既定で、ジャスト イン タイム \(JIT: Just\-In\-Time\) コードの最適化が省略されています。  JIT 最適化の省略とは、最適化されていないコードをデバッグすることを示します。  最適化されていないため、コードの実行速度はやや遅くなりますが、デバッグで操作できる内容はより詳細になります。  最適化されたコードをデバッグするのは困難であるため、最適化されたコードで発生するバグが、非最適化バージョンでは再現しないときにのみお勧めします。  
  
 JIT 最適化は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の **\[モジュールの読み込み中に JIT 最適化を抑制する\]** オプションで制御されます。  このオプションは、**\[オプション\]** ダイアログ ボックスの **\[デバッグ\]** ノードの下にある **\[全般\]** ページにあります。  
  
 **\[モジュールの読み込み中に JIT 最適化を抑制する\]** オプションをオフにすると、最適化された JIT コードをデバッグできます。ただし、最適化されたコードはソース コードとは一致しないため、デバッグ機能は制限されます。  そのため、**\[ローカル\]** や **\[自動変数\]** などのデバッガー ウィンドウには、最適化されていないコードで利用できるのと同じ情報が表示されないことがあります。  
  
 もう 1 つの重要な違いは、マイ コードのみを使用したデバッグの問題です。  マイ コードのみでデバッグすると、デバッガーでは、最適化されたコードはユーザー コードではないと見なされ、これらのコードはデバッグ中に表示されません。  このため、JIT の最適化されたコードをデバッグする場合でも、マイ コードのみをオフに切り替えるという選択肢も考えられます。  詳細については、「[ステップ実行をマイ コードのみに制限する](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)」を参照してください。  
  
 前述したように、モジュールを読み込むと、コードの **\[モジュールの読み込み中に JIT 最適化を抑制する\]** オプションではコードの最適化が省略されます。  実行中のプロセスにアタッチする場合、既に読み込まれ、JIT でコンパイルされ、最適化されているコードが含まれることがあります。  このようなコードの場合、**\[モジュールの読み込み中に JIT 最適化を抑制する\]** オプションの影響はありません。ただし、アタッチ後に読み込まれたモジュールには影響があります。  さらに、**\[モジュールの読み込み中に JIT 最適化を抑制する\]** オプションは、NGEN で作成された WinForms.dll などのモジュールには影響がありません。  
  
## 参照  
 [マネージ コードのデバッグ](../debugger/debugging-managed-code.md)   
 [デバッガーでのコード間の移動](../debugger/navigating-through-code-with-the-debugger.md)   
 [実行中のプロセスへのアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [マネージ実行プロセス](../Topic/Managed%20Execution%20Process.md)