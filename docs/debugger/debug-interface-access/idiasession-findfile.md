---
title: "IDiaSession::findFile | Microsoft Docs"
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
  - "IDiaSession::findFile メソッド"
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findFile
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

コンパイル単位と名前でソース ファイルを取得します。  
  
## 構文  
  
```cpp#  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### パラメーター  
 `pCompiland`  
 \[入力\] 検索のコンテキストとして使用するコンパイル単位を表す [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) オブジェクト。  すべてのコンパイル単位でソース ファイルを検索するには、このパラメーターを `NULL` に設定します。  
  
 `name`  
 \[入力\] 取得するソース ファイルの名前を指定します。  取得するすべてのソース ファイルについて、このパラメーターを `NULL` に設定します。  
  
 `option`  
 \[入力\] 名前の検索に適用される比較オプションを指定します。  [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md) 列挙型の値を単独で、または組み合わせて使用できます。  
  
 `ppResult`  
 \[出力\] 取得されたソース ファイルの一覧を含む [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) オブジェクトを返します。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合はエラー コードを返します。  
  
## 使用例  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## 参照  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md)