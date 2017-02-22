---
title: "定数 (Debug Interface Access SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "定数、DIA SDK"
  - "DIA SDK、定数"
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 定数 (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

これらの文字列定数が DIA SDK によってプログラム デバッグ データベース \(PDB\) ファイルのさまざまな部分を識別するために使用できます。  
  
## 定数  
 次はC\/C\+\+ マクロとして宣言されています。  
  
|マクロ|値|  
|---------|-------|  
|`DiaTable_Symbols`|L " symbol 」は|  
|`DiaTable_Sections`|L " 」|  
|`DiaTable_SrcFiles`|L " 」 SourceFiles|  
|`DiaTable_LineNums`|L " 」 LineNumbers|  
|`DiaTable_SegMap`|L " 」 SegmentMap|  
|`DiaTable_Dbg`|L " 」 Dbg|  
|`DiaTable_InjSrc`|L " 」 InjectedSource|  
|`DiaTable_FrameData`|L " 」 FrameData|  
  
## 使用例  
 この例ではこれらのシンボル 1 を使用して : 次に示します。  
  
```cpp#  
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
  
## 要件  
 ヘッダー : dia2.h  
  
## 参照  
 [参照](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [インターフェイス \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)