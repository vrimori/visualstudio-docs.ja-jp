---
title: クライアント ブロック用のフック関数 |Microsoft Docs
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
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b16dc9eaff974e98e411d4f49d8aed6f9f656e8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773939"
---
# <a name="client-block-hook-functions"></a>Client ブロック用のフック関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`_CLIENT_BLOCK` 型のブロックに格納されているデータの内容を検証したりレポートしたりするために、専用の関数を作成できます。 作成する関数には、CRTDBG.H で定義されている次のようなプロトタイプが必要です。  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 つまり、独自のフック関数が受け入れる必要があります、 **void**と共に割り当てブロックの先頭を指すポインター、 **size_t**割り当てのサイズを示す値を入力し、返す`void`. それ以外の内容については、自由に決定できます。  
  
 フック関数を使用して、インストールすると[_CrtSetDumpClient](http://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033)、毎回呼び出されます、`_CLIENT_BLOCK`ブロックをダンプします。 使用することができますし、 [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)型またはダンプされたブロックに情報を取得します。  
  
 渡す、関数へのポインター`_CrtSetDumpClient`の種類は **_CRT_DUMP_CLIENT**CRTDBG で定義されている、します。H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>関連項目  
 [デバッグ用フック関数の作成](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 サンプル](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)



