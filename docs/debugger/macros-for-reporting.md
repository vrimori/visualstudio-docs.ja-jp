---
title: レポート用マクロ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dd2dbb0651aa35243090fb554fa9142573e04e04
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="macros-for-reporting"></a>レポート用マクロの使用
使用することができます、 **_RPTn**、および**_RPTFn** CRTDBG で定義されているマクロです。H の代わりに`printf`デバッグ用のステートメント。 これらのマクロは、リリースでは自動的に消滅ビルド**_DEBUG**が定義されていないためで囲む必要はありません**#ifdef**s。  
  
|マクロ|説明|  
|-----------|-----------------|  
|**_RPT0**、 **_RPT1**、 **_RPT2**、 **_RPT3**、 **_RPT4**|メッセージ文字列と、0 から 4 個の引数を出力します。 _Rpt1 から**_RPT4**、メッセージ文字列は、引数に対して printf 書式指定文字列として機能します。|  
|**_RPTF0**、 **_RPTF1**、 **、_RPTF2**、 **_RPTF4**|同じ**_RPTn**がこれらのマクロはマクロが配置されているファイル名と行番号も出力します。|  
  
 次に例を示します。  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 このコードの値を出力する`someVar`と`otherVar`に**stdout**です。 次のように `_RPTF2` を呼び出すと、これらの値と一緒にファイル名と行番号も出力できます。  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 特定のアプリケーションでは、C ランタイム ライブラリのマクロで提供されているデバッグ レポートでは不十分な場合があります。その場合は、独自の要件を満たす専用のマクロを設計できます。 ヘッダー ファイルの 1 つは、たとえば、含めることも、マクロを定義するには、次と呼ばれるようなコード**ALERT_IF2**:  
  
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
  
 1 回の呼び出し**ALERT_IF2**のすべての機能を実行できなかった、 **printf**このトピックの冒頭にあるコード。  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 カスタム マクロは、目的に応じて出力情報の量を増減したり、出力先を変更したりなどの変更を簡単に実現できるため、デバッグ要件が複雑さを増してくる段階で使用すると便利です。  
  
## <a name="see-also"></a>関連項目  
 [CRT のデバッグ技術](../debugger/crt-debugging-techniques.md)