---
title: "クライアント ブロック用のフック関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0356ef6574e281ed896df5789eb741da1f206ba4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="client-block-hook-functions"></a>Client ブロック用のフック関数
`_CLIENT_BLOCK` 型のブロックに格納されているデータの内容を検証したりレポートしたりするために、専用の関数を作成できます。 作成する関数には、CRTDBG.H で定義されている次のようなプロトタイプが必要です。  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 つまり、独自のフック関数を受け入れる必要があります、 **void**と連携して、割り当てブロックの先頭を指すポインター、 **size_t**割り当てのサイズを示す値を入力し、返す`void`. それ以外の内容については、自由に決定できます。  
  
 フック関数を使用して、インストールした後[_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient)、たびに呼び出されます、`_CLIENT_BLOCK`ブロックをダンプします。 使用してできます[_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)型またはダンプされたブロックのサブタイプに情報を取得します。  
  
 渡す、関数へのポインター`_CrtSetDumpClient`の型は**_CRT_DUMP_CLIENT**CRTDBG で定義されています。H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>参照  
 [デバッグ用フック関数の作成](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 サンプル](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)