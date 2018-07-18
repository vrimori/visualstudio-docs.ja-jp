---
title: レポートのフック関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 562944404d3e02a2e5768fcd74c67302475e6190
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481179"
---
# <a name="report-hook-functions"></a>レポート用のフック関数
レポート用のフック関数の場合を使用してインストール[_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook)、たびに呼び出されます[_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)デバッグ レポートが生成されます。 レポート用のフック関数を使用して、特定の割り当て型に関するレポートだけを出力できます。 レポート用のフック関数には、次のようなプロトタイプが必要です。  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 渡すポインター **_CrtSetReportHook**の種類は **_CRT_REPORT_HOOK**CRTDBG で定義されている、します。H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 ランタイム ライブラリが独自のフック関数を呼び出したときに、 *nRptType*引数には、レポートのカテゴリが含まれています (**前述**、 **_CRT_ERROR**、または **_CRT_ASSERT**)、 *szMsg* 、完全に組み立てられたレポートのメッセージ文字列へのポインターが含まれていますと*retVal*を指定するかどうか`_CrtDbgReport`通常の実行を続行する必要がありますレポートまたは開始デバッガーが生成されます。 (A *retVal*実行を継続する値は 0、1 の値は、デバッガーを起動します)。  
  
 返すかかどうかフック関数は、以降のレポートは必要ありませんされるように、完全に対象のメッセージを処理、 **TRUE**です。 返された場合**FALSE**、`_CrtDbgReport`レポート メッセージを通常されます。  
  
## <a name="see-also"></a>関連項目  
 [デバッグ用フック関数の作成](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 サンプル](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)