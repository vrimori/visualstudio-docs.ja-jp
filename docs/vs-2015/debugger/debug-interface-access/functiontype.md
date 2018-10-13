---
title: FunctionType |Microsoft Docs
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
- function signature
- FunctionType symbol
ms.assetid: 646a07e7-9d4f-4e21-95e3-3e403cdd4843
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e56c038ef0dc3cb9b60f060914923cae3070894f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298091"
---
# <a name="functiontype"></a>FunctionType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

各一意の関数シグネチャがで識別される、`SymTagFunctionType`シンボル。 各パラメーターは、クラスの子シンボルとして識別される、`SymTagFunctionArgType`タグ。  
  
## <a name="properties"></a>プロパティ  
 次の表では、この記号の型の有効な追加のプロパティを示します。  
  
|プロパティ|データの種類|説明|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|`DWORD`|値の 1 つ、 [CV_call_e 列挙型](../../debugger/debug-interface-access/cv-call-e.md)します。|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|クラスのこの関数 (またはメソッド) のメンバーであること。|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|クラスの親のシンボルの ID。|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` 場合は、関数は定数としてマークされます。|  
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|`DWORD`|関数パラメーターの数。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|外側のコンパイル単位シンボル。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|構文の親のシンボルの ID。|  
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|`IDiaSymbol*`|("This")、メソッドのオブジェクト ポインターの型。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックス ID。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|返します`SymTagFunctionType`(の 1 つ、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)値)。|  
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|`LONG`|論理メソッドの場合は、"this"調整権限を保持します。|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|戻り値の型の記号。|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|型のシンボルの ID。|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` 場合は、関数は、整列されていません。|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` 場合は、関数は、volatile としてマークされます。|  
  
## <a name="see-also"></a>関連項目  
 [シンボル型のクラス階層](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [CV_access_e 列挙型](../../debugger/debug-interface-access/cv-access-e.md)   
 [FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)



