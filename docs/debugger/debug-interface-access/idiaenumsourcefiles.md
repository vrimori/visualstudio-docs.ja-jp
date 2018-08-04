---
title: IDiaEnumSourceFiles |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles interface
ms.assetid: 5c0779a6-a2ea-408a-90da-ebdecf2b83c0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33960cf8cfde8d781d52e0519911093019a93941
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511025"
---
# <a name="idiaenumsourcefiles"></a>IDiaEnumSourceFiles
データ ソースに含まれるさまざまなソース ファイルを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaEnumSourceFiles : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDiaEnumSourceFiles`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaEnumSourceFiles::get__NewEnum](../../debugger/debug-interface-access/idiaenumsourcefiles-get-newenum.md)|取得、`IEnumVARIANT Interface`この列挙子のバージョン。|  
|[IDiaEnumSourceFiles::get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md)|ソース ファイルの数を取得します。|  
|[IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)|インデックスを使用してソース ファイルを取得します。|  
|[IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)|列挙体シーケンス内のソース ファイルの指定した数を取得します。|  
|[IDiaEnumSourceFiles::Skip](../../debugger/debug-interface-access/idiaenumsourcefiles-skip.md)|指定された数の列挙体シーケンス内のソース ファイルをスキップします。|  
|[IDiaEnumSourceFiles::Reset](../../debugger/debug-interface-access/idiaenumsourcefiles-reset.md)|先頭に、列挙体シーケンスをリセットします。|  
|[IDiaEnumSourceFiles::Clon](../../debugger/debug-interface-access/idiaenumsourcefiles-clone.md)|現在の列挙子と同じ列挙状態を格納する列挙子を作成します。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスを呼び出すことによって取得、`QueryInterface`メソッドを[IDiaTable](../../debugger/debug-interface-access/idiatable.md)オブジェクト。 詳細については、例を参照してください。  
  
## <a name="example"></a>例  
 この例は、取得する方法を示します、 `IDiaEnumSourceFiles` DIA のセッション オブジェクト内のテーブルの一覧からインターフェイス。 ソース ファイルの情報へのアクセスの例は、次を参照してください。、 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)インターフェイス。  
  
```C++  
  
IDiaEnumSourceFiles* GetEnumSourceFiles(IDiaSession *pSession)  
{  
    IDiaEnumSourceFiles * pUnknown    = NULL;  
    REFIID                iid         = __uuidof(IDiaEnumSourceFiles);  
    IDiaEnumTables*       pEnumTables = NULL;  
    IDiaTable*            pTable      = NULL;  
    ULONG                 celt        = 0;  
  
    if (pSession->getEnumTables(&pEnumTables) != S_OK)  
    {  
        wprintf(L"ERROR - GetTable() getEnumTables\n");  
        return NULL;  
    }  
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)  
    {  
        // There is only one table that matches the given iid  
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);  
        pTable->Release();  
        if (hr == S_OK)  
        {  
            break;  
        }  
    }  
    pEnumTables->Release();  
    return pUnknown;  
}  
```  
  
## <a name="requirements"></a>要件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>関連項目  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiasession::findfile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [Idiasession::findlinesbylinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)