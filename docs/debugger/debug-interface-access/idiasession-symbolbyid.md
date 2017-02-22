---
title: "IDiaSession::symbolById | Microsoft Docs"
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
  - "IDiaSession::symbolById メソッド"
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::symbolById
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

一意識別子によってシンボルを取得します。  
  
## 構文  
  
```cpp#  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### パラメーター  
 `id`  
 \[入力\] 一意の識別子。  
  
 `ppSymbol`  
 \[出力\] 取得されたシンボル [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) を表すオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 指定された識別子はすべてのシンボルを一意にするために DIA SDK によって内部的に使用される一意の値です。  
  
 このメソッドが別のシンボルの型を表すシンボルを取得するにはを使用できます \(例を参照\)。  
  
## 使用例  
 この例では他のシンボルの型を表す [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) を取得します。  この例はセッションで `symbolById` のメソッドを使用する方法を示します。  より簡単な方法は型のシンボルを直接取得するに [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) のメソッドを呼び出します。  
  
```cpp#  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## 参照  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)