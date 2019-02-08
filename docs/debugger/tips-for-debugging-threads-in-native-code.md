---
title: ネイティブ コード内のスレッドをデバッグするためのヒント |Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 363e42700188c931c8be84d456a21112142925c8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54968845"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>ネイティブ コード内のスレッドのデバッグのヒント
ここでは、ネイティブ コード内のスレッドをデバッグするときに役立つヒントを紹介します。  
  
-   **[ウォッチ]** ウィンドウまたは **[クイック ウォッチ]** ダイアログ ボックスで「`@TIB`」と入力すると、[スレッド情報ブロック] の内容を表示できます。  
  
-   **[ウォッチ]** ウィンドウまたは **[クイック ウォッチ]** ダイアログ ボックスで「`@Err`」と入力すると、現在のスレッドの最終エラー コードを表示できます。  
  
-   マルチスレッド アプリケーションのデバッグには、C ランタイム ライブラリ (CRT) 関数を使用できます。 詳細については、「[_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)」をご覧ください。  
  
## <a name="see-also"></a>関連項目
 [マルチスレッド アプリケーションのデバッグ](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)
