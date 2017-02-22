---
title: "レポート用マクロの使用 | Microsoft Docs"
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
  - "vs.debug.macros"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_RPTFn マクロ"
  - "_RPTn マクロ"
  - "CRT, レポート マクロ"
  - "デバッグ [CRT], レポート マクロ"
  - "マクロ, CRT レポート マクロ"
  - "マクロ, デバッグ"
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# レポート用マクロの使用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

CRTDBG.H で定義されている **\_RPTn** マクロと **\_RPTFn** マクロで、デバッグ用の `printf` ステートメントを置き換えることができます。  これらのマクロは、**\_DEBUG** が定義されていないリリース ビルドでは自動的に消滅するため、**\#ifdef** で囲む必要はありません。  
  
|マクロ|説明|  
|---------|--------|  
|**\_RPT0**、**\_RPT1**、**\_RPT2**、**\_RPT3**、**\_RPT4**|メッセージ文字列と、0 から 4 個の引数を出力します。  \_RPT1 から **\_RPT4** の場合、メッセージ文字列は、引数に対して printf と同じスタイルの書式指定文字列として機能します。|  
|**\_RPTF0**、**\_RPTF1**、**、\_RPTF2**、**\_RPTF4**|**\_RPTn** と同様ですが、これらのマクロが記述されているファイル名と行番号も出力します。|  
  
 次に例を示します。  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 このコードは、`someVar` の値と `otherVar` の値を **stdout** に出力します。  次のように `_RPTF2` を呼び出すと、これらの値と一緒にファイル名と行番号も出力できます。  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 特定のアプリケーションでは、C ランタイム ライブラリのマクロで提供されているデバッグ レポートでは不十分な場合があります。その場合は、独自の要件を満たす専用のマクロを設計できます。  たとえば、ヘッダー ファイルの 1 つに、次のような **ALERT\_IF2** というマクロを定義できます。  
  
```  
#ifndef _DEBUG                  /* For RELEASE builds */  
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)  
#else                           /* For DEBUG builds   */  
#define  ALERT_IF2(expr, msg, arg1, arg2) \  
    do { \  
        if ((expr) && \  
            (1 == _CrtDbgReport(_CRT_ERROR, \  
                __FILE__, __LINE__, msg, arg1, arg2))) \  
            _CrtDbgBreak( ); \  
    } while (0)  
#endif  
```  
  
 次のように **ALERT\_IF2** を 1 回呼び出すだけで、このトピックの冒頭に示した **printf** コードと同じ機能を実現できます。  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 カスタム マクロは、目的に応じて出力情報の量を増減したり、出力先を変更したりなどの変更を簡単に実現できるため、デバッグ要件が複雑さを増してくる段階で使用すると便利です。  
  
## 参照  
 [CRT のデバッグ技術](../debugger/crt-debugging-techniques.md)