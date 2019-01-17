---
title: シンボル型の階層をクラス |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa257de86367f2531cce5c57080cd059856fa82a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902855"
---
# <a name="class-hierarchy-of-symbol-types"></a>シンボル型のクラス階層
次の表では、クラス階層内のシンボルの型について説明します。  
  
## <a name="symbol-types"></a>シンボル型  
  
|記号の型|説明|  
|-----------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|各クラス、構造、および和集合を表すために使用する記号です。|  
|[Enum (Debug Interface Access SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|列挙型の記号。|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|ポインター型の記号。|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|配列型の記号です。|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|基本型のシンボル|  
|[Typedef (Debug Interface Access SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|その他の種類の名前を導入する記号です。|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|ユーザー定義型 (UDT) の各基底クラスに使用する記号。|  
|[フレンド (Debug Interface Access SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|フレンド クラスのフレンド関数記号です。|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|各一意の関数シグネチャの記号。|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|関数の各パラメーターの記号。|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|仮想テーブルのサイズの記号。|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|仮想テーブルを表す記号です。|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|ベンダ定義の型の記号。|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|メタデータで定義された型を表す記号です。|  
|[ディメンション](../../debugger/debug-interface-access/dimension.md)|配列の次元の記号。|  
  
> [!NOTE]
>  各シンボルはシンボルとその他のシンボルへの参照に関する情報を保持するプロパティを持つことができます。 これらのプロパティは、個々 のシンボルのトピックに表示されます。  
  
## <a name="see-also"></a>「  
 [CV_access_e 列挙型](../../debugger/debug-interface-access/cv-access-e.md)   
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [シンボルとシンボル タグ](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)