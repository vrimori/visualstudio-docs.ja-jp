---
title: CompilandEnv |Microsoft Docs
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
- CompilandEnv symbol
ms.assetid: 808404bb-ece1-47f1-b9ea-c76d4d86ddd9
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 157a8e4a483c5c8ef57eaa6adbdb54b74fa82178
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757631"
---
# <a name="compilandenv"></a>CompilandEnv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

コンパイラは、シンボルを使用した追加の環境変数を含めることができます。 1 つである`SymTagCompilandEnv`の各変数の記号。  
  
## <a name="properties"></a>プロパティ  
 次の表では、この記号の型の有効なプロパティを示します。  
  
|プロパティ|データの種類|説明|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|親のコンパイル単位の記号。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|構文の親のシンボルの ID。|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|変数の名前。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックス ID。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|返します`SymTagCompilandEnv`(の 1 つ、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)値)。|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|変数の内容を文字列値 (`VT_BSTR`)。|  
  
## <a name="see-also"></a>関連項目  
 [コンパイル単位](../../debugger/debug-interface-access/compiland.md)   
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)



