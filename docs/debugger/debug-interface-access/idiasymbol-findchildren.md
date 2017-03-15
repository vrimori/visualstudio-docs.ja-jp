---
title: "IDiaSymbol::findChildren | Microsoft Docs"
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
  - "IDiaSymbol::findChildren メソッド"
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

シンボルの子を取得します。  
  
## 構文  
  
```cpp#  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### パラメーター  
 `symtag`  
 \[入力\] [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md) で定義されている取得する子のシンボルのタグを指定します。  取得するすべての子の `SymTagNull` に設定します。  
  
 `name`  
 \[入力\] 取得する子の名前を指定します。  取得するすべての子の `NULL` に設定します。  
  
 `compareFlags`  
 \[出力\] 一致の名前に適用される比較オプションを指定します。  [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md) の列挙体からの値は単独でまたは組み合わせで使用できます。  
  
 `ppResult`  
 \[出力\] 取得された子シンボルの一覧を含む [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) のオブジェクトを返します。  
  
## 戻り値  
 子が見つからないシンボルの少なくとも 1 人の子が見つからないまたはその `S_FALSE` を返します `S_OK` を ; それ以外の場合はエラー コードを返します。  
  
## 解説  
 このメソッドは最初のパラメーターにこのシンボルを持つ [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) のメソッドを呼び出すことと同じです。  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md)