---
title: IDiaSymbol::get_isAcceleratorStubFunction |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2c11cc560be00bd51f8c5ebb35803240c5fbe8e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925332"
---
# <a name="idiasymbolgetisacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
シェーダーに対応するアクセラレータのコンパイルのシンボルが最上位の関数シンボルに対応するかどうかを示す、`parallel_for_each`呼び出します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_isAcceleratorStubFunction(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pFlag`  
 [out]ポインターを`BOOL`シェーダーに対応するアクセラレータのコンパイルのシンボルが最上位の関数シンボルに対応するかどうかを示す、`parallel_for_each`呼び出します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)