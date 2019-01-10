---
title: Idiaenumsymbols::skip |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 492748dc54f68d4f888b8cfb6ad8e27ec44435d0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53918626"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
指定された数の列挙体シーケンス内のシンボルをスキップします。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 celt  
 [in]スキップする列挙体シーケンス内のシンボルの数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`をスキップするシンボルがある場合。  
  
## <a name="see-also"></a>「  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)