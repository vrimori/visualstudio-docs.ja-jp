---
title: IDiaReadExeAtRVACallback |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5da0af12c193bfa93b176ef0b06a4860afb3f2ac
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273235"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

相対仮想アドレスで指定された実行可能ファイルのバイト数を指定するクライアント アプリケーションを有効にします。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDiaReadExeAtRVACallback`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|指定した数の指定された相対仮想アドレス (RVA) 実行可能ファイルからで始まるバイトを読み取ります。|  
  
## <a name="remarks"></a>Remarks  
 クライアント アプリケーションは、実行可能ファイルのファイルに相対仮想アドレスを使用して実行可能ファイルのバイト数を提供するために、このインターフェイスを実装します。 ファイルの絶対オフセットを使用するには、実装、 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このメソッドは、クライアント アプリケーションによって実装されに渡される、 [idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)メソッド、ファイルの読み取りの代替方法として。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>関連項目  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)



