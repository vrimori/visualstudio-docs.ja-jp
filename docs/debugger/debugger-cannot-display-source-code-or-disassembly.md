---
title: デバッガーは、ソース コードまたは逆アセンブルを表示できません |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee5fe6c07eb9f6f5fbcbca70b58c60a996b5b297
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>[デバッガーは、ソース コードまたは逆アセンブリを表示できません] ダイアログ ボックス
このエラーには、次のメッセージが表示されます。  
  
 デバッガーは、プログラムの実行が停止したソースコードまたは逆アセンブルを表示できません。  
  
 このエラー メッセージは、次のいくつかの理由によって発生します。  
  
-   逆アセンブリをサポートしない言語のデバッグ中に、ソース コードがない場所にあるブレークポイントにヒットした可能性があります。 開く、**ブレークポイント** ウィンドウで、ブレークポイントを見つけて削除ことです。  
  
-   スクリプトをデバッグしている場合は、プログラムにスレッドが存在しないときにブレークポイントにヒットした可能性があります。 選択**ステップ**または**続行**から、**デバッグ** メニューのデバッグを再開します。  
  
-   セキュリティ上の考慮から、デバッガーが、スタック、スレッド、レジスタ、またはその他のコンテキスト情報をデバッグ中のプログラムから読み取れない可能性があります。 これは、Web アプリケーションをデバッグしていて、仮想ディレクトリの適切なアクセス権がない場合によく発生します。 仮想ディレクトリのセキュリティを匿名に設定して再試行します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でデバッグ](../debugger/index.md)[デバッガーの機能のツアー](../debugger/debugger-feature-tour.md)   
 [デバッガーでのデータ表示](../debugger/viewing-data-in-the-debugger.md)