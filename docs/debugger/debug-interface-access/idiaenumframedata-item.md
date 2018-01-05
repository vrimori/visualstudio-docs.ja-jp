---
title: "Idiaenumframedata::item |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3b2379d1f535583b3ff729342657cf44861c4939
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
インデックスを使用して、フレーム データ要素を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 インデックス  
 [in]インデックス、 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)を取得するオブジェクト。 インデックスが範囲 0 `count`-1 で、ここで`count`によって返される、 [idiaenumframedata::get_count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)メソッドです。  
  
 section  
 [out]返します、 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)目的のフレームのデータ要素を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>参照  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)