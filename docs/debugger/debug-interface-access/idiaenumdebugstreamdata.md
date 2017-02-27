---
title: "IDiaEnumDebugStreamData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumDebugStreamData インターフェイス"
ms.assetid: e2023c32-4c05-4d0c-a0be-f016a230c788
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaEnumDebugStreamData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッグ データ ストリームのレコードへのアクセスを提供します。  
  
## 構文  
  
```  
IDiaEnumDebugStreamData : IUnknown  
```  
  
## Vtable の順序でメソッド  
 次の表は `IDiaEnumDebugStreamData` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[IDiaEnumDebugStreamData::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-newenum.md)|この列挙子の [IEnumVARIANT Interface](http://msdn.microsoft.com/ja-jp/139e3c93-faef-4003-9079-e0e94494db3e) のバージョンを取得します。|  
|[IDiaEnumDebugStreamData::get\_Count](../Topic/IDiaEnumDebugStreamData::get_Count.md)|デバッグ データ ストリーム内のレコード数を取得します。|  
|[IDiaEnumDebugStreamData::get\_name](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-name.md)|デバッグ データ ストリームの名前を取得します。|  
|[IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)|指定されたレコードを取得します。|  
|[IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)|列挙体シーケンスから指定されたレコード数を取得します。|  
|[IDiaEnumDebugStreamData::Skip](../Topic/IDiaEnumDebugStreamData::Skip.md)|列挙体シーケンス内の指定されたレコード数をスキップします。|  
|[IDiaEnumDebugStreamData::Reset](../../debugger/debug-interface-access/idiaenumdebugstreamdata-reset.md)|列挙されたシーケンスを先頭にリセットします。|  
|[IDiaEnumDebugStreamData::Clone](../../debugger/debug-interface-access/idiaenumdebugstreamdata-clone.md)|現在の列挙子と同じ列挙されたシーケンスを含む列挙子を作成します。|  
  
## 解説  
 このインターフェイスはデバッグ データ ストリームのレコードのストリームを表します。  各レコードのサイズと解釈はレコードが取得されるデータのストリームに依存します。  このインターフェイスはシンボル ファイルのバイトの生データへのアクセスを提供します。  
  
## 呼び出し元のメモ  
 `IDiaEnumDebugStreamData` のオブジェクトを取得するに [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md) または [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md) のメソッドを呼び出します。  
  
## 使用例  
 この例では単一のデータ ストリームやレコードにアクセスする方法を示しています。  
  
```cpp#  
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
  
## 必要条件  
 ヘッダー : Dia2.h  
  
 ライブラリ : diaguids.lib  
  
 DLL: msdia80.dll  
  
## 参照  
 [インターフェイス \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)