---
title: IDiaStackWalkHelper |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 80f269df947227f36e0c87a7efeddda8d8ef1248
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944229"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
プログラム デバッグ データベース (.pdb) ファイルを使用して、スタック ウォークが容易になります。  
  
## <a name="syntax"></a>構文  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDiaStackWalkHelper`:  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|レジスタの値を取得します。|  
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|レジスタの値を設定します。|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|メモリ内で実行可能ファイルのイメージからのデータのブロックを読み取ります。|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|最も近い関数のリターン アドレスの指定したスタック フレームを検索します。|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|または、指定したスタック アドレスの近くのリターン アドレスの指定したスタック フレームを検索します。|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|指定された仮想アドレスを含むスタック フレームを取得します。|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|指定した仮想アドレスを表すシンボルを取得します。 **注:** シンボルは、型である必要があります`SymTagFunctionType`(からの値、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)列挙型)。|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|指定された仮想アドレスに関連付けられている PDATA データ ブロックを返します。|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|実行可能ファイルのメモリ領域で仮想アドレスをどこかが指定されて、実行可能ファイルの開始仮想アドレスを取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、プログラムの実行中にスタック フレームのリストを構築する実行可能ファイルに関する情報を取得する DIA コードによって呼び出されます。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 クライアント アプリケーションでは、プログラムの実行中にスタックのウォークをサポートするためにこのインターフェイスを実装します。 このインターフェイスのインスタンスは、 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)または[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)メソッド。  
  
## <a name="requirements"></a>要件  
 ヘッダー:dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>「  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)