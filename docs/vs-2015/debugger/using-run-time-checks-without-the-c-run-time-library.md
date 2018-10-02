---
title: C ランタイム ライブラリなしのチェックの実行時間を使用して |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 864e21d2c2ec2a9922d70e6b69192d9268556737
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547264"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>C ランタイム ライブラリなしのランタイム チェックの使用方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[を使用して実行時チェックせず、C ランタイム ライブラリ](https://docs.microsoft.com/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)します。  
  
C ランタイム ライブラリなしプログラムをリンクする場合を使用して **/NODEFAULTLIB**実行時のチェックを使用しては、RunTmChk.lib とリンクする必要があります。  
  
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
  
 既定のエラー レポート関数を組み込むと、`_RTC_SetErrorFuncW` を使用して追加のエラー レポート関数を組み込むことができます。 詳細については、次を参照してください。 [_RTC_SetErrorFuncW](http://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a)します。  
  
## <a name="see-also"></a>関連項目  
 [方法 : ネイティブ ランタイム チェックを使用する](../debugger/how-to-use-native-run-time-checks.md)





