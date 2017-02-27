---
title: "IDiaInjectedSource | Microsoft Docs"
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
  - "IDiaInjectedSource インターフェイス"
ms.assetid: 75192c5c-812d-4675-9dc5-4c2cff3ba503
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaInjectedSource
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

アクセスは DIA のデータ ソースに格納されたソース・コードを挿入します。  
  
## 構文  
  
```  
IDiaInjectedSource : IUnknown  
```  
  
## Vtable の順序でメソッド  
 次の表は `IDiaInjectedSource` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[IDiaInjectedSource::get\_crc](../../debugger/debug-interface-access/idiainjectedsource-get-crc.md)|計算されたソース \(CRC\) ・コードを巡回バイトから重複チェックを取得します。|  
|[IDiaInjectedSource::get\_length](../../debugger/debug-interface-access/idiainjectedsource-get-length.md)|コードのバイト数を取得します。|  
|[IDiaInjectedSource::get\_filename](../../debugger/debug-interface-access/idiainjectedsource-get-filename.md)|ソース ファイル名を取得します。|  
|[IDiaInjectedSource::get\_objectFilename](../../debugger/debug-interface-access/idiainjectedsource-get-objectfilename.md)|ソースがコンパイルされたオブジェクト ファイル名を取得します。|  
|[IDiaInjectedSource::get\_virtualFilename](../../debugger/debug-interface-access/idiainjectedsource-get-virtualfilename.md)|非ファイルのソース・コードに割り当てられる名前を取得します ; つまり挿入されたコードにします。|  
|[IDiaInjectedSource::get\_sourceCompression](../Topic/IDiaInjectedSource::get_sourceCompression.md)|使用するソースの圧縮のインジケーターを取得します。|  
|[IDiaInjectedSource::get\_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)|ソース・コードのバイトを取得します。|  
  
## 解説  
 挿入されたソースはコンパイル時に挿入されるテキストです。  これは C\+\+ で使用するプリプロセッサ `#include` を示します。  
  
## 呼び出し元のメモ  
 [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md) または [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md) のメソッドを呼び出してこのインターフェイスを取得します。  `IDiaInjectedSource` インターフェイスを取得する例については[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) のインターフェイスを参照してください。  
  
## 使用例  
 この例では `IDiaInjectedSource` のインターフェイスからデータを表示します。  [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md) のインターフェイスを使用する方法については[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) のインターフェイスの例を参照してください。  
  
```cpp#  
void PrintInjectedSource(IDiaInjectedSource* pSource)  
{  
    ULONGLONG codeLength      = 0;  
    DWORD     crc             = 0;  
    DWORD     compressionType = 0;  
    BSTR      sourceFilename  = NULL;  
    BSTR      objectFilename  = NULL;  
    BSTR      virtualFilename = NULL;  
  
    std::cout << "Injected Source:" << std::endl;  
    if (pSource != NULL)  
    {  
        if (pSource->get_crc(&crc) == S_OK &&  
            pSource->get_sourceCompression(&compressionType) == S_OK &&  
            pSource->get_length(&codeLength) == S_OK)  
        {  
            wprintf(L"  crc = %lu\n", crc);  
            wprintf(L"  code length = %I64u\n",codeLength);  
            wprintf(L"  compression type code = %lu\n", compressionType);  
        }  
  
        wprintf(L"  source filename: ");  
        if (pSource->get_filename(&sourceFilename) == S_OK)  
        {  
            wprintf(L"%s", sourceFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  object filename: ");  
        if (pSource->get_filename(&objectFilename) == S_OK)  
        {  
            wprintf(L"%s", objectFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  virtual filename: ");  
        if (pSource->get_filename(&virtualFilename) == S_OK)  
        {  
            wprintf(L"%s", virtualFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        SysFreeString(sourceFilename);  
        SysFreeString(objectFilename);  
        SysFreeString(virtualFilename);  
    }  
}  
```  
  
## 必要条件  
 ヘッダー : Dia2.h  
  
 ライブラリ : diaguids.lib  
  
 DLL: msdia80.dll  
  
## 参照  
 [インターフェイス \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)   
 [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)