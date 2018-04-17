---
title: ネイティブ コード内のスレッドのデバッグのヒント |Microsoft ドキュメント
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
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 72b913c64d78966bde96419978a066cc9921ebaa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="tips-for-debugging-threads-in-native-code"></a>ネイティブ コード内のスレッドのデバッグのヒント
ここでは、ネイティブ コード内のスレッドをデバッグするときに役立つヒントを紹介します。  
  
-   スレッド情報ブロックの内容を表示するには」と入力して`@TIB`で、**ウォッチ**ウィンドウまたは**クイック ウォッチ**  ダイアログ ボックス。  
  
-   入力すると、現在のスレッドの最終エラー コードを表示できます`@Err`で、**ウォッチ**ウィンドウまたは**クイック ウォッチ**  ダイアログ ボックス。  
  
-   マルチスレッド アプリケーションのデバッグには、C ランタイム ライブラリ (CRT) 関数を使用できます。 詳細については、「[_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [マルチ スレッド アプリケーションをデバッグします。](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)