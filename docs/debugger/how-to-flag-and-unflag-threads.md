---
title: '方法: フラグを設定し、スレッドのフラグ解除 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d05987b23eca2d22472929a91fa1a140d7af10d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54969458"
---
# <a name="how-to-flag-and-unflag-threads-c-visual-basic-c"></a>方法: フラグを設定し、スレッドのフラグを解除 (C#、Visual Basic、C++)

アイコンでマークすることによって、特に注目するスレッドのフラグを設定することができます、**スレッド**、**並列スタック**(スレッド ビュー)、**並列ウォッチ**、および**GPU スレッド**windows。 このアイコンにより、フラグが設定されているスレッドをそれ以外のスレッドと簡単に区別できるようになります。  
  
フラグが設定されたスレッドは、特別な扱いも受信、**スレッド**ボックスの一覧、**デバッグの場所**ツールバーとその他のマルチ スレッドのデバッグ ウィンドウでします。 すべてのスレッドまたはでフラグが設定されたスレッドのみを表示することができます、**スレッド**リストまたは他のウィンドウにします。
  
### <a name="to-flag-or-unflag-a-thread"></a>スレッドのフラグを設定または設定解除するには
  
- **スレッド**または**並列ウォッチ**ウィンドウで、興味のあるスレッドを検索し、選択するか、フラグをクリアするには、フラグ アイコンをクリックしています。 
- **並列スタック**ウィンドウで、スレッドまたはスレッドのグループを右クリック**フラグ/ <thread>** または**フラグ解除/ <thread>** します。
  
### <a name="to-unflag-all-threads"></a>すべてのスレッドのフラグを解除するには  
  
-   **[スレッド]** ウィンドウで、いずれかのスレッドを右クリックし、**[すべてのスレッドのフラグを解除]** をクリックします。
-   **並列ウォッチ**ウィンドウで、すべてのフラグのスレッドを右クリックし、選択**フラグ解除**します。  
  
### <a name="to-display-only-flagged-threads"></a>フラグが設定されたスレッドのみ表示するには  
  
-   選択、**フラグが設定されたスレッドのみを表示する**マルチ スレッド デバッグ ウィンドウのいずれかでボタンをクリックします。  
  
### <a name="to-flag-just-my-code"></a>マイ コードのみにフラグを設定するには  
  
1.  **[スレッド]** ウィンドウの上部にあるツール バーで、フラグ アイコンをクリックします。  
  
2.  ドロップダウン リストで、**[マイ コードのみにフラグを設定]** をクリックします。  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>選択したモジュールに関連するスレッドにフラグを設定するには  
  
1.  **[スレッド]** ウィンドウのツール バーで、フラグ アイコンをクリックします。  
  
2.  ドロップダウン リストで、**[カスタム モジュール選択にフラグを設定]** をクリックします。  
  
3.  **[モジュールの選択]** ダイアログ ボックスで、目的のモジュールを選択します。  
  
4.  (省略可能) **[検索]** ボックスに、特定のモジュールを検索するための文字列を入力します。  
  
5.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目
 [マルチスレッド アプリケーションのデバッグ](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [マルチ スレッド アプリケーションのデバッグの開始](../debugger/get-started-debugging-multithreaded-apps.md)  
 [チュートリアル: [スレッド] ウィンドウを使用してマルチ スレッド アプリケーションをデバッグします。](../debugger/how-to-use-the-threads-window.md)
