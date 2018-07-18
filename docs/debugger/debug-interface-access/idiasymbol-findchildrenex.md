---
title: IDiaSymbol::findChildrenEx |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenEx
ms.assetid: 6e045045-da8c-4338-9423-81a1ca20c405
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: abc8657f57ad58f8a6c259b38e98c34455019186
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31464496"
---
# <a name="idiasymbolfindchildrenex"></a>IDiaSymbol::findChildrenEx
シンボルの子を取得します。 返されるローカル シンボルにはでの最適化を使用して、プログラムがコンパイルされている場合、ライブの範囲の情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT findChildrenEx (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `symtag`  
 [in]タグを指定します、シンボルの子を取得するので定義されている、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)です。 設定`SymTagNull`すべての子を取得します。  
  
 `name`  
 [in]取得する子の名前を指定します。 設定`NULL`すべての子を取得します。  
  
 `compareFlags`  
 [in]名前の一致に適用する比較オプションを指定します。 値から、 [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md)列挙体は、単独または組み合わせて使用できます。  
  
 `ppResult`  
 [out]返します、 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)子の記号の一覧を含むオブジェクトを取得します。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`シンボルの少なくとも 1 つの子が見つかりましたが、または返す`S_FALSE`場合は子が見つかりませんでした。 エラー コードを返しますそれ以外の場合。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、拡張のバージョンの[idiasymbol::findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [Idiasession::findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md)