---
title: "Idiaenumsegments::next |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7cd90b31d9baa887052b7264bfb8be8df65f1535
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
指定した列挙のシーケンス内のセグメント数を取得します。  
  
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
 [out]目的を入力するのには配列を[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)セグメントを表すオブジェクト。  
  
 pceltFetched  
 [out]フェッチされた列挙子のセグメントの数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`ない他のセグメントがある場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>参照  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)