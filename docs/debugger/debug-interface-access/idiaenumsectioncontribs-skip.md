---
title: Idiaenumsectioncontribs::skip |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e24d913acfacbec626befac07167528b9be2ace
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009818"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
指定された数の列挙体シーケンスにおけるのセクションをスキップします。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Skip(   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]スキップする列挙体シーケンス内のセクションの投稿の数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`複数セクションをスキップする投稿がある場合。  
  
## <a name="see-also"></a>「  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)