---
title: Visual Studio でマルチ スレッド アプリケーションのデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 09/05/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 80618257e61356285d9b8c9c2bcf2a7a2e11e831
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279547"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>マルチスレッド アプリケーションのデバッグ
スレッドは、オペレーティング システムでプロセッサ時間を割り当てる命令のシーケンスです。 オペレーティング システムで実行されているプロセスは、いずれも 1 つ以上のスレッドで構成されます。 複数のスレッドで構成されるプロセスをマルチスレッド プロセスといいます。  
  
複数のプロセッサ、マルチコア プロセッサ、またはハイパースレッディング プロセッサを搭載したコンピューターでは、同時に複数のスレッドを実行できます。 複数のスレッドを同時に実行すると、プログラムのパフォーマンスは大幅に向上しますが、複数のスレッドを追跡する必要があるため、デバッグは難しくなります。  
  
また、マルチスレッドには新しい種類の潜在的な問題が伴います。 たとえば、複数のスレッドが同じリソースにアクセスする必要があり、一度に 1 つのスレッドだけがそのリソースに安全にアクセスできるということがよくあります。 一度に 1 つのスレッドだけがリソースにアクセスできるようにするには、相互排他を適用する必要があります。 相互排他が正しく実行しない場合は作成できます、*デッドロック*条件で実行できるスレッドはありません。 デッドロックは、デバッグが特に困難な問題の 1 つです。

Visual Studio には、マルチ スレッド アプリのデバッグで使用するためのさまざまなツールが用意されています。

- スレッドのデバッグの主なツールにはスレッドの場合、**スレッド**ウィンドウで、ソース ウィンドウ、スレッド マーカー**並列スタック**ウィンドウで、**並列ウォッチ**ウィンドウ、および**デバッグの場所**ツールバー。 詳細については、**スレッド**ウィンドウと**デバッグの場所**ツールバーを参照してください[チュートリアル: [スレッド] ウィンドウを使用してデバッグ](../debugger/how-to-use-the-threads-window.md)します。 使用する方法については、**並列スタック**と**並列ウォッチ**windows を参照してください[マルチ スレッド アプリケーションのデバッグの開始](../debugger/get-started-debugging-multithreaded-apps.md)します。 両方のトピックでは、スレッド マーカーを使用する方法を説明します。
  
- 使用するコード、[タスク並列ライブラリ (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)または[同時実行ランタイム](/cpp/parallel/concrt/concurrency-runtime/)、デバッグの主なツールは、**並列スタック**ウィンドウで、 **並列ウォッチ**ウィンドウ、および**タスク**ウィンドウ (、**タスク**ウィンドウには、JavaScript もサポートしています)。 最初に、次を参照してください。[チュートリアル: 並行アプリケーションのデバッグ](../debugger/walkthrough-debugging-a-parallel-application.md)と[チュートリアル: C++ AMP アプリケーションのデバッグ](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)します。 

- 主要なツールは、GPU でスレッドをデバッグするには、 **GPU スレッド**ウィンドウ。 参照してください[方法: GPU スレッド ウィンドウを使用して](../debugger/how-to-use-the-gpu-threads-window.md)します。  

- 主なツールには、プロセスの**プロセスにアタッチ** ダイアログ ボックスで、**プロセス**ウィンドウで、および**デバッグの場所**ツールバー。  
  
Visual Studio には、強力なブレークポイントとトレースポイントも用意されており、マルチスレッド アプリケーションのデバッグに役立ちます。 ブレークポイント条件およびフィルターを使用するには、個々 のスレッドにブレークポイントを配置します。 参照してください[ブレークポイントを使用して](../debugger/using-breakpoints.md)します。 
  
ユーザー インターフェイスを含むマルチスレッド アプリケーションは、特にデバッグが困難になることがあります。 その場合には、アプリケーションを別のコンピューターで実行し、リモート デバッグを使用することを検討してください。 詳しくは、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容
 [マルチ スレッド アプリケーションのデバッグの開始](../debugger/get-started-debugging-multithreaded-apps.md)します。  
 スレッドのデバッグの機能に重点を置いて、機能のガイド付きツアー、**並列スタック**ウィンドウと**並列ウォッチ**ウィンドウ。

 [スレッドとプロセスをデバッグするためのツール](../debugger/debug-threads-and-processes.md)  
 スレッドとプロセスをデバッグするためのツールの機能を一覧表示します。  
  
 [複数プロセスをデバッグする](../debugger/debug-multiple-processes.md)  
 複数プロセスのデバッグ方法について説明します。

 [チュートリアル: [スレッド] ウィンドウのデバッグ](../debugger/how-to-use-the-threads-window.md)します。  
 使用する方法のチュートリアル、**スレッド**ウィンドウと**デバッグの場所**ツールバー。 

 [チュートリアル: 並行アプリケーションをデバッグします。](../debugger/walkthrough-debugging-a-parallel-application.md)  
 使用する方法のチュートリアル、**並列スタック**と**タスク**windows。  
  
 [方法 : デバッグ中に別のスレッドに切り替える](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 デバッグ コンテキストを別のスレッドに切り替える 3 つの方法について説明します。  
  
 [方法 : スレッドに対するフラグの設定と設定解除を行う](../debugger/how-to-flag-and-unflag-threads.md)  
 デバッグ中に特に注意する必要のあるスレッドにマークまたはフラグを設定する方法について説明します。    
  
 [方法 : 高パフォーマンス クラスター上でデバッグする](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 パフォーマンスの高いクラスター上で実行されるアプリケーションをデバッグする方法について説明します。  

 [ネイティブ コード内のスレッドのデバッグのヒント](../debugger/tips-for-debugging-threads-in-native-code.md)  
 ネイティブ スレッドのデバッグに役立つ簡単な手法について説明します。 

 [方法 : ネイティブ コードのスレッド名を設定する](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 スレッドに表示される名前を付けて、**スレッド**ウィンドウ。  
  
 [方法 : マネージド コードのスレッド名を設定する](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 スレッドに表示される名前を付けて、**スレッド**ウィンドウ。 
  
## <a name="related-sections"></a>関連項目  
 [ブレークポイントの使用](../debugger/using-breakpoints.md)

 - 個別のスレッドをデバッグする場合は、ブレークポイント条件またはフィルターを使用します。  
  
 - トレースポイントを使用すると、プログラムの実行を中断なしでトレースできます。 この方法はデッドロックなどの問題を調べる場合に役立ちます。  
  
 [スレッド化](/dotnet/standard/threading/index)  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] プログラミングでのスレッドの概念についてコード例を示しながら説明します。  
  
 [コンポーネントのマルチスレッド](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] コンポーネントでのマルチスレッドの使用方法について説明します。  
  
 [旧形式のコードのためのマルチスレッド サポート (Visual C++)](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)  
 MFC を使用する C# プログラマを対象とし、スレッドの概念についてコード例を示しながら説明します。  
  
## <a name="see-also"></a>関連項目  
 [スレッドとプロセス](../debugger/debug-threads-and-processes.md)   
 [Remote Debugging](../debugger/remote-debugging.md)