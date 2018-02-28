---
title: "Idiaenumdebugstreamdata::item |Microsoft ドキュメント"
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
helpviewer_keywords:
- IDiaEnumDebugStreamData::Item method
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bc1d2fb208cdc59fa8915d61d11e37f137014ecc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumdebugstreamdataitem"></a>IDiaEnumDebugStreamData::Item
指定されたレコードを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Item (   
   DWORD  index,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 インデックス  
 [in]取得するレコードのインデックス。 インデックスが範囲 0 `count`-1 で、ここで`count`によって返される[idiaenumdebugstreamdata::get_count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)です。  
  
 cbData  
 [in](バイト単位)、データ バッファーのサイズ。  
  
 pcbData  
 [out]返されるバイト数を返します。 場合`data`は`NULL`、し`pcbData`指定されたレコードで使用できるデータのバイト数合計にはが含まれています。  
  
 データ  
 [out]デバッグ ストリーム レコードのデータが入力バッファー。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 返します`E_INVALIDARG`無効なパラメーターの場合は、`index`パラメーターが範囲外です。  
  
## <a name="see-also"></a>参照  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [Idiaenumdebugstreamdata::next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)   
 [Idiaenumdebugstreams::item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [Idiaenumdebugstreamdata::get_count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)   
 [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)