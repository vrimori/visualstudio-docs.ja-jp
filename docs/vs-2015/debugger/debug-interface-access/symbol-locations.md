---
title: シンボルの場所 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- LocationType values
- symbols [DIA SDK], locations
ms.assetid: 7c8cd8fe-169e-4161-9cff-5e9015984add
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 88d8fd37babea18aa385598cad12436b414f5ff8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284636"
---
# <a name="symbol-locations"></a>シンボルの場所
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ほとんどのシンボル、イメージ ファイル内で定義されている場所であります。 値を持つシンボルの場所が指定されて、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)列挙体。 シンボルの場所に応じて他のプロパティをサポート可能性があります。  
  
 次の表では、最もよく使用される場所の種類とその他のプロパティを示します。  
  
|場所の種類|追加のプロパティ|  
|-------------------|---------------------------|  
|`LocIsNull`|none|  
|`LocIsStatic`|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)<br /><br /> [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [Idiasymbol::get_relativevirtualaddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md) (相対仮想アドレスは有効な場合)<br /><br /> [Idiasymbol::get_virtualaddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md) (イメージ ベースは 0 以外に設定されている) 場合|  
|`LocIsTLS`|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|  
|`LocIsRegRel`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsThisRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsEnregistered`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|  
|`LocIsBitField`|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)<br /><br /> [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsSlot`|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|  
|`LocIsIlRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocInMetaData`|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|  
|`LocIsConstant`|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|  
  
## <a name="see-also"></a>関連項目  
 [Idiasymbol::get_addressoffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)   
 [Idiasymbol::get_addresssection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [Idiasymbol::get_bitposition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)   
 [Idiasymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)   
 [Idiasymbol::get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Idiasymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)   
 [Idiasymbol::get_registerid](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)   
 [Idiasymbol::get_relativevirtualaddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)   
 [Idiasymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)   
 [Idiasymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)   
 [Idiasymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)   
 [Idiasymbol::get_virtualaddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)   
 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)   
 [シンボルとシンボル タグ](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)



