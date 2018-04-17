---
title: シンボル型の構文階層 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81cd3e54d61682962109afb59a396645ef65294d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="lexical-hierarchy-of-symbol-types"></a>シンボル型の構文階層
次の表は、構文の階層でシンボルの型を示します。  
  
## <a name="symbol-types"></a>シンボル型  
  
|記号の型|説明|  
|-----------------|-----------------|  
|[注釈](../../debugger/debug-interface-access/annotation.md)|プログラム コードでは、注釈付きの場所を指定します。|  
|[ブロック](../../debugger/debug-interface-access/block.md)|関数の入れ子になったスコープを指定します。|  
|`Compiland`|指定します、 `compiland` .exe ファイルにリンクします。|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|コンパイル単位のデータを追加のコンパイル単位の詳細の読み込みを必要とし、取得するため実行時のオーバーヘッドが増加する可能性がありますを指定します。|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|コンパイル単位のコンパイルをする重要な追加の環境変数を指定します。|  
|[カスタム (Debug Interface Access SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|ユーザー定義のシンボルを指定します。|  
|[データ (Debug Interface Access SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|パラメーター、ローカル変数、グローバル変数、およびクラス メンバーとしてこのような変数を指定します。|  
|[Exe](../../debugger/debug-interface-access/exe.md)|データのグローバル スコープを指定します.exe または .dll のファイル全体に対応します。|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|定義済みのポイントを持つ関数を指定するデバッグを終了するのです。|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|定義済みのポイントを持つ関数を指定するデバッグでは、開始します。|  
|[関数 (Debug Interface Access SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|関数を指定します。|  
|[ラベル (Debug Interface Access SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|プログラム コード内の場所を指定します。|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|実行可能プログラムを作成するときに表示される外部シンボルを指定します。|  
|[サンク](../../debugger/debug-interface-access/thunk.md)|指定します、`thunk`です。|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|指定します、`namespace`識別子。|  
  
> [!NOTE]
>  追加のシンボル プロパティは、シンボルの種類に応じてできる場合があります。 これらのプロパティは、個々 のシンボルのトピックで一覧表示されます。  
  
## <a name="see-also"></a>関連項目  
 [シンボル型のクラス階層](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Idiasymbol::get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [シンボルとシンボル タグ](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)