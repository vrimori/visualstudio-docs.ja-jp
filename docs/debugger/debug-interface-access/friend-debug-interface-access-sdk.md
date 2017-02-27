---
title: "フレンド (Debug Interface Access SDK) | Microsoft Docs"
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
  - "フレンド関数 [DIA SDK]"
  - "フレンド クラス [DIA SDK]"
  - "フレンド シンボル"
ms.assetid: 5147a170-41ce-4727-8ace-c318e8d11647
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# フレンド (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

フレンド クラスとフレンド関数は `SymTagFriend` の記号で示されます。  これらは親の型 \(UDTs\) の子で[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md) のプロパティがあります。  
  
## プロパティ  
 次の表はこのシンボルの型に対して有効なプロパティを次に示します。  
  
|プロパティ|データ型|Description|  
|-----------|----------|-----------------|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|UDT の親のシンボル。|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|クラスの親のシンボル ID。|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|クラスの名前。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックスの ID。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|`SymTagFriend` [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md) の値 \(1\) を返します。|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|クラスや関数のシンボル。|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|型のシンボル ID。|  
  
## 参照  
 [シンボル型のクラス階層](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)