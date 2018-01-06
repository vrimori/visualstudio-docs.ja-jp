---
title: "C ランタイム ライブラリなしのチェックの実行時間を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fc81dd57ca6a91cd748da82c792c2bbeca88bb25
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>C ランタイム ライブラリなしのランタイム チェックの使用方法
C ランタイム ライブラリなしプログラムをリンクする場合を使用して**/NODEFAULTLIB**実行時のチェックを使用して、RunTmChk.lib とリンクする必要があります。  
  
 `_RTC_Initialize` は、ランタイム チェックでプログラムを初期化します。 C ランタイム ライブラリとリンクしない場合は、次のように、プログラムが `_RTC_Initialize` を呼び出す前に、ランタイム エラー チェックでコンパイルされているかどうかを確認する必要があります。  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 C ランタイム ライブラリをリンクしない場合は、`_CRT_RTC_INITW` と呼ばれる関数も定義する必要があります。 `_CRT_RTC_INITW` は、次に示すように、ユーザー定義関数を既定のエラー レポート関数としてインストールします。  
  
```  
// C version:  
_RTC_error_fnW __cdecl _CRT_RTC_INITW(  
        void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler.  
    return &MyErrorFunc;   
}  
  
// C++ version:  
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(  
       void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler:  
    return &MyErrorFunc;  
}  
```  
  
 既定のエラー レポート関数を組み込むと、`_RTC_SetErrorFuncW` を使用して追加のエラー レポート関数を組み込むことができます。 詳細については、次を参照してください。 [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw)です。  
  
## <a name="see-also"></a>参照  
 [方法 : ネイティブ ランタイム チェックを使用する](../debugger/how-to-use-native-run-time-checks.md)