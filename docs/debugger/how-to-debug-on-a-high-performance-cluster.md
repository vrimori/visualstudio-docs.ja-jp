---
title: "方法 : 高パフォーマンス クラスター上でデバッグする | Microsoft Docs"
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
  - "クラスター デバッグ"
  - "高パフォーマンス デバッグ"
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : 高パフォーマンス クラスター上でデバッグする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

高パフォーマンス クラスター上でのマルチプロセス プログラムのデバッグは、リモート コンピューター上での通常のプログラムのデバッグと似ています。  ただし、追加の考慮事項がいくつかあります。  一般的なリモート セットアップ要件については、「[リモート デバッグ](../debugger/remote-debugging.md)」を参照してください。  
  
 高パフォーマンス クラスター上でデバッグするときは、リモート デバッグに使用できる [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のデバッグ ウィンドウとデバッグ手法をすべて使用できます。  ただし、リモートでデバッグするため、外部のコンソール ウィンドウは使用できません。  
  
 **\[スレッド\]** ウィンドウと **\[プロセス\]** ウィンドウは、並列アプリケーションをデバッグする際に特に役立ちます。  これらのウィンドウの使い方に関するヒントについては、「[How to: Use the Processes Window](http://msdn.microsoft.com/ja-jp/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)」および「[方法 : \[スレッド\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Threads%20Window.md)」を参照してください。  
  
 以下の手順では、高パフォーマンス クラスター上でのデバッグに特に役立つ手法を示します。  
  
 並列アプリケーションをデバッグするときは、特定のスレッド、プロセス、またはコンピューターにブレークポイントを設定することが必要になる場合があります。  これを行うには、通常のブレークポイントを作成してから、ブレークポイント フィルターを追加します。  
  
### \[ブレークポイントのフィルター\] ダイアログ ボックスを開くには  
  
1.  ソース ウィンドウ、**\[逆アセンブル\]** ウィンドウ、**\[呼び出し履歴\]** ウィンドウ、または **\[ブレークポイント\]** ウィンドウでブレークポイント グリフを右クリックします。  
  
2.  ショートカット メニューの **\[フィルター\]** をクリックします。  このオプションは、最上位レベルまたは **\[ブレークポイント\]** のサブメニューとして表示されます。  
  
### 特定のコンピューターにブレークポイントを設定するには  
  
1.  **\[プロセス\]** ウィンドウでコンピューター名を確認します。  
  
2.  ブレークポイントを選択し、前記の手順に従って **\[ブレークポイントのフィルター\]** ダイアログ ボックスを開きます。  
  
3.  **\[ブレークポイントのフィルター\]** ダイアログ ボックスに次の文字列を入力します。  
  
     MachineName \=*yourmachinename*  
  
     より複雑なフィルターを作成する場合は、AND 演算子 \(`&`\)、OR 演算子 \(`||`\)、NOT 演算子 \(`!`\)、およびかっこを使って句を結合できます。  
  
4.  **\[OK\]** をクリックします。  
  
### 特定のプロセスにブレークポイントを設定するには  
  
1.  **\[プロセス\]** ウィンドウで、プロセス名またはプロセス ID 番号を取得します。  
  
2.  ブレークポイントを選択し、最初の手順に従って **\[ブレークポイントのフィルター\]** ダイアログ ボックスを開きます。  
  
3.  **\[ブレークポイントのフィルター\]** ダイアログ ボックスに次の文字列を入力します。  
  
     `ProcessName =`  *yourprocessname*  
  
     または  
  
     `ProcessID =` *yourprocessIDnumber*  
  
     より複雑なフィルターを作成する場合は、AND 演算子 \(`&`\)、OR 演算子 \(`||`\)、NOT 演算子 \(`!`\)、およびかっこを使って句を結合できます。  
  
4.  **\[OK\]** をクリックします。  
  
### 特定のスレッドにブレークポイントを設定するには  
  
1.  **\[スレッド\]** ウィンドウで、スレッド名またはスレッド ID 番号を取得します。  
  
2.  ブレークポイントを選択し、最初の手順に従って **\[ブレークポイントのフィルター\]** ダイアログ ボックスを開きます。  
  
3.  **\[ブレークポイントのフィルター\]** ダイアログ ボックスに次の文字列を入力します。  
  
     `ThreadName =` *yourthreadname*  
  
     または  
  
     `ThreadID =` *yourthreadIDnumber*  
  
     より複雑なフィルターを作成する場合は、AND 演算子 \(`&`\)、OR 演算子 \(`||`\)、NOT 演算子 \(`!`\)、およびかっこを使って句を結合できます。  
  
4.  **\[OK\]** をクリックします。  
  
## 使用例  
 次の例は、`marvin` というコンピューターと `fourier1` というスレッドを対象とするブレークポイントのフィルターを作成する方法を示しています。  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## 参照  
 [マルチスレッド アプリケーションのデバッグ](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [リモート デバッグ](../debugger/remote-debugging.md)   
 [How to: Use the Processes Window](http://msdn.microsoft.com/ja-jp/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [方法 : \[スレッド\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Threads%20Window.md)   
 [Threads and Processes](http://msdn.microsoft.com/ja-jp/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [ブレークポイントの使用](../debugger/using-breakpoints.md)