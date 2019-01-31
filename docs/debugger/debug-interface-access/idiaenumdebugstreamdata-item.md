---
title: Idiaenumdebugstreamdata::item |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Item method
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff59abc8aa0db3d25a42b443cccdc20084dd0d11
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031183"
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
 [in]取得するレコードのインデックス。 インデックスは 0 ~ の範囲内で、 `count`-1 の場合、`count`によって返される[idiaenumdebugstreamdata::get_count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)します。  
  
 cbData  
 [in](バイト単位)、データ バッファーのサイズ。  
  
 pcbData  
 [out]返されるバイト数を返します。 場合`data`は`NULL`、し`pcbData`指定されたレコードで使用できるデータのバイト数合計にはが含まれています。  
  
 data[]  
 [out]デバッグ ストリーム レコードのデータが入力バッファー。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 返します`E_INVALIDARG`無効なパラメーターの場合、`index`パラメーターが範囲外です。  
  
## <a name="see-also"></a>「  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)   
 [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)   
 [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)