---
title: クライアント ブロック用のフック関数 |Microsoft ドキュメント
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
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eccc1781174394da333d2fc703fec0b4d31e522a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31457232"
---
# <a name="client-block-hook-functions"></a>Client ブロック用のフック関数
`_CLIENT_BLOCK` 型のブロックに格納されているデータの内容を検証したりレポートしたりするために、専用の関数を作成できます。 作成する関数には、CRTDBG.H で定義されている次のようなプロトタイプが必要です。  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 つまり、独自のフック関数を受け入れる必要があります、 **void**と連携して、割り当てブロックの先頭を指すポインター、 **size_t**割り当てのサイズを示す値を入力し、返す`void`. それ以外の内容については、自由に決定できます。  
  
 フック関数を使用して、インストールした後[_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient)、たびに呼び出されます、`_CLIENT_BLOCK`ブロックをダンプします。 使用してできます[_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)型またはダンプされたブロックのサブタイプに情報を取得します。  
  
 渡す、関数へのポインター`_CrtSetDumpClient`の型は **_CRT_DUMP_CLIENT**CRTDBG で定義されています。H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>関連項目  
 [デバッグ用フック関数の作成](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 サンプル](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)