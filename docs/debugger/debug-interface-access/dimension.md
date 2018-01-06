---
title: "ディメンション |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Dimension Symbol
ms.assetid: 94f791da-bfea-454f-8a14-da31e8e1596a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 613ce44699f76715d7ca00f1afba132c168573af
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="dimension"></a>ディメンション
各 FORTRAN 配列によって識別されるディメンションには、`SymTagDimension`シンボル。  
  
## <a name="properties"></a>プロパティ  
 次の表は、この記号の型の他の有効なプロパティを示します。  
  
|プロパティ|データの種類|説明|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|`IDiaSymbol*`|FORTRAN 配列の次元の下限値です。|  
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|`DWORD`|下限のシンボルの ID です。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックスの ID。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|返します`SymTagDimension`(のいずれか、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)値)。|  
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|`IDiaSymbol*`|FORTRAN 配列の次元の上限値です。|  
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|`DWORD`|上限は、シンボルの ID です。|  
  
## <a name="see-also"></a>参照  
 [ArrayType](../../debugger/debug-interface-access/arraytype.md)   
 [シンボル型のクラス階層](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)