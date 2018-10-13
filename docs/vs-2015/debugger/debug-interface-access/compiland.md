---
title: コンパイル単位 |Microsoft Docs
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
- compiland symbol
- compilands, compiland symbol
ms.assetid: c798eb2b-664a-41ec-ae90-5e9d292507ca
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 34cb6f2c8660a6344ca906f036abd3292a69dda3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49217166"
---
# <a name="compiland"></a>コンパイル単位
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

1 つである`SymTagCompiland`の .exe ファイルにリンクされた各コンパイル単位シンボルします。 コンパイル単位の情報を使用したシンボルに分割されて、`SymTagCompiland`タグで、追加のコンパイル単位シンボルを読み込むことがなく取得できます、および記号を`SymTagCompilandDetails`タグで、追加のシンボルを読み込む必要があります。  
  
## <a name="properties"></a>プロパティ  
 次の表では、この記号の型の有効なプロパティを示します。  
  
|プロパティ|データの種類|説明|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` エディット コンティニュは、コンパイルで有効化された場合。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|.Exe ファイルの記号。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|構文の親のシンボルの ID。|  
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|`BSTR`|オブジェクトがから読み込まれたライブラリまたはオブジェクトのファイルの名前。|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|コンパイル単位のオブジェクト ファイルのファイル名。|  
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|`BSTR`|ソース ファイルの名前。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックス ID。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|返します`SymTagCompiland`(の 1 つ、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)値)。|  
  
## <a name="see-also"></a>関連項目  
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)   
 [CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)   
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)



