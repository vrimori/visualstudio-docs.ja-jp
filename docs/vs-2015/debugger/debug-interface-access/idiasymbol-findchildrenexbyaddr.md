---
title: IDiaSymbol::findChildrenExByAddr |Microsoft Docs
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
- IDiaSymbol::findChildrenExByAddr
ms.assetid: c1e7885d-2d15-4529-9ac2-32dd22efe31c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9cd72b80feb1c8e2ecca603b929737bf05dd829e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924357"
---
# <a name="idiasymbolfindchildrenexbyaddr"></a>IDiaSymbol::findChildrenExByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指定したアドレスに有効なシンボルの子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
  
## <a name="remarks"></a>Remarks  
 返されるローカル シンボルには、ライブの範囲の情報が含まれます。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [Idiasession::findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md)



