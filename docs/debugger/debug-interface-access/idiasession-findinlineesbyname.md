---
title: "IDiaSession::findInlineesByName | Microsoft Docs"
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
ms.assetid: 9860336d-f703-4ecb-bfc4-3f5beb175a76
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineesByName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

クライアントが、指定した名前に一致するすべてのインライン関数の行番号情報を反復処理できる列挙型を取得します。  
  
## 構文  
  
```cpp#  
HRESULT findInlineesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### パラメーター  
 `name`  
 \[出力\] 名前が比較に使用するを指定します。  
  
 `option`  
 \[入力\] 名前の検索に適用される比較オプションを指定します。  [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md) 列挙型の値を単独で、または組み合わせて使用できます。  
  
 `ppResult`  
 \[出力\] 取得された行番号の一覧を含む [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) のオブジェクトを返します。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合はエラー コードを返します。  
  
## 参照  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)