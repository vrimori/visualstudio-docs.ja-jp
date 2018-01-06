---
title: "方法: 高パフォーマンス クラスター上でのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-perfomance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 18a8d66da62fd480934c750a6b809465022c5d6b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>方法 : 高パフォーマンス クラスター上でデバッグする
高パフォーマンス クラスター上でのマルチプロセス プログラムのデバッグは、リモート コンピューター上での通常のプログラムのデバッグと似ています。 ただし、追加の考慮事項がいくつかあります。 一般的なリモート セットアップ要件は、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)です。  
  
 高パフォーマンス クラスター上でデバッグするときは、リモート デバッグに使用できる [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のデバッグ ウィンドウとデバッグ手法をすべて使用できます。 ただし、リモートでデバッグするため、外部のコンソール ウィンドウは使用できません。  
  
 **スレッド**ウィンドウと**プロセス**ウィンドウは並列アプリケーションをデバッグするために特に役立ちます。 これらのウィンドウを使用する方法のヒントについては、次を参照してください。[する方法: [プロセス] ウィンドウを使用して](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)と[チュートリアル: [スレッド] ウィンドウを使用してデバッグ](../debugger/how-to-use-the-threads-window.md)です。  
  
 以下の手順では、高パフォーマンス クラスター上でのデバッグに特に役立つ手法を示します。  
  
 並列アプリケーションをデバッグするときは、特定のスレッド、プロセス、またはコンピューターにブレークポイントを設定することが必要になる場合があります。 これを行うには、通常のブレークポイントを作成してから、ブレークポイント フィルターを追加します。  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>[ブレークポイントのフィルター] ダイアログ ボックスを開くには  
  
1.  ソース ウィンドウでブレークポイント グリフを右クリックして、**逆アセンブル** ウィンドウで、**呼び出し履歴**ウィンドウで、または**ブレークポイント**ウィンドウです。  
  
2.  ショートカット メニューをクリックして**フィルター**です。 このオプションは、レベル、またはサブメニューで下の最上部に表示可能性があります**ブレークポイント**です。  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>特定のコンピューターにブレークポイントを設定するには  
  
1.  コンピューター名を取得、**プロセス**ウィンドウです。  
  
2.  ブレークポイントを選択し、開く、**ブレークポイント フィルター**  ダイアログ ボックスの前の手順に従ってします。  
  
3.  **ブレークポイント フィルター**ダイアログ ボックスで、種類。  
  
     MachineName =*yourmachinename*  
  
     より複雑なフィルターを作成する場合は、AND 演算子 (`&`)、OR 演算子 (`||`)、NOT 演算子 (`!`)、およびかっこを使って句を結合できます。  
  
4.  **[OK]**をクリックします。  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>特定のプロセスにブレークポイントを設定するには  
  
1.  このプロセスの名前を取得またはプロセス ID 番号を**プロセス**ウィンドウです。  
  
2.  ブレークポイントを選択し、開く、**ブレークポイント フィルター**  ダイアログ ボックスの最初の手順と同様にします。  
  
3.  **ブレークポイント フィルター**ダイアログ ボックスで、種類。  
  
     `ProcessName =`  *yourprocessname*  
  
     または  
  
     `ProcessID =`*yourprocessIDnumber*  
  
     より複雑なフィルターを作成する場合は、AND 演算子 (`&`)、OR 演算子 (`||`)、NOT 演算子 (`!`)、およびかっこを使って句を結合できます。  
  
4.  **[OK]**をクリックします。  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>特定のスレッドにブレークポイントを設定するには  
  
1.  スレッド名を取得またはスレッド ID 番号を**スレッド**ウィンドウです。  
  
2.  ブレークポイントを選択し、開く、**ブレークポイント フィルター**  ダイアログ ボックスの最初の手順に従ってします。  
  
3.  **ブレークポイント フィルター**ダイアログ ボックスで、種類。  
  
     `ThreadName =`*yourthreadname*  
  
     または  
  
     `ThreadID =`*yourthreadIDnumber*  
  
     より複雑なフィルターを作成する場合は、AND 演算子 (`&`)、OR 演算子 (`||`)、NOT 演算子 (`!`)、およびかっこを使って句を結合できます。  
  
4.  **[OK]**をクリックします。  
  
## <a name="example"></a>例  
 次の例は、`marvin` というコンピューターと `fourier1` というスレッドを対象とするブレークポイントのフィルターを作成する方法を示しています。  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>参照  
 [マルチ スレッド アプリケーションをデバッグします。](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [リモート デバッグ](../debugger/remote-debugging.md)   
 [方法: [プロセス] ウィンドウの使用](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [マルチ スレッド アプリケーションのデバッグの開始します。](../debugger/get-started-debugging-multithreaded-apps.md)   
 [スレッドとプロセス](http://msdn.microsoft.com/en-us/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [ブレークポイントの使用](../debugger/using-breakpoints.md)