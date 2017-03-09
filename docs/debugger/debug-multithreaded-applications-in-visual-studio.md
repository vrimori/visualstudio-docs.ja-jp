---
title: "マルチスレッド アプリケーションのデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.gputthreads"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッグ [Visual Studio], 高パフォーマンス コンピューティング"
  - "デバッグ [Visual Studio], マルチスレッド"
  - "高パフォーマンス デバッグ"
  - "マルチスレッド デバッグ"
  - "スレッド処理 [Visual Studio], デバッグ"
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# マルチスレッド アプリケーションのデバッグ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

スレッドは、オペレーティング システムでプロセッサ時間を割り当てる命令のシーケンスです。  オペレーティング システムで実行されているプロセスは、いずれも 1 つ以上のスレッドで構成されます。  複数のスレッドで構成されるプロセスをマルチスレッド プロセスといいます。  
  
 複数のプロセッサ、マルチコア プロセッサ、またはハイパースレッディング プロセッサを搭載したコンピューターでは、同時に複数のスレッドを実行できます。  複数のスレッドを同時に実行すると、プログラムのパフォーマンスは大幅に向上しますが、複数のスレッドを追跡する必要があるため、デバッグは難しくなります。  
  
 また、マルチスレッドには新しい種類の潜在的な問題が伴います。  たとえば、複数のスレッドが同じリソースにアクセスする必要があり、一度に 1 つのスレッドだけがそのリソースに安全にアクセスできるということがよくあります。  一度に 1 つのスレッドだけがリソースにアクセスできるようにするには、相互排他を適用する必要があります。  相互排他が正しく適用されなければ、*デッドロック*状態が発生し、すべてのスレッドが実行不能になる可能性があります。  デッドロックは、デバッグが特に困難な問題の 1 つです。  
  
 Visual Studio の \[**スレッド**\] ウィンドウ、\[GPU スレッド\] ウィンドウ、\[並列ウォッチ\] ウィンドウ、その他の機能を使用すると、マルチスレッドのデバッグが容易になります。 スレッド機能の詳細について確認するには、チュートリアルを完了することをお勧めします。  「[チュートリアル : マルチスレッド アプリケーションのデバッグ](../debugger/walkthrough-debugging-a-multithreaded-application.md)」および「[チュートリアル : C\+\+ AMP アプリケーションのデバッグ](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)」をご覧ください。  
  
 Visual Studio には、強力なブレークポイントとトレースポイントも用意されており、マルチスレッド アプリケーションのデバッグに役立ちます。  ブレークポイント フィルターを使用すると、個々のスレッドにブレークポイントを配置できます。  「[ブレークポイントの使用](../debugger/using-breakpoints.md)」をご覧ください。  
  
 ユーザー インターフェイスを含むマルチスレッド アプリケーションは、特にデバッグが困難になることがあります。  その場合には、アプリケーションを別のコンピューターで実行し、リモート デバッグを使用することを検討してください。  詳しくは、「[リモート デバッグ](../debugger/remote-debugging.md)」をご覧ください。  
  
## このセクションの内容  
 [スレッドとプロセスの操作](../debugger/debug-threads-and-processes.md)  
 スレッドとプロセスのデバッグの基本について説明します。  
  
 [プロセスのデバッグ](../debugger/debug-multiple-processes.md)  
 複数プロセスのデバッグ方法について説明します。  
  
 [方法 : \[スレッド\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Threads%20Window.md)  
 **\[スレッド\]** ウィンドウを使用してスレッドをデバッグする際に役立つ手順について説明します。  
  
 [方法 : デバッグ中に別のスレッドに切り替える](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 デバッグ コンテキストを別のスレッドに切り替える 3 つの方法について説明します。  
  
 [方法 : スレッドに対するフラグの設定と設定解除を行う](../Topic/How%20to:%20Flag%20and%20Unflag%20Threads.md)  
 デバッグ中に特に注意する必要のあるスレッドにマークまたはフラグを設定する方法について説明します。  
  
 [方法 : ネイティブ コードのスレッド名を設定する](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 **\[スレッド\]** ウィンドウに表示するスレッド名の設定方法について説明します。  
  
 [方法 : マネージ コードのスレッド名を設定する](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 **\[スレッド\]** ウィンドウに表示するスレッド名の設定方法について説明します。  
  
 [チュートリアル : マルチスレッド アプリケーションのデバッグ](../debugger/walkthrough-debugging-a-multithreaded-application.md)  
 [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] の方法に重点を置いてスレッドのデバッグ機能を紹介するガイド ツアーです。  
  
 [方法 : 高パフォーマンス クラスター上でデバッグする](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 パフォーマンスの高いクラスター上で実行されるアプリケーションをデバッグする方法について説明します。  
  
 [ネイティブ コード内のスレッドのデバッグのヒント](../debugger/tips-for-debugging-threads-in-native-code.md)  
 ネイティブ スレッドのデバッグに役立つ簡単な手法について説明します。  
  
 [\[タスク\] ウィンドウの使用](../Topic/Using%20the%20Tasks%20Window.md)  
 マネージまたはネイティブのすべてのタスク オブジェクトの一覧を、それらのステータス、およびその他の有益な情報を含めて表示します。  
  
 [\[並列スタック\] ウィンドウの使用](../Topic/Using%20the%20Parallel%20Stacks%20Window.md)  
 複数のスレッド \(またはタスク\) の呼び出し履歴を単一のビューに表示します。また、スレッド \(またはタスク\) で共通のスタック セグメントを結合します。  
  
 [チュートリアル: 並行アプリケーションのデバッグ](../debugger/walkthrough-debugging-a-parallel-application.md)  
 \[並列タスク\] ウィンドウと \[並列スタック\] ウィンドウの使用方法を示すチュートリアルです。  
  
 [方法: 並列ウォッチ ウィンドウを使用する](../debugger/how-to-use-the-parallel-watch-window.md)  
 複数のスレッド間で値と式を検査します。  
  
 [方法: GPU スレッド ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20GPU%20Threads%20Window.md)  
 デバッグ中に GPU 上で実行されているスレッドを調べて操作します。  
  
## 関連項目  
 [ブレークポイントの使用](../debugger/using-breakpoints.md)  
 -   個々のスレッドにブレークポイントを配置する場合にブレークポイント フィルターを使用する方法について説明します。  
  
-   トレースポイントを使用すると、プログラムの実行を中断なしでトレースできます。  この方法はデッドロックなどの問題を調べる場合に役立ちます。  
  
 [Threading](../Topic/Managed%20Threading.md)  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] プログラミングでのスレッドの概念についてコード例を示しながら説明します。  
  
 [コンポーネントのマルチスレッド](../Topic/Multithreading%20in%20Components.md)  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] コンポーネントでのマルチスレッドの使用方法について説明します。  
  
 [旧形式のコードのためのマルチスレッド サポート \(Visual C\+\+\)](/visual-cpp/parallel/multithreading/multithreading-support-for-older-code-visual-cpp)  
 MFC を使用する C\# プログラマを対象とし、スレッドの概念についてコード例を示しながら説明します。  
  
## 参照  
 [スレッドとプロセスの操作](../debugger/debug-threads-and-processes.md)   
 [リモート デバッグ](../debugger/remote-debugging.md)