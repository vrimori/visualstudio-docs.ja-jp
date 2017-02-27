---
title: "IDiaSession::findChildren | Microsoft Docs"
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
  - "IDiaSession::findChildren メソッド"
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

シンボルの名前と型に一致する場合は指定された親の識別子のすべての子を取得します。  
  
## 構文  
  
```cpp#  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### パラメーター  
 `parent`  
 \[入力\] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) に親。  この親のシンボルが関数モジュールまたはブロックの場合構文は子 `ppResult` に返されます。  親のシンボルが型の場合クラスの子が返されます。  このパラメーターがの場合`NULL``symtag` は `SymTagExe` または `SymTagNull` にグローバル スコープ \(.exe ファイル\) を返す設定する必要があります。  
  
 `symtag`  
 \[入力\] 取得する子のシンボルのタグを指定します。  値は [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md) の列挙体から取得されます。  すべての子を取得するために `SymTagNull` に設定します。  
  
 `name`  
 \[入力\] 取得する子の名前を指定します。  取得するすべての子の `NULL` に設定します。  
  
 `compareFlags`  
 \[出力\] 一致の名前に適用される比較オプションを指定します。  [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md) の列挙体からの値は単独でまたは組み合わせで使用できます。  
  
 `ppResult`  
 \[出力\] 取得された子シンボルの一覧を含む [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 使用例  
 次の例に `pFunc` 関数のローカル変数を検索する方法がに一致の名前 `szVarName` 示します。  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## 参照  
 [概要](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)