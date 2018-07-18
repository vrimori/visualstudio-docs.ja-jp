---
title: IDiaSymbol::get_isAcceleratorStubFunction |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cddf6be53925ed6f9cd613f7e7a19cca9f00cace
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468052"
---
# <a name="idiasymbolgetisacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
シンボルに対応するアクセラレータ用にコンパイルされたシェーダーのトップレベルの関数シンボルに対応するかどうかを示します、`parallel_for_each`呼び出します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_isAcceleratorStubFunction(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pFlag`  
 [out]ポインター、`BOOL`シェーダーに対応するアクセラレータのコンパイルにシンボルがトップレベルの関数シンボルに対応かどうかを示す、`parallel_for_each`呼び出します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`またはエラー コード。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)