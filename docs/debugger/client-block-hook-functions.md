---
title: "Client ブロック用のフック関数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CrtSetDumpClient 関数"
  - "クライアント ブロック, フック関数"
  - "クライアント ブロック, 検証と報告 (データの)"
  - "デバッグ [C++], フック関数"
  - "フック, クライアント ブロック"
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Client ブロック用のフック関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`_CLIENT_BLOCK` 型のブロックに格納されているデータの内容を検証したりレポートしたりするために、専用の関数を作成できます。  作成する関数には、CRTDBG.H で定義されている次のようなプロトタイプが必要です。  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 つまり、独自のフック関数は、対象となる割り当てブロックの先頭への **void** ポインターと、割り当てサイズを示す **size\_t** 型の値を受け取り、`void` を返すようにする必要があります。  それ以外の内容については、自由に決定できます。  
  
 作成したフック関数を [\_CrtSetDumpClient](/visual-cpp/c-runtime-library/reference/crtsetdumpclient) を使用して組み込むと、`_CLIENT_BLOCK` 型のブロックがダンプされるたびに、このフック関数が呼び出されます。  [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype) を使用すると、ダンプされたブロックの型や、その細分化された型に関する情報を取得できます。  
  
 `_CrtSetDumpClient` に渡す独自の関数へのポインターは **\_CRT\_DUMP\_CLIENT** 型です。これらは、CRTDBG.H で次のように定義されています。  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## 参照  
 [デバッグ用フック関数の作成](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/ja-jp/21e1346a-6a17-4f57-b275-c76813089167)   
 [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype)