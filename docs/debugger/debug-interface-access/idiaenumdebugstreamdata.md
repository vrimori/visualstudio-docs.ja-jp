---
title: "IDiaEnumDebugStreamData |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumDebugStreamData interface
ms.assetid: e2023c32-4c05-4d0c-a0be-f016a230c788
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 31e7f3415a502d2bf7737a498f235fd38a75ec48
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumdebugstreamdata"></a>IDiaEnumDebugStreamData
デバッグ データ ストリーム内のレコードへのアクセスを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaEnumDebugStreamData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDiaEnumDebugStreamData`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaEnumDebugStreamData::get__NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-newenum.md)|取得、 [IEnumVARIANT インターフェイス](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e)この列挙子のバージョン。|  
|[IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)|デバッグ データ ストリーム内のレコードの数を取得します。|  
|[IDiaEnumDebugStreamData::get_name](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-name.md)|デバッグ データ ストリームの名前を取得します。|  
|[IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)|指定されたレコードを取得します。|  
|[IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)|列挙のシーケンスから指定されたレコード数を取得します。|  
|[IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)|指定した列挙のシーケンス内のレコード数をスキップします。|  
|[IDiaEnumDebugStreamData::Reset](../../debugger/debug-interface-access/idiaenumdebugstreamdata-reset.md)|列挙のシーケンスを先頭にリセットします。|  
|[IDiaEnumDebugStreamData::Clone](../../debugger/debug-interface-access/idiaenumdebugstreamdata-clone.md)|現在の列挙子として同じ列挙のシーケンスを含む列挙子を作成します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、デバッグ データ ストリーム内のレコードのストリームを表します。 各レコードの解釈とサイズは、レコードの取得元のデータ ストリームに依存します。 このインターフェイスは、実質的にシンボル ファイルに生データのバイトへのアクセスを提供します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す、 [idiaenumdebugstreams::item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)または[idiaenumdebugstreams::next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)を取得する方法、`IDiaEnumDebugStreamData`オブジェクト。  
  
## <a name="example"></a>例  
 この例では、1 つのデータ ストリームとそのレコードにアクセスする方法を示します。  
  
```C++  
void PrintStreamData(IDiaEnumDebugStreamData* pStream)  
{  
    BSTR  wszName;  
    LONG  dwElem;  
    ULONG celt    = 0;  
    DWORD cbData;  
    DWORD cbTotal = 0;  
    BYTE  data[1024];  
  
    if(pStream->get_name(&wszName) != S_OK)  
    {  
        wprintf_s(L"ERROR - PrintStreamData() get_name\n");  
    }  
    else  
    {  
        wprintf_s(L"Stream: %s", wszName);  
        SysFreeString(wszName);  
    }  
    if(pStream->get_Count(&dwElem) != S_OK)  
    {  
        wprintf(L"ERROR - PrintStreamData() get_Count\n");  
    }  
    else  
    {  
        wprintf(L"(%d)\n", dwElem);  
    }  
    while(pStream->Next(1, sizeof(data), &cbData, (BYTE *)&data, &celt) == S_OK)  
    {  
        DWORD i;  
        for (i = 0; i < cbData; i++)  
        {  
            wprintf(L"%02X ", data[i]);  
            if(i && i % 8 == 7 && i+1 < cbData)  
            {  
                wprintf(L"- ");  
            }  
        }  
        wprintf(L"| ");  
        for(i = 0; i < cbData; i++)  
        {  
            wprintf(L"%c", iswprint(data[i]) ? data[i] : '.');  
        }  
        wprintf(L"\n");  
        cbTotal += cbData;  
    }  
    wprintf(L"Summary :\n\tSizeof(Elem) = %d\n\tNo of Elems = %d\n\n",  
            cbTotal/dwElem, dwElem);  
}  
```  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>参照  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenumdebugstreams::item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)