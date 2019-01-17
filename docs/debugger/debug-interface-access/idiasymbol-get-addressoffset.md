---
title: Idiasymbol::get_addressoffset |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 78f801faae0a32bd928f6adb8062acf18bdf1332
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875194"
---
# <a name="idiasymbolgetaddressoffset"></a>IDiaSymbol::get_addressOffset
アドレス場所のオフセットの部分を取得します。 使用する場合、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)に設定されている`LocIsStatic`します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]アドレス場所のオフセットの部分を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティがシンボルを使用できないことを意味します。  
  
## <a name="remarks"></a>コメント  
 静的メンバーを外部 DLL 内にある、このメソッドによって返されるオフセットあります 0 仮想メンバーのアドレスを取得するのには、このメソッドを利用。 仮想アドレスは有効な場合にのみ、 [idiasession::put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)メソッドで、 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)インターフェイスは、DLL の読み込みアドレスを指定する 0 以外のパラメーターで呼び出されました。  
  
 アドレスのセクションの一部を取得する、 [idiasymbol::get_addresssection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)メソッド。  
  
## <a name="requirements"></a>要件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|dia2.h|  
|バージョン:|DIA SDK v7.0|  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)   
 [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)