---
title: IDiaStackWalker |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae33fc6c135322e6b6a0a965188848ddac363cbc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993674"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
.Pdb ファイルに情報を使用してスタックの操作を行う方法の説明を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDiaStackWalker`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|X86 スタック フレームの列挙子を取得します。 プラットフォーム。|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|特定のプラットフォームの種類のスタック フレームの列挙子を取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、読み込まれたモジュールのスタック フレームの一覧の取得に使用されます。 各メソッドに渡される、 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) (クライアント アプリケーションによって実装される) のスタック フレームのリストを作成するために必要な情報を提供するオブジェクト。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは呼び出すことによって取得、`CoCreateInstance`クラス識別子を持つメソッド`CLSID_DiaStackWalker`とのインターフェイス ID`IID_IDiaStackWalker`します。 この例では、このインターフェイスを取得する方法を示します。  
  
## <a name="example"></a>例  
 この例は、取得する方法を示します、`IDiaStackWalker`インターフェイス。  
  
```C++  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>要件  
 ヘッダー:dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>「  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)