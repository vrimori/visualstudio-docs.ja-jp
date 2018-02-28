---
title: "IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d96e58f19ae4170430488bc33e454d70944c36af
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)