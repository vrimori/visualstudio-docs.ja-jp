---
title: シンボルとシンボル タグ |Microsoft Docs
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
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7eaf514ce88b20954ace1206ab625ae55ed12cd2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189788"
---
# <a name="symbols-and-symbol-tags"></a>シンボルとシンボル タグ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

コンパイル済みプログラムのデバッグについては、プログラム データベース (.pdb) ファイルでデバッグ インターフェイスへのアクセス (DIA) SDK の Api を使用してアクセス可能であるシンボルとして格納されます。 すべてのシンボルが、 [idiasymbol::get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)と[idiasymbol::get_symindexid](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)プロパティ。 `symTag`プロパティで定義されているシンボルの種類を示す、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)列挙体。 `symIndexId`プロパティは、`DWORD`シンボルのすべてのインスタンスの一意の識別子を表す値です。  
  
 シンボルがシンボルとその他のシンボルへの参照に関する追加情報ほとんどの場合に指定できるプロパティを持つことも、 [idiasymbol::get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)または[idiasymbol::get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). として参照が返される参照を含むプロパティを照会するときに、 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)オブジェクト。 このようなプロパティ常とペアになる別のプロパティ名"id"サフィックスが付いたが同じで、たとえば、 [idiasymbol::get_lexicalparentid](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)と[idiasymbol::get_classparentid](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)します。 内のテーブル[シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)、[シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)、および[シンボル型のクラス階層](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)さまざまな種類の各プロパティの説明のシンボル。 これらのプロパティには、関連する情報またはその他のシンボルへの参照があります。 `*Id`プロパティは、関連するプロパティを単純に数値の序数識別子、さらにディスカッションから省略されています。 それらはパラメーターのわかりやすくするために必要な場合にのみです。  
  
 エラーが発生しないと、シンボル プロパティに値が割り当てられる場合、プロパティにアクセスしようとすると、プロパティの取得 メソッドを返します。`S_OK`します。 戻り値`S_FALSE`プロパティが現在のシンボルの無効であることを示します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)  
 シンボルの場所のさまざまな種類をについて説明します。  
  
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 ファイル、モジュール、関数などの構文階層を形成するシンボルの型について説明します。  
  
 [シンボル型のクラス階層](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 クラス、配列、および関数型を返すなど、さまざまな言語要素に対応するシンボルの型について説明します。  
  
## <a name="see-also"></a>関連項目  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)



