---
title: "シンボルとシンボル タグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c3e51d02171455cd5b0b6051ed3b05c6d95278ce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="symbols-and-symbol-tags"></a>シンボルとシンボル タグ
コンパイル済みのプログラムに関するデバッグ情報は、シンボルとデバッグ インターフェイス アクセス (DIA) SDK の Api を使用してアクセス可能であるプログラム データベース (.pdb) ファイルに格納されます。 すべてのシンボルが、 [idiasymbol::get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)と[idiasymbol::get_symindexid](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)プロパティです。 `symTag`で定義されているプロパティがシンボルの種類を示す、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)列挙します。 `symIndexId`プロパティは、`DWORD`シンボルのすべてのインスタンスの一意の識別子を含む値です。  
  
 シンボルがシンボルに加え、他のシンボルへの参照に関する追加情報ほとんどの場合に指定できるプロパティを持つも、 [idiasymbol::get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)または[idiasymbol::get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). として参照が返される参照を含んでいるプロパティをクエリするとき、 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)オブジェクト。 などのプロパティは常にペアになって別のプロパティ名"Id"と付加が同じでなど[idiasymbol::get_lexicalparentid](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)と[idiasymbol::get_classparentid](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)です。 内のテーブル[シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)、[シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)、および[シンボル型のクラス階層](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)さまざまな種類の各プロパティの概要のシンボル。 これらのプロパティには、関連する情報またはその他のシンボルへの参照があります。 `*Id`プロパティは、関連するプロパティを単に数値の序数に基づく識別子、さらにディスカッションから省略されています。 それらはパラメーターの説明で必要な場合のみです。  
  
 エラーが発生しないと、シンボルのプロパティに値が割り当てられる場合、プロパティにアクセスしようとすると、プロパティの"get"メソッドを返します`S_OK`です。 戻り値の`S_FALSE`プロパティが現在のシンボルに対して有効でないことを示します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)  
 シンボルの場所のさまざまな種類をについて説明します。  
  
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 ファイル、モジュール、関数などの構文上の階層を形成するシンボルの型について説明します。  
  
 [シンボル型のクラス階層](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 クラス、配列、および関数型を返すように、別の言語要素に対応するシンボルの型について説明します。  
  
## <a name="see-also"></a>参照  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)