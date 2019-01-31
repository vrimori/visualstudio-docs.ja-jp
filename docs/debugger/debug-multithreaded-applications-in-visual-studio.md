---
title: マルチ スレッド アプリケーションのデバッグ |Microsoft Docs
ms.custom: seodec18
ms.date: 11/06/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8158444662b7e0b2f7eb90d4ec5919314489dfc1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960604"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Visual Studio でマルチスレッド アプリケーションをデバッグする
スレッドは、オペレーティング システムがプロセッサ時間を許可する命令のシーケンスです。 オペレーティング システムで実行されているプロセスは、いずれも 1 つ以上のスレッドで構成されます。 複数のスレッドで構成されるプロセスをマルチスレッド プロセスといいます。  
  
複数のプロセッサ、マルチコア プロセッサ、またはハイパースレッディングでコンピューターには、複数の同時スレッドを実行できます。 プログラムのパフォーマンスを大幅に改善できる多数のスレッドを使用して並列処理しますが、その可能性がありますもデバッグをより困難多数のスレッドを追跡しているため。  
  
マルチ スレッドは、新しい種類の潜在的なバグを導入できます。 たとえば、2 つまたは複数のスレッドが同じリソースにアクセスする必要がありますが、一度に 1 つのスレッドがリソースを安全にアクセスできます。 相互排他のいくつかの形式は、1 つのスレッドがいつでもリソースにアクセスすることを確認する必要があります。 相互排他が正しく実装されていない場合は作成できます、*デッドロック*条件はいるスレッドは実行されません。 デッドロックは、デバッグする困難な問題ではよくあります。

## <a name="tools-for-debugging-multithreaded-apps"></a>マルチ スレッド アプリケーションをデバッグするためのツール

Visual Studio には、マルチ スレッド アプリのデバッグで使用するためのさまざまなツールが用意されています。

- スレッドのデバッグの主なツールにはスレッドの場合、**スレッド**ウィンドウで、ソース ウィンドウ、スレッド マーカー、**並列スタック**ウィンドウで、**並列ウォッチ**ウィンドウ、および**デバッグの場所**ツールバー。 詳細については、**スレッド**ウィンドウと**デバッグの場所**ツールバーを参照してください[チュートリアル。[スレッド] ウィンドウを使用してデバッグする](../debugger/how-to-use-the-threads-window.md) 使用する方法については、**並列スタック**と**並列ウォッチ**windows を参照してください[マルチ スレッド アプリケーションのデバッグの開始](../debugger/get-started-debugging-multithreaded-apps.md)します。 両方のトピックでは、スレッド マーカーを使用する方法を説明します。
  
- 使用するコード、[タスク並列ライブラリ (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)または[同時実行ランタイム](/cpp/parallel/concrt/concurrency-runtime/)、デバッグの主なツールは、**並列スタック**ウィンドウで、 **並列ウォッチ**ウィンドウ、および**タスク**ウィンドウで、JavaScript もサポートしています。 最初に、次を参照してください。[チュートリアル。並列アプリケーションのデバッグ](../debugger/walkthrough-debugging-a-parallel-application.md)と[チュートリアル。C++ AMP アプリケーションのデバッグ](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)します。 

- 主要なツールは、GPU でスレッドをデバッグするには、 **GPU スレッド**ウィンドウ。 「[方法: GPU スレッド ウィンドウを使用する](../debugger/how-to-use-the-gpu-threads-window.md)」を参照してください。  

- 主なツールには、プロセスの**プロセスにアタッチ** ダイアログ ボックスで、**プロセス**ウィンドウで、および**デバッグの場所**ツールバー。  
  
Visual Studio も提供します強力なブレークポイントとトレース ポイント、マルチ スレッド アプリケーションをデバッグするときに便利なをすることができます。 ブレークポイント条件およびフィルターを使用して、個々 のスレッドにブレークポイントを設定します。 トレース ポイント、プログラムの実行をトレースするデッドロックなどの問題を調査する互換性に影響せず、できます。 詳細については、次を参照してください。[ブレークポイント アクションとトレース ポイント](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)します。

ユーザー インターフェイスを含むマルチスレッド アプリケーションは、特にデバッグが困難になることがあります。 2 番目のコンピューターでアプリケーションを実行し、リモート デバッグの使用を検討する可能性があります。 詳細については、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)します。  
  
## <a name="articles-about-debugging-multithreaded-apps"></a>マルチ スレッド アプリのデバッグに関する情報の記事

 [マルチ スレッド アプリケーションのデバッグの開始します。](../debugger/get-started-debugging-multithreaded-apps.md)   
 スレッドのデバッグの機能に重点を置いた機能ツアー、**並列スタック**ウィンドウと**並列ウォッチ**ウィンドウ。

 [スレッドとプロセスをデバッグするためのツール](../debugger/debug-threads-and-processes.md)  
 スレッドとプロセスをデバッグするためのツールの機能を一覧表示します。  
  
 [複数プロセスをデバッグする](../debugger/debug-multiple-processes.md)  
 複数プロセスのデバッグ方法について説明します。

 [チュートリアル: [スレッド] ウィンドウを使用してデバッグする](../debugger/how-to-use-the-threads-window.md)  
 使用する方法のチュートリアル、**スレッド**ウィンドウと**デバッグの場所**ツールバー。 

 [チュートリアル: 並行アプリケーションをデバッグする](../debugger/walkthrough-debugging-a-parallel-application.md)  
 使用する方法のチュートリアル、**並列スタック**と**タスク**windows。  
  
 [方法: デバッグ中に別のスレッドに切り替える](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 別のスレッドに、デバッグ コンテキストを切り替えるいくつかの方法です。  
  
 [方法: スレッドに対するフラグの設定と設定解除を行う](../debugger/how-to-flag-and-unflag-threads.md)  
 デバッグ中に特に注意する必要のあるスレッドにマークまたはフラグを設定する方法について説明します。    
  
 [方法: 高パフォーマンス クラスター上でデバッグする](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 パフォーマンスの高いクラスター上で実行されるアプリケーションをデバッグする方法について説明します。  

 [ネイティブ コード内のスレッドのデバッグのヒント](../debugger/tips-for-debugging-threads-in-native-code.md)  
 ネイティブ スレッドのデバッグに役立つ簡単な手法について説明します。 

 [方法: ネイティブ コードのスレッド名を設定する](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 **[スレッド]** ウィンドウに表示するスレッド名の設定方法について説明します。  
  
 [方法: マネージド コードのスレッド名を設定する](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 **[スレッド]** ウィンドウに表示するスレッド名の設定方法について説明します。 
  
## <a name="see-also"></a>関連項目  

[ブレークポイントの使用](../debugger/using-breakpoints.md)  
[スレッド化](/dotnet/standard/threading/index)  
[コンポーネントのマルチスレッド](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
[旧形式のコードのためのマルチスレッド サポート (Visual C++)](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)  
 [スレッドとプロセスの操作](../debugger/debug-threads-and-processes.md)   
 [リモート デバッグ](../debugger/remote-debugging.md)