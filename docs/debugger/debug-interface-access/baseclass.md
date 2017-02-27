---
title: "BaseClass | Microsoft Docs"
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
  - "ユーザー定義型、基底クラス"
  - "BaseClass シンボル"
  - "基底クラス、ユーザー定義型"
ms.assetid: 9375ca35-cb91-45f5-8903-7344ee4528e8
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# BaseClass
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ユーザー定義型のシンボルの各 \(UDT\) 基本クラスは `SymTagBaseClass` のタグを持つ子によって識別されます。  型のプロパティは基になる UDT のシンボルが含まれ基になる UDT のすべてのプロパティはBaseClass にこのシンボルの一部として使用できます。  
  
## プロパティ  
 次の表はこのシンボルの型に対して有効なプロパティを次に示します。  
  
|プロパティ|データ型|Description|  
|-----------|----------|-----------------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|この基本クラスに適用されるアクセス修飾子。  [CV\_access\_e 列挙型](../../debugger/debug-interface-access/cv-access-e.md) 値のいずれか。|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|外側のクラスのシンボル \(存在する場合\)。|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|クラスの親のシンボル ID。|  
|[IDiaSymbol::get\_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|基本クラスにコンストラクターが存在 `TRUE`。|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|基本クラスを定数としてマークされている場合 `TRUE`。|  
|[IDiaSymbol::get\_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|基本クラスの代入演算子がある場合 `TRUE`。|  
|[IDiaSymbol::get\_hasCastOperator](../Topic/IDiaSymbol::get_hasCastOperator.md)|`BOOL`|基本クラスにキャスト演算子がある場合 `TRUE`。|  
|[IDiaSymbol::get\_hasNestedTypes](../Topic/IDiaSymbol::get_hasNestedTypes.md)|`BOOL`|基本クラスに入れ子にされた型である場合 `TRUE`。|  
|[IDiaSymbol::get\_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|`BOOL`|基本クラスは間接場合 `TRUE`。|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`DWORD`|バイトこの基本クラスの長さ。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|外側のコンパイル単位のシンボル。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|構文親のシンボル ID。|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|基本クラスの名前。|  
|[IDiaSymbol::get\_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|基本クラスになっている場合 `TRUE`。|  
|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|構造体内の基本クラスを表すサブオブジェクトのオフセット。|  
|[IDiaSymbol::get\_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|基本クラスにオーバーロードされた演算子がある場合 `TRUE`。|  
|[IDiaSymbol::get\_packed](../Topic/IDiaSymbol::get_packed.md)|`BOOL`|おけば基本クラスが `TRUE`。|  
|[IDiaSymbol::get\_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|基本クラスが nonglobal 範囲にある `TRUE`。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックスの ID。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|`SymTagBaseClass` [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md) の値 \(1\) を返します。|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|基本クラス [UDT](../../debugger/debug-interface-access/udt.md) のシンボル。|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|型のシンボル ID。|  
|[IDiaSymbol::get\_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|`DWORD`|[UdtKind 列挙型](../../debugger/debug-interface-access/udtkind.md) の値。|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|基本クラスでアライメントされていない場合 `TRUE`。|  
|[IDiaSymbol::get\_virtualBaseClass](../Topic/IDiaSymbol::get_virtualBaseClass.md)|`BOOL`|基本クラスの仮想関数である場合 `TRUE`。|  
|[IDiaSymbol::get\_virtualBaseDispIndex](../Topic/IDiaSymbol::get_virtualBaseDispIndex.md)|`DWORD`|仮想基本的なと変位のテーブルにインデックス。|  
|[IDiaSymbol::get\_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|`LONG`|仮想基本ポインターのオフセット。|  
|[IDiaSymbol::get\_virtualBaseTableType](../Topic/IDiaSymbol::get_virtualBaseTableType.md)|`IDiaSymbol*`|仮想テーブル ベースのポインターの型です。|  
|[IDiaSymbol::get\_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|`IDiaSymbol*`|この基本クラスの仮想テーブルの種類を示すシンボルです。|  
|[IDiaSymbol::get\_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|`DWORD`|仮想テーブルの図形のシンボル ID。|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|基本クラスが volatile としてマークされている場合 `TRUE`。|  
  
## 参照  
 [シンボル型のクラス階層](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [UDT](../../debugger/debug-interface-access/udt.md)