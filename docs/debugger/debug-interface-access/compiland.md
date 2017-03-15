---
title: "コンパイル単位 | Microsoft Docs"
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
  - "コンパイル単位シンボル"
  - "コンパイル単位、コンパイル単位シンボル"
ms.assetid: c798eb2b-664a-41ec-ae90-5e9d292507ca
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# コンパイル単位
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

.exe ファイルにリンクする各コンパイル単位の `SymTagCompiland` の 1 種類のシンボルがあります。  コンパイル単位の追加情報はコンパイル単位のシンボルを読み込むに取得できると追加のシンボルを読み込む必要になる場合があります `SymTagCompilandDetails` のタグが付いたシンボル分割されます `SymTagCompiland` のタグが付いたシンボルの間で。  
  
## プロパティ  
 次の表はこのシンボルの型に対して有効なプロパティを次に示します。  
  
|プロパティ|データ型|Description|  
|-----------|----------|-----------------|  
|[IDiaSymbol::get\_editAndContinueEnabled](../Topic/IDiaSymbol::get_editAndContinueEnabled.md)|`BOOL`|エディット コンティニュはコンパイルで有効になっている場合 `TRUE`。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|.exe ファイルのシンボル。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|構文親のシンボル ID。|  
|[IDiaSymbol::get\_libraryName](../Topic/IDiaSymbol::get_libraryName.md)|`BSTR`|オブジェクトが読み込まれたライブラリまたはオブジェクト ファイルの名前。|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|コンパイル単位のオブジェクト ファイルの名前。|  
|[IDiaSymbol::get\_sourceFileName](../Topic/IDiaSymbol::get_sourceFileName.md)|`BSTR`|ソース ファイルの名前。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックスの ID。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|`SymTagCompiland` [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md) の値 \(1\) を返します。|  
  
## 参照  
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)   
 [CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)   
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)