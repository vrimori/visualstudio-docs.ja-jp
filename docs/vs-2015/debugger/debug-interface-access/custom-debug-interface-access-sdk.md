---
title: カスタム (Debug Interface Access SDK) |Microsoft Docs
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
- Custom symbol
ms.assetid: a219fc83-d2a8-4bc5-b7e1-bfafeb247f16
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 644c3989215bfaa2200a2e1506a0ebf0e881d84a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800381"
---
# <a name="custom-debug-interface-access-sdk"></a>カスタム (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

一部のコンパイラでは、標準の構文の記号の種類のいずれかで識別されていないシンボルを導入します。 これらのシンボルがで識別される、`SymTagCustom`タグ。  
  
## <a name="properties"></a>プロパティ  
 次の表では、この記号の型の有効なプロパティを示します。  
  
|プロパティ|データの種類|説明|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|`BYTE`|シンボルに関連付けられているデータの配列。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックス ID。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|返します`SymTagCustom`(の 1 つ、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)値)。|  
  
## <a name="see-also"></a>関連項目  
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)



