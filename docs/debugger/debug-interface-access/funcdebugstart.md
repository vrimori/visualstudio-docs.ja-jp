---
title: FuncDebugStart |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- FuncDebugStart symbol
- debugging [DIA SDK], start point
ms.assetid: 1cbc6ca5-87d0-4c30-a39e-0a9dc62ce1a9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fcfd72850d4bf2b2cd6b33628a0640b7fbe1a17
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919514"
---
# <a name="funcdebugstart"></a>FuncDebugStart
関数をデバッグで定義されたポイントがある場合は、ポイントが、シンボルをで識別されることを開始する、`SymTagFuncDebugStart`タグ。  
  
## <a name="properties"></a>プロパティ  
 次の表では、この記号の型の有効なプロパティを示します。  
  
|プロパティ|データの種類|説明|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|場所のオフセットの部分詳細については、次を参照してください。、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)します。|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|場所のセクションの一部詳細については、次を参照してください。、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)します。|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` 場合は、関数は、カスタム呼び出し規約 (DIA SDK バージョン 8.0 でのみまたはそれ以降) を使用します。|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` 場合 (以降でのみ DIA SDK バージョン 8.0) まで戻り関数を実行します。|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` 関数には、割り込み (DIA SDK バージョン 8.0 でのみまたはそれ以降) からの戻り値が含まれています。 場合、|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` (以降でのみ DIA SDK バージョン 8.0)、この関数は静的とマークされている場合。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|外側の関数の記号。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|構文の親のシンボルの ID。|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|開始点がある静的な場所です。詳細については、次を参照してください。[シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)します。|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` 関数が指定した場合、 [noinline](/cpp/cpp/noinline)属性 (DIA SDK バージョン 8.0 でのみまたはそれ以降)。|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` 関数が指定した場合、 [noreturn](/cpp/cpp/noreturn)属性 (DIA SDK バージョン 8.0 でのみまたはそれ以降)。|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` 関数は、(DIA SDK バージョン 8.0 でのみまたはそれ以降) と呼ばれることはありません。 場合、|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|メモリ内でシンボルをオフセットします。詳細については、次を参照してください。、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)、`LocIsRegRel`します。|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` 場合は、コードでは、(以降でのみ DIA SDK バージョン 8.0)、最適化されたコードのデバッグ情報を持っています。|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|そのブロック内で関数の相対位置。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックス ID。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|返します`SymTagFuncDebugStart`(の 1 つ、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)値)。|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|実行可能ファイル内の関数の位置。|  
  
## <a name="see-also"></a>「  
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)   
 [シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)