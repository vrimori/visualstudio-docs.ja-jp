---
title: '方法: スレッドのフラグの設定とフラグ |Microsoft Docs'
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
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f81de0353311d11cf744487d581296500d62ecb5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537534"
---
# <a name="how-to-flag-and-unflag-threads"></a>方法 : スレッドに対するフラグの設定と設定解除を行う
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: フラグとスレッドのフラグを解除](https://docs.microsoft.com/visualstudio/debugger/how-to-flag-and-unflag-threads)します。  
  
アイコンでマークすることによって、特に注目するスレッドのフラグを設定することができます、**スレッド**、**並列スタック**、**並列ウォッチ**、および**GPUスレッド**windows。 このアイコンにより、フラグが設定されているスレッドをそれ以外のスレッドと簡単に区別できるようになります。  
  
 フラグが設定されたスレッドは、特別な扱いも受信、**スレッド**ボックスの一覧、**デバッグの場所**ツールバー。 この一覧では、すべてのスレッドを表示することも、フラグが設定されたスレッドのみを表示することもできます。 スレッドのフラグを設定するときに、**スレッド**フラグが設定されたスレッドのみを表示するリストが自動的に切り替わりますが、切り替えることができます必要に応じてすべてのスレッドを表示します。  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>[スレッド] ウィンドウでスレッドに対するフラグを設定または解除するには  
  
-   **スレッド**ウィンドウで、興味のあるスレッドを検索し、選択するか、フラグをクリアするには、フラグ アイコンをクリックしています。  
  
### <a name="to-unflag-all-threads"></a>すべてのスレッドのフラグを解除するには  
  
-   **スレッド**ウィンドウで、任意のスレッドを右クリックし、順にクリックします**すべてのスレッドのフラグを解除**します。  
  
### <a name="to-display-only-flagged-threads"></a>フラグが設定されたスレッドのみ表示するには  
  
-   デバッグ ウィンドウでフラグ ボタンをクリックします。  
  
### <a name="to-flag-just-my-code"></a>マイ コードのみにフラグを設定するには  
  
1.  ツールバーの上部にある、**スレッド**ウィンドウで、フラグ アイコンをクリックします。  
  
2.  ボックスの一覧でクリックして**マイ コードのみをフラグ**します。  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>選択したモジュールに関連するスレッドにフラグを設定するには  
  
1.  ツールバーで、**スレッド**ウィンドウで、フラグ アイコンをクリックします。  
  
2.  ボックスの一覧でクリックして**カスタム モジュール選択にフラグ**します。  
  
3.  **モジュールの選択** ダイアログ ボックスで、使用するモジュールを選択します。  
  
4.  (省略可能)**検索**ボックスに、特定のモジュールを検索する文字列を入力します。  
  
5.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [マルチ スレッド アプリケーションをデバッグします。](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [チュートリアル : マルチスレッド アプリケーションのデバッグ](../debugger/walkthrough-debugging-a-multithreaded-application.md)



