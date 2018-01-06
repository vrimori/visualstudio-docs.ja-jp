---
title: "ブロック |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- SymTagBlock symbol
- nested scopes
- Block symbol
ms.assetid: 95b7b0c1-ecc9-405f-8456-5f9cfb866498
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 637758d8d66095ddf1d986c6abf638fc7e1ab548
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="block"></a>ブロック
各コード ブロックがによって識別される、`SymTagBlock`シンボル。 ブロック シンボルを使用して、関数内で入れ子になったスコープを識別します。  
  
## <a name="properties"></a>プロパティ  
 次の表は、この記号の型の有効なプロパティを示します。  
  
|プロパティ|データの種類|説明|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|オフセットの部分の場所です。詳細については、次を参照してください。、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)です。|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|場所のセクションの一部詳細については、次を参照してください。、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)です。|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|ブロック内のコードのバイト数。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|外側のブロックまたは関数の記号。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|構文上の親の記号の ID を返します。|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|ブロックがある静的な場所です。詳細については、「[シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)です。|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|(これは、空の文字列では通常) ブロックの名前を返します。|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|構文上の親を基準としたこのブロックの仮想アドレスを返します。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックスの ID。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|返します`SymTagBlock`(のいずれか、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)値)。|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|このブロック内に実行可能ファイルの仮想アドレスを返します。|  
  
## <a name="see-also"></a>参照  
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)   
 [シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)