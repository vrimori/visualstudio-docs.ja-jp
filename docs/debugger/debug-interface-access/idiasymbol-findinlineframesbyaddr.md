---
title: IDiaSymbol::findInlineFramesByAddr |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36a122e6-f27e-40cd-9784-cdaf279e1905
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cbf330238d213854ba26d8345d0daaee7b3f9b1d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31464470"
---
# <a name="idiasymbolfindinlineframesbyaddr"></a>IDiaSymbol::findInlineFramesByAddr
すべての指定したアドレスのインライン フレームを反復処理するクライアントを許可する列挙体を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT findInlineFramesByAddr (   
   DWORD             isect,  
   DWORD             offset,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `isect`  
 [in]アドレスのセクションのコンポーネントを指定します。  
  
 `offset`  
 [in]アドレスのオフセットのコンポーネントを指定します。  
  
 `ppResult`  
 [out]保持する`IDiaEnumSymbols`取得されるフレームの一覧を含むオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)