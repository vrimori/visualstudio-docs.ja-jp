---
title: '方法: 高パフォーマンス クラスター上のデバッグ |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-perfomance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9964621c216d058581d9298956ba90ac6cdbef86
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280793"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>方法 : 高パフォーマンス クラスター上でデバッグする
高パフォーマンス クラスター上でのマルチプロセス プログラムのデバッグは、リモート コンピューター上での通常のプログラムのデバッグと似ています。 ただし、追加の考慮事項がいくつかあります。 一般的なリモート セットアップ要件は、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)します。  
  
 高パフォーマンス クラスター上でデバッグするときは、リモート デバッグに使用できる [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のデバッグ ウィンドウとデバッグ手法をすべて使用できます。 ただし、リモートでデバッグするため、外部のコンソール ウィンドウは使用できません。  
  
 **スレッド**ウィンドウと**プロセス**ウィンドウは並列アプリケーションのデバッグに特に便利です。 これらのウィンドウを使用する方法のヒントについては、次を参照してください。[方法: [プロセス] ウィンドウを使用して、](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))と[チュートリアル: [スレッド] ウィンドウを使用してデバッグ](../debugger/how-to-use-the-threads-window.md)します。  
  
 以下の手順では、高パフォーマンス クラスター上でのデバッグに特に役立つ手法を示します。  
  
 並列アプリケーションをデバッグするときは、特定のスレッド、プロセス、またはコンピューターにブレークポイントを設定することが必要になる場合があります。 これを行うには、通常のブレークポイントを作成してから、ブレークポイント フィルターを追加します。  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>[ブレークポイントのフィルター] ダイアログ ボックスを開くには  
  
1.  ソース ウィンドウでブレークポイント グリフを右クリックして、**逆アセンブリ**ウィンドウで、**呼び出し履歴**ウィンドウ、または**ブレークポイント**ウィンドウ。  
  
2.  ショートカット メニューで、**フィルター**します。 このオプションは、レベル、またはサブメニューの下の上部に表示可能性があります**ブレークポイント**します。  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>特定のコンピューターにブレークポイントを設定するには  
  
1.  コンピューター名を取得、**プロセス**ウィンドウ。  
  
2.  ブレークポイントを選択し、開く、**ブレークポイント フィルター**  ダイアログ ボックスのように、前の手順で説明されています。  
  
3.  **ブレークポイント フィルター**ダイアログ ボックスで、種類。  
  
     MachineName =*コンピューター名*  
  
     より複雑なフィルターを作成する場合は、AND 演算子 (`&`)、OR 演算子 (`||`)、NOT 演算子 (`!`)、およびかっこを使って句を結合できます。  
  
4.  **[OK]** をクリックします。  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>特定のプロセスにブレークポイントを設定するには  
  
1.  プロセス名を取得またはプロセス ID 番号を**プロセス**ウィンドウ。  
  
2.  ブレークポイントを選択し、開く、**ブレークポイント フィルター**  ダイアログ ボックスの最初の手順のようにします。  
  
3.  **ブレークポイント フィルター**ダイアログ ボックスで、種類。  
  
     `ProcessName =`  *yourprocessname*  
  
     または  
  
     `ProcessID =` *yourprocessIDnumber*  
  
     より複雑なフィルターを作成する場合は、AND 演算子 (`&`)、OR 演算子 (`||`)、NOT 演算子 (`!`)、およびかっこを使って句を結合できます。  
  
4.  **[OK]** をクリックします。  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>特定のスレッドにブレークポイントを設定するには  
  
1.  スレッド名を取得またはスレッド ID 番号を**スレッド**ウィンドウ。  
  
2.  ブレークポイントを選択し、開く、**ブレークポイントのフィルター**  ダイアログ ボックスの最初の手順で説明します。  
  
3.  **ブレークポイント フィルター**ダイアログ ボックスで、種類。  
  
     `ThreadName =` *yourthreadname*  
  
     または  
  
     `ThreadID =` *yourthreadIDnumber*  
  
     より複雑なフィルターを作成する場合は、AND 演算子 (`&`)、OR 演算子 (`||`)、NOT 演算子 (`!`)、およびかっこを使って句を結合できます。  
  
4.  **[OK]** をクリックします。  
  
## <a name="example"></a>例  
 次の例は、`marvin` というコンピューターと `fourier1` というスレッドを対象とするブレークポイントのフィルターを作成する方法を示しています。  
  
`(MachineName = marvin) & (ThreadName = fourier1)`  

  
## <a name="see-also"></a>関連項目  
 [マルチ スレッド アプリケーションをデバッグします。](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [リモート デバッグ](../debugger/remote-debugging.md)   
 [方法: [プロセス] ウィンドウの使用](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))   
 [マルチ スレッド アプリケーションのデバッグの開始します。](../debugger/get-started-debugging-multithreaded-apps.md)   
 [スレッドとプロセス](/previous-versions/visualstudio/visual-studio-2010/ms164740(v=vs.100))   
 [ブレークポイントの使用](../debugger/using-breakpoints.md)