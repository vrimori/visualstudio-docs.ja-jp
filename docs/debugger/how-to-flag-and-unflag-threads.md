---
title: '方法: フラグを設定し、スレッドのフラグ解除 |Microsoft ドキュメント'
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
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 052c9d65e833152c0d3d3f67eda41742119eccaf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-flag-and-unflag-threads"></a>方法 : スレッドに対するフラグの設定と設定解除を行う
アイコンでマークすることによって、特に注目するスレッドのフラグを設定することができます、**スレッド**、**並列スタック**(スレッド ビュー)、**並列ウォッチ**、および**GPU スレッド**windows です。 このアイコンにより、フラグが設定されているスレッドをそれ以外のスレッドと簡単に区別できるようになります。  
  
フラグが設定されたスレッドも特別な扱い、**スレッド**ボックスの一覧、**デバッグの場所**ツールバーとその他のマルチ スレッドのデバッグ ウィンドウでします。 すべてのスレッドまたはでフラグが設定されたスレッドのみを表示することができます、**スレッド**リストまたは他のウィンドウでします。
  
### <a name="to-flag-or-unflag-a-thread"></a>スレッドのフラグを設定または設定解除するには 
  
-   **スレッド**または**並列ウォッチ**ウィンドウで、興味のあるスレッドを検索アイコンをクリックして、フラグを選択するか、フラグをクリアします。 
-   **並列スタック**ウィンドウで、スレッドやスレッドと選択のグループを右クリック**フラグ/ <thread>** または**フラグ解除/ <thread>**です。
  
### <a name="to-unflag-all-threads"></a>すべてのスレッドのフラグを解除するには  
  
-   **スレッド** ウィンドウでは、任意のスレッドを右クリックし、をクリックして**すべてのスレッドのフラグを解除**です。
-   **並列ウォッチ**ウィンドウで、すべてフラグが設定されたスレッドを右クリックし、選択**フラグ解除**です。  
  
### <a name="to-display-only-flagged-threads"></a>フラグが設定されたスレッドのみ表示するには  
  
-   選択、**フラグが設定されたスレッドのみを表示する**マルチ スレッドのデバッグ ウィンドウのいずれかでボタンをクリックします。  
  
### <a name="to-flag-just-my-code"></a>マイ コードのみにフラグを設定するには  
  
1.  上部のツールバーで、**スレッド**ウィンドウで、フラグ アイコンをクリックします。  
  
2.  ドロップダウン リストでをクリックして**フラグ マイ コードのみ**です。  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>選択したモジュールに関連するスレッドにフラグを設定するには  
  
1.  ツールバーで、**スレッド**ウィンドウで、フラグ アイコンをクリックします。  
  
2.  ドロップダウン リストでをクリックして**カスタム モジュール選択にフラグ**です。  
  
3.  **モジュールの選択** ダイアログ ボックスで、目的のモジュールを選択します。  
  
4.  (省略可能)**検索**ボックスに、特定のモジュールを検索する文字列を入力します。  
  
5.  **[OK]**をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [マルチ スレッド アプリケーションをデバッグします。](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [マルチ スレッド アプリケーションのデバッグの開始します。](../debugger/get-started-debugging-multithreaded-apps.md)  
 [チュートリアル: [スレッド] ウィンドウを使用するマルチ スレッド アプリケーションをデバッグします。](../debugger/how-to-use-the-threads-window.md)