---
title: '方法: スレッド ビュー内のスレッドの検索 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2d582a10e2738b69724765477ee64c47e8cb68c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
  
6.  **[OK]**をクリックします。  
  
 一致するスレッドが見つかった場合は、スレッド ビュー」ウィンドウでハイライトされます。