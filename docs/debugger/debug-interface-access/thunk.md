---
title: "サンク | Microsoft Docs"
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
  - "サンクのプロパティ [DIA SDK]"
  - "サンク シンボル"
ms.assetid: 01abb95f-d89a-465c-a4eb-8e8509598c95
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# サンク
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

各 `thunk` は `SymTagThunk` のタグによって識別されます。  
  
## プロパティ  
 次の表はこのシンボルの型に対して有効なプロパティを次に示します。  
  
|プロパティ|データ型|Description|  
|-----------|----------|-----------------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|アクセス修飾子の [CV\_access\_e 列挙型](../../debugger/debug-interface-access/cv-access-e.md)属性の値の V8.0 DIA \(SDK 1 以降でのみ\)。|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|場所のオフセットの一部 ; 詳細については[LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md) を参照してください。|  
|[IDiaSegment::get\_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|`DWORD`|場所のセクションの一部 ; 詳細については[LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md) を参照してください。|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|クラスの親を囲みDIA \(SDK V8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|外側のクラスの親のシンボル ID SDK V8.0 DIA \(以降でのみ\)。|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|サンクを定数としてマークされている場合は TRUE DIA \(SDK V8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|サンクが仮想関数について true DIA \(SDK V8.0 以降でのみ\)|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|サンクが静的として考慮されている場合は TRUE DIA \(SDK V8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|サンクのコードのバイト数。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|外側のコンパイル単位ブロックまたは関数のシンボル。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|構文親のシンボル ID。|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|終点に静的な位置がある ; 詳細については[シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md) の列挙体を参照してください。|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|サンクの名前。|  
|[IDiaSymbol::get\_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|サンクはすべて仮想 True DIA \(SDK V8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|モジュール内のこのサンクの相対位置。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックスの ID。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|`SymTagThunk` [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md) の値 \(1\) を返します。|  
|[IDiaSymbol::get\_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|`DWORD`|サンクのターゲット位置の一部を加算します。|  
|[IDiaSymbol::get\_targetRelativeVirtualAddress](../Topic/IDiaSymbol::get_targetRelativeVirtualAddress.md)|`DWORD`|含むブロックのサンクのターゲットの相対仮想アドレス。|  
|[IDiaSymbol::get\_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|`DWORD`|サンクのターゲットのセクションの部分。|  
|[IDiaSymbol::get\_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|`ULONGLONG`|実行可能イメージのサンクのターゲット位置。|  
|[IDiaSymbol::get\_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|`DWORD`|[THUNK\_ORDINAL 列挙型](../../debugger/debug-interface-access/thunk-ordinal.md) で定義されているサンクの種類。|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|このサンクの種類 \(DIA SDK V8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|型のシンボル ID SDK V8.0 DIA \(以降でのみ\)。|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|サンクが配置される `TRUE` DIA \(SDK V8.0 以降でのみ\)|  
|[IDiaSymbol::get\_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|サンクが仮想モデルの場合 `TRUE` DIA \(SDK V8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|実行可能イメージ内のこのサンクの位置。|  
|[IDiaSymbol::get\_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|このサンクへの仮想テーブルのオフセット \(DIA SDK V8.0 以降でのみ\)。|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|サンクが volatile としてマークされている場合 `TRUE` DIA \(SDK V8.0 以降でのみ\)。|  
  
## 参照  
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)   
 [THUNK\_ORDINAL 列挙型](../../debugger/debug-interface-access/thunk-ordinal.md)