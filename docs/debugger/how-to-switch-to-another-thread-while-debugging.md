---
title: デバッグ中に別のスレッドに切り替える
ms.custom: seodec18
ms.date: 04/27/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 163d14de4880ed1c5e2ae6a3170ec5ae1ae47485
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005190"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>方法: Visual Studio でのデバッグ中に別のスレッドに切り替える (C#、Visual Basic、C++)
マルチ スレッド アプリケーションをデバッグするときに、別のスレッドで作業しているスレッドから切り替えるにはいくつかのメソッドのいずれかを使用できます。

> [!NOTE]
> スレッドが実行される順序を制御する場合は、する必要があります[を固定およびスレッドの凍結解除](../debugger/get-started-debugging-multithreaded-apps.md)します。

コード エディターとさまざまなマルチ スレッド デバッグ ウィンドウ内のスレッドを調べると、黄色の矢印は、現在のスレッドを示します。 巻いた尾の付いた緑色の矢印は、現在ではないスレッドの現在のデバッガーのコンテキストであることを示します。
  
### <a name="to-switch-to-any-thread-that-appears"></a>表示される他のスレッドに切り替える 
  
-   **スレッド**または**並列ウォッチ**ウィンドウで、スレッドをダブルクリックします。  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>ソース ウィンドウでスレッドを切り替えるには  
  
-   左側の余白で、スレッド マーカーのアイコンを右クリックして![スレッド マーカー](../debugger/media/dbg-thread-marker.png "ThreadMarker")、 をポイント**に切り替える**、切り替え先のスレッドの名前をクリックして. ショートカット メニューには、その場所にあるスレッドのみが表示されます。  
  
     スレッド マーカーが表示されない場合で右クリックし、**スレッド**ウィンドウことを確認します**ソース スレッドを表示**が選択されています。  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>[デバッグの場所] ツール バーでスレッドを切り替えるには  
  
1.  **デバッグの場所**ツールバーで、をクリックして、**スレッド**一覧。  
  
2.  一覧で、切り替え先のスレッドをクリックします。  
  
## <a name="see-also"></a>関連項目
 [マルチスレッド アプリケーションのデバッグ](../debugger/debug-multithreaded-applications-in-visual-studio.md)
