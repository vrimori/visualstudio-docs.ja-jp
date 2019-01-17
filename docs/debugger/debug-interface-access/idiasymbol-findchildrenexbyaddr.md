---
title: IDiaSymbol::findChildrenExByAddr |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByAddr
ms.assetid: c1e7885d-2d15-4529-9ac2-32dd22efe31c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 900699fc543da7eba25624766ac6c8b0d5cf88bb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875100"
---
# <a name="idiasymbolfindchildrenexbyaddr"></a>IDiaSymbol::findChildrenExByAddr
指定したアドレスに有効なシンボルの子を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT findChildrenExByAddr (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `symtag`  
 [in]定義されているを取得するには、子のシンボル タグを指定します、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)します。 設定`SymTagNull`のすべての子を取得します。  
  
 `name`  
 [in]取得する子の名前を指定します。 設定`NULL`のすべての子を取得します。  
  
 `compareFlags`  
 [in]名前の一致に適用される比較オプションを指定します。 値から、 [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md)列挙体は、単独または組み合わせて使用できます。  
  
 `address`  
 [in]シンボルのアドレス。  
  
 `ppResult`  
 [out]返します、 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)子シンボルの一覧を含むオブジェクトを取得します。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`シンボルの少なくとも 1 つの子が検出されましたが、またはを返す`S_FALSE`場合は子が見つかりませんでした。 それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 返されるローカル シンボルには、ライブの範囲の情報が含まれます。  
  
## <a name="requirements"></a>要件  
 ヘッダー:dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md)