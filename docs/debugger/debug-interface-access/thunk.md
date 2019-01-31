---
title: サンク |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- thunk properties [DIA SDK]
- thunk symbol
ms.assetid: 01abb95f-d89a-465c-a4eb-8e8509598c95
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1012053d3c63f9da18120dd3ccaa652ffc2301a8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070371"
---
# <a name="thunk"></a>サンク
各`thunk`で識別される、`SymTagThunk`タグ。  
  
## <a name="properties"></a>プロパティ  
 次の表では、この記号の型の有効なプロパティを示します。  
  
|プロパティ|データの種類|説明|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|いずれかのアクセス修飾子 属性、 [CV_access_e 列挙型](../../debugger/debug-interface-access/cv-access-e.md)(DIA SDK バージョン 8.0 でのみまたはそれ以降) の値。|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|場所のオフセットの部分詳細については、次を参照してください。、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)します。|  
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|`DWORD`|場所のセクションの一部詳細については、次を参照してください。、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)します。|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|(DIA SDK バージョン 8.0 の下でのみまたはそれ以降) が存在する場合は、クラスの親を囲みます。|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|それを囲むクラス親シンボル (DIA SDK バージョン 8.0 でのみまたはそれ以降) の ID。|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|サンクが (DIA SDK バージョン 8.0 でのみまたはそれ以降) の定数としてマークされている場合は TRUE。|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|サンクは仮想関数 (DIA SDK バージョン 8.0 でのみまたはそれ以降) の概要については、TRUE を返します。|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|TRUE の場合、サンクと見なされます静的 (DIA SDK バージョン 8.0 でのみまたはそれ以降)。|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|サンクのコードのバイト数。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|外側のコンパイル単位、ブロック、または関数の記号。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|構文の親のシンボルの ID。|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|終了ポイントがある静的な場所です。詳細については、次を参照してください。[シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)列挙体。|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|サンクの名前。|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|(以降でのみ DIA SDK バージョン 8.0) は、サンクが純粋仮想の場合は TRUE。|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|そのモジュール内でこのサンクの相対位置。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックス ID。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|返します`SymTagThunk`(の 1 つ、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)値)。|  
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|`DWORD`|サンク ターゲットの場所のオフセットの部分。|  
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|`DWORD`|サンク ターゲット、それを囲むブロック内の相対仮想アドレス。|  
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|`DWORD`|サンク ターゲットのセクションの一部です。|  
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|`ULONGLONG`|実行可能イメージ内のサンク ターゲットの位置。|  
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|`DWORD`|定義されている型のサンク、 [THUNK_ORDINAL 列挙型](../../debugger/debug-interface-access/thunk-ordinal.md)します。|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|このサンク (DIA SDK バージョン 8.0 でのみまたはそれ以降) の型。|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|型のシンボル (DIA SDK バージョン 8.0 でのみまたはそれ以降) の ID。|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` (以降でのみ DIA SDK バージョン 8.0)、サンクがアラインされていない場合|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` 場合は、サンク仮想 (だけには DIA SDK バージョン 8.0 以降) です。|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|このサンク実行可能イメージ内の位置。|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|このサンク (DIA SDK バージョン 8.0 でのみまたはそれ以降) を仮想テーブル内のオフセット。|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` 場合は、サンクは、揮発性 (以降でのみ DIA SDK バージョン 8.0) としてマークされます。|  
  
## <a name="see-also"></a>「  
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)   
 [THUNK_ORDINAL 列挙型](../../debugger/debug-interface-access/thunk-ordinal.md)