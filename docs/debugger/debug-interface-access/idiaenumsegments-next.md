---
title: Idiaenumsegments::next |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c9966555c673904a423de1b215e438b5db15479
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951029"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
指定した列挙体シーケンス内のセグメント数を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Next (   
   ULONG         celt,   
   IDiaSegment** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 celt  
 [in]取得する列挙子内のセグメントの数。  
  
 rgelt  
 [out]情報を格納する目的である配列[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)セグメントを表すオブジェクト。  
  
 pceltFetched  
 [out]フェッチされた列挙子のセグメントの数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`ない他のセグメントがある場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)