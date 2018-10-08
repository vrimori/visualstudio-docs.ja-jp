---
title: デバッガーは、ソース コードまたは逆アセンブルを表示できません |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd21a38123894e7254bf4af6629528f8af4bf52d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544636"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>[デバッガーは、ソース コードまたは逆アセンブリを表示できません] ダイアログ ボックス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[デバッガーできません表示ソース コードまたは逆アセンブル](https://docs.microsoft.com/visualstudio/debugger/debugger-cannot-display-source-code-or-disassembly)します。  
  
このエラーには、次のメッセージが表示されます。  
  
 デバッガーは、プログラムの実行が停止したソースコードまたは逆アセンブルを表示できません。  
  
 このエラー メッセージは、次のいくつかの理由によって発生します。  
  
-   逆アセンブリをサポートしない言語のデバッグ中に、ソース コードがない場所にあるブレークポイントにヒットした可能性があります。 開く、**ブレークポイント**ウィンドウで、ブレークポイントを見つけて削除します。  
  
-   スクリプトをデバッグしている場合は、プログラムにスレッドが存在しないときにブレークポイントにヒットした可能性があります。 選択**手順**または**続行**から、**デバッグ** メニューのデバッグを再開します。  
  
-   セキュリティ上の考慮から、デバッガーが、スタック、スレッド、レジスタ、またはその他のコンテキスト情報をデバッグ中のプログラムから読み取れない可能性があります。 これは、Web アプリケーションをデバッグしていて、仮想ディレクトリの適切なアクセス権がない場合によく発生します。 仮想ディレクトリのセキュリティを匿名に設定して再試行します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーの基本事項](../debugger/debugger-basics.md)   
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)   
 [デバッガーでのデータ表示](../debugger/viewing-data-in-the-debugger.md)



