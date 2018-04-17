---
title: IDiaStackWalkHelper |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 881fcbb4f019ad9cb6321423c12269fb6e3ad78f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
プログラム デバッグ データベース (.pdb) ファイルを使用して、スタック ウォークが容易になります。  
  
## <a name="syntax"></a>構文  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## <a name="methods-in-vtable-order"></a>VTable 順序のメソッド  
 次の表は、のメソッドを示しています`IDiaStackWalkHelper`:。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|レジスタの値を取得します。|  
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|レジスタの値を設定します。|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|メモリ内で実行可能ファイルのイメージからのデータ ブロックを読み取ります。|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|最も近い関数のリターン アドレスの指定したスタック フレームを検索します。|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|または、指定したスタック アドレスの近くのリターン アドレスの指定したスタック フレームを検索します。|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|指定された仮想アドレスを含むスタック フレームを取得します。|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|指定した仮想アドレスを含んでいるシンボルを取得します。 **注:**シンボルは、型である必要があります`SymTagFunctionType`(から値、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)列挙型)。|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|指定された仮想アドレスに関連付けられている PDATA データ ブロックを返します。|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|実行可能ファイルのメモリ領域で仮想アドレスを任意の場所が指定されて、実行可能ファイルの開始仮想アドレスを取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、プログラムの実行中のスタック フレームの一覧を構築するために実行可能ファイルに関する情報を取得する DIA コードによって呼び出されます。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 クライアント アプリケーションでは、プログラムの実行中にスタックのウォークをサポートするためにこのインターフェイスを実装します。 このインターフェイスのインスタンスに渡される、 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)または[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>関連項目  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)