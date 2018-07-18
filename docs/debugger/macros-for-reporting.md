---
title: レポート用マクロの |Microsoft Docs
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
ms.openlocfilehash: 57b254323fac5d670cd44399cd8d22c9530c4510
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056603"
---
# <a name="macros-for-reporting"></a>レポート用マクロの使用
デバッグについては、使用することができます、 **_RPTn**と **_RPTFn** crtdbg マクロ。代わりに、H`printf`ステートメント。 Inclose にする必要はありません **#ifdef**s のリリースでは自動的に消滅するため、ビルド **_DEBUG**が定義されていません。  
  
|マクロ|説明|  
|-----------|-----------------|  
|**_RPT0**、 **_RPT1**、 **_RPT2**、 **_RPT3**、 **_RPT4**|メッセージ文字列と、0 から 4 個の引数を出力します。 _Rpt1 **_RPT4**、メッセージ文字列は、引数の printf スタイルの書式指定文字列として機能します。|  
|**_RPTF0**、 **_RPTF1**、 **_RPTF2**、 **_RPTF4**|同じ **_RPTn**がこれらのマクロは、マクロが配置されているファイル名と行番号も出力します。|  
  
 次に例を示します。  
  
```cpp
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 このコードの値を出力する`someVar`と`otherVar`に**stdout**します。 次のように `_RPTF2` を呼び出すと、これらの値と一緒にファイル名と行番号も出力できます。  
  
```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
特定のアプリケーションは、デバッグ レポート C ランタイム ライブラリに付属しているマクロを提供しない必要があることがあります。 このような場合は、独自の要件を満たすために特に設計マクロを記述できます。 ヘッダー ファイルの 1 つなどを含めることができます、マクロを定義するには、次と呼ばれるようなコード**ALERT_IF2**:  
  
```cpp
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
  
 1 回の呼び出しに**ALERT_IF2**のすべての機能を実行する可能性があります、 **printf**コード。  
  
```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 多かれ少なかれさまざまな宛先に情報を報告するカスタム マクロを簡単に変更することができます。 デバッグ ニーズが進化するにつれて、この方法は特に便利です。  
  
## <a name="see-also"></a>関連項目  
 [CRT のデバッグ技術](../debugger/crt-debugging-techniques.md)
