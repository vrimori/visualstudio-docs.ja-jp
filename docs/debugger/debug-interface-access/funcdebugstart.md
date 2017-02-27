---
title: "FuncDebugStart | Microsoft Docs"
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
  - "FuncDebugStart シンボル"
  - "デバッグ [DIA SDK]、始点"
ms.assetid: 1cbc6ca5-87d0-4c30-a39e-0a9dc62ce1a9
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# FuncDebugStart
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

関数のデバッグを開始するに指定された点がある場合そのポイントは `SymTagFuncDebugStart` のタグが付いたシンボルによって識別されます。  
  
## プロパティ  
 次の表はこのシンボルの型に対して有効なプロパティを次に示します。  
  
|プロパティ|データ型|Description|  
|-----------|----------|-----------------|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|場所のオフセットの一部 ; 詳細については[LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md) を参照してください。|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|場所のセクションの一部 ; 詳細については[LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md) を参照してください。|  
|[IDiaSymbol::get\_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|関数がカスタム呼び出し規約を使用する場合 `TRUE` DIA \(SDK v8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|関数がを返す場合`TRUE` DIA \(SDK v8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|関数が割り込みからの戻り値が含まれている場合 `TRUE` DIA \(SDK v8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|関数が静的としてマークされている場合 `TRUE` DIA \(SDK v8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|外側の関数のシンボル。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|構文親のシンボル ID。|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|始点に静的な位置がある ; 詳細については[シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md) を参照してください。|  
|[IDiaSymbol::get\_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|関数が [noinline](/visual-cpp/cpp/noinline) の属性が指定されている場合は `TRUE` DIA \(SDK v8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|関数が [noreturn](/visual-cpp/cpp/noreturn) の属性が指定されている場合は `TRUE` DIA \(SDK v8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|関数が呼び出される `TRUE` する DIA \(SDK v8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|メモリのシンボルのオフセット ; 詳細については[LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)`LocIsRegRel` を参照してください。|  
|[IDiaSymbol::get\_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|コードに最適化されたコードのデバッグ情報がある場合 `TRUE` DIA \(SDK v8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|ブロック内の関数の相対位置。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックスの ID。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|`SymTagFuncDebugStart` [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md) の値 \(1\) を返します。|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|実行可能ファイル内の関数の位置。|  
  
## 参照  
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)   
 [シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)