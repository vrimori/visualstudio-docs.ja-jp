---
title: Idiaenumsegments::skip |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Skip method
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 52f83ebca4d7d03afb8eae7a9b885334ccc1cb71
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924306"
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
指定された数の列挙体シーケンス内のセグメントをスキップします。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 celt  
 [in]スキップする列挙体シーケンス内のセグメントの数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`をスキップするより多くないセグメントがある場合。  
  
## <a name="see-also"></a>「  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)