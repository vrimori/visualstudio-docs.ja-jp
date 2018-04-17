---
title: IDiaStackWalkFrame |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e532323923aaa3c50e00fc685fb39eaf8bfed80
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
呼び出しの間でのスタック コンテキストを維持、 [idiaframedata::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDiaStackWalkFrame`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|レジスタの値を取得します。|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|レジスタの値を設定します。|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|イメージからメモリを読み取ります。|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|最も近い関数のリターン アドレスの指定したスタック フレームを検索します。|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|指定されたアドレスに近いのリターン アドレスの指定したスタック フレームを検索します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、レジスタの書き込みだけでなくメモリへのアクセスおよび戻り値のアドレスの検索プログラムの実行中に使用されます。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 クライアント アプリケーションを選択し、このインターフェイスを実装するインターフェイスのインスタンスを渡す、 [idiaframedata::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)メソッドです。 各呼び出し中に、レジスタの状態を維持するためにこのインターフェイスの同じインスタンスを繰り返し使用される、`execute`メソッドです。 `execute`メソッドが戻り値のアドレスを決定するもこのインターフェイスを使用します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>関連項目  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)