---
title: 定数 (Debug Interface Access SDK) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d625146e1c7777955186100a805e7db8e22e63b6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="constants-debug-interface-access-sdk"></a>定数 (Debug Interface Access SDK)
DIA SDK によってプログラム デバッグ データベース (PDB) ファイルのさまざまなセクションを識別する文字列定数を使用できます。  
  
## <a name="constants"></a>定数  
 次は、C と C++ マクロとして宣言されます。  
  
|マクロ|[値]|  
|-----------|-----------|  
|`DiaTable_Symbols`|L「シンボル」|  
|`DiaTable_Sections`|L「のセクションでは」|  
|`DiaTable_SrcFiles`|L「ソースファイル」|  
|`DiaTable_LineNums`|L"LineNumbers"|  
|`DiaTable_SegMap`|L"SegmentMap"|  
|`DiaTable_Dbg`|L"Dbg"|  
|`DiaTable_InjSrc`|L"InjectedSource"|  
|`DiaTable_FrameData`|L"FrameData"|  
  
## <a name="example"></a>例  
 これらのシンボルのいずれかの使用例を次に示します。  
  
```C++  
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)  
{  
    HRESULT hr;  
    VARIANT var;  
    var.vt      = VT_BSTR;  
    var.bstrVal = SysAllocString( DiaTable_Symbols );  
    hr = pEnumTables->Item( var, pTable );  
    return(hr);  
}  
```  
  
## <a name="requirements"></a>要件  
 ヘッダー: dia2.h  
  
## <a name="see-also"></a>関連項目  
 [参照](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)