---
title: "IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f12417323d0553fc6dd9ca33c65c566229454c99
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
対応するタグの値を指定するには、このメソッドは、指定の相対仮想アドレスにある場合は、このスタブ関数に含まれている記号の列挙を返します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `tagValue`  
 [in]Pointee シンボル レコードを検出するポインターのタグ値。  
  
 `rva`  
 [in]指定したタグの値を持つ pointee 変数に対応するシンボルをフィルター処理に使用される rva です。  
  
 `ppResult`  
 [out]ポインター、`IDiaEnumSymbols`結果で初期化されたインターフェイス ポインター。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`またはエラー コード。  
  
## <a name="remarks"></a>コメント  
 のみこのメソッドを呼び出して、`IDiaSymbol`アクセラレータ スタブ関数に対応するインターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)