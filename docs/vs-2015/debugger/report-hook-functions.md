---
title: レポート用のフック関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 557790edc774bab9db43830a4f5fc3e21cfc9758
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279449"
---
# <a name="report-hook-functions"></a>レポート用のフック関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

レポート用のフック関数の場合を使用してインストール[_CrtSetReportHook](http://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509)、毎回と呼びます[_CrtDbgReport](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)デバッグ レポートを生成します。 レポート用のフック関数を使用して、特定の割り当て型に関するレポートだけを出力できます。 レポート用のフック関数には、次のようなプロトタイプが必要です。  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 渡すポインター **_CrtSetReportHook**の種類は **_CRT_REPORT_HOOK**CRTDBG で定義されている、します。H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 ランタイム ライブラリが独自のフック関数を呼び出すときに、 *nRptType*引数には、レポートのカテゴリが含まれています (**前述**、 **_CRT_ERROR**、または **_CRT_ASSERT**)、 *szMsg*を完全に組み立てられたレポートのメッセージ文字列へのポインターが含まれていますと*retVal*を指定するかどうか`_CrtDbgReport`通常の実行を続行する必要があります後、デバッガーを開始、レポートを生成しています。 (A *retVal*値が 0 の実行を継続する、値 1 は、デバッガーを起動します)。  
  
 返すかかどうかフック関数は、さらにレポートを作成する必要はありませんように完全には、問題のメッセージを処理、 **TRUE**します。 返された場合**FALSE**、`_CrtDbgReport`レポート メッセージを通常されます。  
  
## <a name="see-also"></a>関連項目  
 [デバッグ用フック関数の作成](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 サンプル](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



