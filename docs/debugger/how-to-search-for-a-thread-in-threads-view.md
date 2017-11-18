---
title: "方法: スレッド ビュー内のスレッドの検索 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16404b5446b8aedc26d8ecc88e88b6061d896e69
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>方法: スレッド ビューでスレッドを検索する
検索条件としてスレッド ID、またはモジュールの文字列を使用して、スレッド ビューで特定のスレッドの検索することができます。 検索の最初の方向を指定することもできます。 ダイアログ ボックスで、フィールドは、スレッド ツリーで選択されているスレッドの属性が表示されます。  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>スレッド ビューでスレッドを検索するには  
  
1.  ウィンドウを整列するようにその spy++ と、アクティブな[スレッド ビュー](../debugger/threads-view.md)ウィンドウが表示されます。  
  
2.  **検索**] メニューの [選択**スレッド**です。  
  
     [スレッド検索 ダイアログ ボックス](../debugger/thread-search-dialog-box.md)が開きます。  
  
3.  検索条件として、スレッド ID、またはモジュールの文字列を入力します。  
  
4.  値を指定しないすべてのフィールドをオフにします。  
  
    > [!TIP]
    >  モジュールが所有するすべてのスレッドを検索するには、クリア、**スレッド**でテキスト ボックスと、モジュールの種類の名前、**モジュール**ボックス。 使用して**次を検索**スレッドの検索を続行します。  
  
5.  選択**を**または**ダウン**検索の方向。  
  
6.  **[OK]** をクリックします。  
  
 一致するスレッドが見つかった場合は、スレッド ビュー」ウィンドウでハイライトされます。