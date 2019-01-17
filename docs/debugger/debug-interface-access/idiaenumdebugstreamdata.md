---
title: IDiaEnumDebugStreamData |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData interface
ms.assetid: e2023c32-4c05-4d0c-a0be-f016a230c788
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9bf1fdf790878097c9d777ba8eae5386593bccb4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989712"
---
# <a name="idiaenumdebugstreamdata"></a>IDiaEnumDebugStreamData
デバッグのデータ ストリーム内のレコードへのアクセスを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaEnumDebugStreamData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDiaEnumDebugStreamData`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaEnumDebugStreamData::get__NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-newenum.md)|取得、 [IEnumVARIANT インターフェイス](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant)この列挙子のバージョン。|  
|[IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)|デバッグのデータ ストリーム内のレコードの数を取得します。|  
|[IDiaEnumDebugStreamData::get_name](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-name.md)|デバッグのデータ ストリームの名前を取得します。|  
|[IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)|指定されたレコードを取得します。|  
|[IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)|列挙のシーケンスから指定されたレコード数を取得します。|  
|[IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)|指定された数の列挙のシーケンス内のレコードをスキップします。|  
|[IDiaEnumDebugStreamData::Reset](../../debugger/debug-interface-access/idiaenumdebugstreamdata-reset.md)|列挙のシーケンスを先頭にリセットします。|  
|[IDiaEnumDebugStreamData::Clone](../../debugger/debug-interface-access/idiaenumdebugstreamdata-clone.md)|現在の列挙子と同じ列挙型のシーケンスを格納する列挙子を作成します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、デバッグ データのストリーム内のレコードのストリームを表します。 各レコードの解釈とサイズは、レコードの取得元のデータ ストリームに依存します。 このインターフェイスは、シンボル ファイルの生データのバイトへのアクセスを効果的に提供します。  
  
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
  
## <a name="requirements"></a>要件  
 ヘッダー:dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>「  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)