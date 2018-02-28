---
title: "方法: デバッグ中に別のスレッドに切り替える |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0710bad95484ada62faa042edabf5b76ac459558
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio"></a>方法: Visual Studio でのデバッグ中に別のスレッドに切り替える
マルチ スレッド アプリケーションをデバッグするときに、別のスレッドで作業しているスレッドから切り替えるにはいくつかの方法のいずれかを使用できます。

> [!NOTE]
> スレッドが実行される順序を制御する場合は、する必要があります[スレッドを凍結解除したり凍結解除したり](../debugger/get-started-debugging-multithreaded-apps.md)です。

コード エディターとさまざまなマルチ スレッド デバッグ ウィンドウ内のスレッドを確認するときに、黄色の矢印は、現在のスレッドを示します。 巻いた尾の付いた緑色の矢印は、現在ではないスレッドの現在のデバッガーのコンテキストであることを示します。
  
### <a name="to-switch-to-any-thread-that-appears"></a>表示される任意のスレッドに切り替えるには 
  
-   **スレッド**または**並列ウォッチ**ウィンドウで、スレッドをダブルクリックします。  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>ソース ウィンドウでスレッドを切り替えるには  
  
-   左側の余白で、スレッド マーカーのアイコンを右クリックして![スレッド マーカー](../debugger/media/dbg-thread-marker.png "ThreadMarker")、 をポイント**に切り替える**、切り替えたいスレッドの名前をクリックして. ショートカット メニューには、その場所にあるスレッドのみが表示されます。  
  
     スレッド マーカーが表示されない場合で右クリックし、**スレッド**ウィンドウことを確認および**ソース内のスレッドを表示**が選択されています。  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>[デバッグの場所] ツール バーでスレッドを切り替えるには  
  
1.  **デバッグの場所**ツールバーで、をクリックして、**スレッド** ボックスの一覧です。  
  
2.  一覧で、切り替え先のスレッドをクリックします。  
  
## <a name="see-also"></a>参照  
 [マルチ スレッド アプリケーションをデバッグします。](../debugger/debug-multithreaded-applications-in-visual-studio.md)
