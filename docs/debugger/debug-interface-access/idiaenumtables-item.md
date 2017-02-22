---
title: "IDiaEnumTables::Item | Microsoft Docs"
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
  - "IDiaEnumTables::Item メソッド"
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumTables::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

インデックスまたは名前でテーブルを取得します。  
  
## 構文  
  
```cpp#  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### パラメーター  
 `index`  
 \[入力\] 取得する [IDiaTable](../../debugger/debug-interface-access/idiatable.md) のキーの名前。  整数のバリアントを使用すると`count` が [IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) のメソッドによって返されるように設定されている `count`0 ~ \-1 にする必要があります。  
  
 `table`  
 \[入力\] [IDiaTable](../../debugger/debug-interface-access/idiatable.md) テーブルを表すオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 文字列のバリアントを指定すると文字列名特定のテーブル。  名前は [定数 \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md) で定義されているテーブル名の 1 つが必要があります。  
  
## 使用例  
  
```cpp#  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## 参照  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [定数 \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)