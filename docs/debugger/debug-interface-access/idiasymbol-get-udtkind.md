---
title: Idiasymbol::get_udtkind |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_udtKind method
ms.assetid: 4002f887-aea6-4475-b302-67c57079fe0a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c97d56b5ff47652ae04d2cb2e37105b08a00612
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996000"
---
# <a name="idiasymbolgetudtkind"></a>IDiaSymbol::get_udtKind
さまざまなユーザー定義型 (UDT) を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_udtKind (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]値を返します、 [UdtKind 列挙型](../../debugger/debug-interface-access/udtkind.md)UDT の種類を指定する列挙体: 構造体、クラス、または共用体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [UdtKind 列挙型](../../debugger/debug-interface-access/udtkind.md)