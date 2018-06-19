---
title: デバッガーは、ソース コードまたは逆アセンブルを表示できません |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 313a0e9e5727d776eaeb13f1c4cef8cf3d8d3bb9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472699"
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