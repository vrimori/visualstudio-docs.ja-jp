---
title: "レポート用のフック関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "_CrtDbgReport 関数"
  - "_CrtSetReportHook 関数"
  - "デバッガー, レポート用のフック関数"
  - "デバッグ [C++], フック関数"
  - "フック, レポート"
  - "メモリの割り当て, デバッグ ヒープ"
  - "レポート用のフック関数"
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# レポート用のフック関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[\_CrtSetReportHook](/visual-cpp/c-runtime-library/reference/crtsetreporthook) を使用して組み込まれたレポート用のフック関数は、[\_CrtDbgReport](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) がデバッグ レポートを生成するたびに呼び出されます。  レポート用のフック関数を使用して、特定の割り当て型に関するレポートだけを出力できます。  レポート用のフック関数には、次のようなプロトタイプが必要です。  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 **\_CrtSetReportHook** に渡すポインターは **\_CRT\_REPORT\_HOOK** 型です。これらは、CRTDBG.H で次のように定義されています。  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 ランタイム ライブラリが独自のフック関数を呼び出す場合は、引数 *nRptType* には、レポートの種類 \(**\_CRT\_WARN**、**\_CRT\_ERROR**、または **\_CRT\_ASSERT**\) が格納されます。引数 *szMsg* には、レポート用の完全にアセンブルされたメッセージ文字列へのポインターが入ります。また、引数 *retVal* には、`_CrtDbgReport` がレポート作成後に通常どおり実行を継続するのか、デバッガーを起動するのかを示す値が格納されます。 *retVal* の値が 0 の場合は実行を継続し、1 の場合はデバッガーを起動します。  
  
 フック関数でメッセージを完全に処理できたため、それ以上レポートを出力する必要がない場合は、**TRUE** を返すようにします。  **FALSE** を返した場合は、`_CrtDbgReport` は通常どおりにレポート メッセージを出力します。  
  
## 参照  
 [デバッグ用フック関数の作成](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/ja-jp/21e1346a-6a17-4f57-b275-c76813089167)