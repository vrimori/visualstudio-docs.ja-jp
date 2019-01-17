---
title: Idiaenumdebugstreams::item |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Item method
ms.assetid: 6b388fe1-eabc-4720-9d59-dc09b0ceaeac
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e098f15238cdf84121cae81685191047c4b04447
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963341"
---
# <a name="idiaenumdebugstreamsitem"></a>IDiaEnumDebugStreams::Item
インデックスまたは名前を使用してデバッグ ストリームを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Item (   
   VARIANT                   index,  
   IDiaEnumDebugStreamData** stream  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 インデックス  
 [in]インデックスまたはデバッグ ストリームの名前を取得します。 0 の範囲の場合は、整数のバリアントを使用すると、必要があります`count`-1 の場合、`count`によって返されるは、 [idiaenumdebugstreams::get_count](../../debugger/debug-interface-access/idiaenumdebugstreams-get-count.md)メソッド。  
  
 ストリーム  
 [out]返します、 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)指定されたデバッグ ストリームを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="example"></a>例  
  
```C++  
IDiaEnumDebugStreamData *GetStreamData(IDiaEnumDebugStreams *pStreamList,  
                                       LONG whichStream)  
{  
    IDiaEnumDebugStreamData *pStreamData = NULL;  
    if (pStreamList != NULL)  
    {  
        LONG numStreams = 0;  
        if (pStreamList->get_count(&numStreams) == S_OK &&  
            whichStream >= 0 && whichStream < numStreams)  
        {  
            VARIANT vIndex;  
            vIndex.vt   = VT_I4;  
            vIndex.lVal = whichStream;  
            if (pStreamList->Item(vIndex,&pStreamData) != S_OK)  
            {  
                 std::cerr << "Error retrieving stream " << whichStream << std::endl;  
            }  
        }  
    }  
    return(pStreamData);  
}  
```  
  
## <a name="see-also"></a>「  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)