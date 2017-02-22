---
title: "IDiaSymbol::findChildrenExByRVA | Microsoft Docs"
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
  - "IDiaSymbol::findChildrenExByRVA"
ms.assetid: cbc57c6c-7d64-4469-a114-1dd6671e5ec5
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::findChildrenExByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定した相対仮想アドレスに有効なシンボルの子を取得します \(RVA\)。  
  
## 構文  
  
```cpp#  
HRESULT findChildrenExByRVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### パラメーター  
 `symtag`  
 \[入力\] [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md) で定義されている取得する子のシンボルのタグを指定します。  取得するすべての子の `SymTagNull` に設定します。  
  
 `name`  
 \[入力\] 取得する子の名前を指定します。  取得するすべての子の `NULL` に設定します。  
  
 `compareFlags`  
 \[出力\] 一致の名前に適用する比較オプションを指定します。  [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md) の列挙体からの値は単独でまたは組み合わせで使用できます。  
  
 `address`  
 \[出力\] RVA を指定します。  
  
 `ppResult`  
 \[出力\] 取得された子シンボルの一覧を含む [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) のオブジェクトを返します。  
  
## 戻り値  
 子が見つからないシンボルの少なくとも 1 人の子が見つからないまたはその `S_FALSE` を返します `S_OK` を ; それ以外の場合はエラー コード。  
  
## 解説  
 返されたローカル シンボルは有効な範囲の情報が含まれています。  
  
## 必要条件  
 ヘッダー : Dia2.h  
  
 ライブラリ : diaguids.lib  
  
 DLL: msdia100.dll  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md)