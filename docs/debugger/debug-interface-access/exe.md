---
title: "Exe | Microsoft Docs"
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
  - ".dll ファイル"
  - "Exe シンボル"
  - ".exe ファイル"
  - "実行可能ファイル、Exe シンボル"
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

の構文はなしのすべてのグローバル スコープまたは .dll ファイルを表すため唯一のシンボルまたは親が用意されています。  ファイルごとに `SymTagExe` のタグを使用して1 台のシンボルがあります。  [IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md) のメソッドはシンボル。  
  
## プロパティ  
 次の表はこのシンボルの型に対して有効なプロパティを次に示します。  
  
|プロパティ|データ型|Description|  
|-----------|----------|-----------------|  
|[IDiaSymbol::get\_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|この実行可能ファイルの年齢。|  
|[IDiaSymbol::get\_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|この実行可能ファイルの `GUID`。|  
|[IDiaSymbol::get\_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|この実行可能ファイルに関連付けられているシンボル ファイルが C の型が含まれている場合 `TRUE` DIA \(SDK v8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|プライベート シンボルがこの実行可能ファイルに関連付けられているシンボル ファイルから削除されて `TRUE` DIA \(SDK v8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|ターゲット CPU [CV\_CPU\_TYPE\_e 列挙型](../../debugger/debug-interface-access/cv-cpu-type-e.md) の値 \(1\) を示す値。|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|.exe ファイルの名前。|  
|[IDiaSymbol::get\_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|実行可能ファイルの定義。|  
|[IDiaSymbol::get\_symbolsFileName](../Topic/IDiaSymbol::get_symbolsFileName.md)|`BSTR`|.exe ファイルの .pdb または .dbg ファイルの完全パス。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックスの ID。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|`SymTagExe` [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md) の値 \(1\) を返します。|  
  
## 参照  
 [IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md)   
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)