---
title: '方法: スレッドのフラグの設定とフラグ |Microsoft Docs'
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
ms.openlocfilehash: 09d26c87867e071b7dafce80d95e4bc46cb88bb8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891376"
---
# <a name="how-to-flag-and-unflag-threads"></a>方法 : スレッドに対するフラグの設定と設定解除を行う
アイコンでマークすることによって、特に注目するスレッドのフラグを設定することができます、**スレッド**、**並列スタック**(スレッド ビュー)、**並列ウォッチ**、および**GPU スレッド**windows。 このアイコンにより、フラグが設定されているスレッドをそれ以外のスレッドと簡単に区別できるようになります。  
  
フラグが設定されたスレッドは、特別な扱いも受信、**スレッド**ボックスの一覧、**デバッグの場所**ツールバーとその他のマルチ スレッドのデバッグ ウィンドウでします。 すべてのスレッドまたはでフラグが設定されたスレッドのみを表示することができます、**スレッド**リストまたは他のウィンドウにします。
  
### <a name="to-flag-or-unflag-a-thread"></a>スレッドのフラグを設定または設定解除するには 
  
- **スレッド**または**並列ウォッチ**ウィンドウで、興味のあるスレッドを検索し、選択するか、フラグをクリアするには、フラグ アイコンをクリックしています。 
- **並列スタック**ウィンドウで、スレッドまたはスレッドのグループを右クリック**フラグ/ <thread>** または**フラグ解除/ <thread>** します。
  
### <a name="to-unflag-all-threads"></a>すべてのスレッドのフラグを解除するには  
  
-   **スレッド**ウィンドウで、任意のスレッドを右クリックし、順にクリックします**すべてのスレッドのフラグを解除**します。
-   **並列ウォッチ**ウィンドウで、すべてのフラグのスレッドを右クリックし、選択**フラグ解除**します。  
  
### <a name="to-display-only-flagged-threads"></a>フラグが設定されたスレッドのみ表示するには  
  
-   選択、**フラグが設定されたスレッドのみを表示する**マルチ スレッド デバッグ ウィンドウのいずれかでボタンをクリックします。  
  
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
 [マルチ スレッド アプリケーションのデバッグの開始します。](../debugger/get-started-debugging-multithreaded-apps.md)  
 [チュートリアル: [スレッド] ウィンドウを使用してマルチ スレッド アプリケーションをデバッグします。](../debugger/how-to-use-the-threads-window.md)