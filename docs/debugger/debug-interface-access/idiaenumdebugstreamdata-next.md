---
title: "Idiaenumdebugstreamdata::next |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2fda26c6ed92a255e25bdbbe836a691ba80752e7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
指定した列挙のシーケンス内のレコード数を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Next (   
   ULONG  celt,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[],  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 celt  
 [in]取得するレコードの数。  
  
 cbData  
 [in](バイト単位)、データ バッファーのサイズ。  
  
 pcbData  
 [out]返されるバイト数を返します。 場合`data`が NULL の場合、`pcbData`要求されたすべてのレコードの合計使用可能なデータのバイト数が含まれています。  
  
 データ  
 [out]デバッグ ストリーム レコードのデータを格納するバッファー。  
  
 pceltFetched  
 [入力、出力].内のレコードの数を返します`data`です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`レコードがある場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>参照  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)