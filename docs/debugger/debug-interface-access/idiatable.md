---
title: IDiaTable |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df042bc8edcdf8e93ba775797f1d099b24e90343
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53863723"
---
# <a name="idiatable"></a>IDiaTable
DIA データ ソースのテーブルを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDiaTable`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|取得、 [IEnumVARIANT インターフェイス](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant)この列挙子のバージョン。|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|テーブルの名前を取得します。|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|テーブルの項目の数を取得します。|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|特定のエントリのインデックスへの参照を取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスを実装して、 `IEnumUnknown` Microsoft.VisualStudio.OLE.Interop 名前空間のメソッドを列挙します。 `IEnumUnknown`列挙体インターフェイスはよりもテーブルの内容を反復処理するはるかに効率的ですが、 [idiatable::get_count](../../debugger/debug-interface-access/idiatable-get-count.md)と[idiatable::item](../../debugger/debug-interface-access/idiatable-item.md)メソッド。  
  
 解釈、`IUnknown`インターフェイスのいずれかから返される、`IDiaTable::Item`メソッドまたは`Next`(Microsoft.VisualStudio.OLE.Interop 名前空間の) 内のメソッドはテーブルの種類に依存します。 たとえば場合、`IDiaTable`インターフェイスは、挿入されたソースの一覧を表す、`IUnknown`インターフェイスを照会する必要があります、 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスを呼び出すことによって取得、 [idiaenumtables::item](../../debugger/debug-interface-access/idiaenumtables-item.md)または[idiaenumtables::next](../../debugger/debug-interface-access/idiaenumtables-next.md)メソッド。  
  
 次のインターフェイスが実装されている、`IDiaTable`インターフェイス (つまり、クエリすることができます、`IDiaTable`次のインターフェイスのいずれかのインターフェイス)。  
  
-   [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>例  
 最初の関数では、`ShowTableNames`セッション内のすべてのテーブルの名前を表示します。 2 番目の関数では、 `GetTable`、指定したインターフェイスを実装するテーブルのテーブルのすべてを検索します。 3 番目の関数では、 `UseTable`、使用する方法を示しています、`GetTable`関数。  
  
> [!NOTE]
>  `CDiaBSTR` ラップするクラスは、`BSTR`し、自動的に処理をインスタンス化がスコープから外れたときに、文字列を解放します。  
  
```C++  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )  
            && celt == 1 )  
    {  
        CDiaBSTR bstrTableName;  
        if ( pTable->get_name( &bstrTableName ) != 0 )  
        {  
            Fatal( "get_name" );  
        }  
        printf( "Found table: %ws\n", bstrTableName );  
    }  
  
// Searches the list of all tables for a table that supports  
// the specified interface.  Use this function to obtain an  
// enumeration interface.  
HRESULT GetTable(IDiaSession* pSession,  
                 REFIID       iid,  
                 void**       ppUnk)  
{  
    CComPtr<IDiaEnumTables> pEnumTables;  
    HRESULT hResult;  
  
    if (FAILED(pSession->getEnumTables(&pEnumTables)))  
        Fatal("getEnumTables");  
  
    CComPtr<IDiaTable> pTable;  
    ULONG celt = 0;  
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&  
           celt == 1)  
    {  
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)  
        {  
            return S_OK;  
        }  
        pTable = NULL;  
    }  
  
    if (FAILED(hResult))  
        Fatal("EnumTables->Next");  
  
    return E_FAIL;  
}  
  
// This function shows how to use the GetTable function.  
void UseTable(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pEnumSegments;  
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))  
    {  
        // Do something with pEnumSegments.  
    }  
}  
```  
  
## <a name="requirements"></a>要件  
 ヘッダー:dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>「  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)