---
title: ネイティブ コード内のスレッドをデバッグするためのヒント |Microsoft Docs
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
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02343da30e4f185a5b4aa236ed9b0b3ef823c4bb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535425"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>ネイティブ コード内のスレッドのデバッグのヒント
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ネイティブ コードでスレッドをデバッグするためのヒント](https://docs.microsoft.com/visualstudio/debugger/tips-for-debugging-threads-in-native-code)します。  
  
ここでは、ネイティブ コード内のスレッドをデバッグするときに役立つヒントを紹介します。  
  
-   スレッド情報ブロックの内容を表示するには」と入力して`@TIB`で、**ウォッチ**ウィンドウまたは**クイック ウォッチ**  ダイアログ ボックス。  
  
-   入力すると、現在のスレッドの最終エラー コードを表示できます`@Err`で、**ウォッチ**ウィンドウまたは**クイック ウォッチ**  ダイアログ ボックス。  
  
-   マルチスレッド アプリケーションのデバッグには、C ランタイム ライブラリ (CRT) 関数を使用できます。 詳細については、「[_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [マルチ スレッド アプリケーションをデバッグします。](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)



