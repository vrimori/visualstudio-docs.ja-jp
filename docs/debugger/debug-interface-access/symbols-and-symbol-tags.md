---
title: "シンボルとシンボル タグ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "シンボル [DIA SDK]"
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# シンボルとシンボル タグ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

コンパイル済みプログラムのデバッグ情報がプログラム データベース \(.pdb\) ファイルで Debug Interface Access SDK の API を使用してアクセスできるシンボルとして \(DIA\) 格納されます。  すべてのシンボルに [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md) と [IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) のプロパティがあります。  `symTag` のプロパティは [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md) の列挙型で定義されているシンボルの種類を示します。  `symIndexId` のプロパティはシンボルのすべてのインスタンスの一意識別子を含む `DWORD` の値です。  
  
 シンボルに最も頻繁に [IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) または [IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md) シンボルに関する追加情報およびへの参照を他のシンボル指定できるプロパティがあります。  参照を含むプロパティを呼び出すと参照は [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) のオブジェクトを返します。  このようなプロパティと同じ名前で別のプロパティと常に使用されますが「 ID 」たとえば[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) と [IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md) をサフィックスとして付けられます。  [シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)[シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md) と [シンボル型のクラス階層](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) のアウトラインのシンボル テーブルの種類ごとにプロパティ。  これらのプロパティは関連情報に関するそのほかのシンボルへの参照がある場合があります。  `*Id` のプロパティが関連プロパティのではなく数値順序の識別子であるため以降の説明では省略されます。  はパラメーターについては必要に応じてだけで参照されます。  
  
 プロパティにアクセスしようとしたときにエラーが発生しないしシンボルのプロパティに値が割り当てられプロパティはメソッドの戻り `S_OK` 「」を取得します。  `S_FALSE` の戻り値はプロパティが現在のシンボルに対して無効であることを示します。  
  
## このセクションの内容  
 [シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)  
 シンボルを使用できる場所の種類について説明します。  
  
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 ファイルモジュール関数のような構文を使用してシンボル階層の型について説明します。  
  
 [シンボル型のクラス階層](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 クラス配列および関数の戻り値の型など異なる言語要素に対応するシンボルの型について説明します。  
  
## 参照  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)