---
title: "方法: プロセス ビューでのプロセスの検索 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78c67ccc34d9c95914f6b46d537a4df3431c877f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>方法: プロセス ビューでプロセスを検索する
検索条件として、プロセス ID またはモジュールの文字列を使用して、[プロセス] ビューで特定のプロセスを検索できます。 検索の最初の方向を指定することもできます。 ダイアログ ボックスで、フィールドは、処理ツリーで選択したプロセスの属性が表示されます。  
  
### <a name="to-search-for-a-process-in-processes-view"></a>プロセス ビューでプロセスを検索するには  
  
1.  ウィンドウを整列するようにその spy++ と、アクティブな[プロセス ビュー](../debugger/processes-view.md)ウィンドウが表示されます。  
  
2.  **検索**] メニューの [選択**プロセスを検索**  
  
     [プロセス検索 ダイアログ ボックス](../debugger/process-search-dialog-box.md)が開きます。  
  
3.  検索条件として、プロセス ID またはモジュールの文字列を入力します。  
  
4.  値を指定しないすべてのフィールドをオフにします。  
  
    > [!TIP]
    >  モジュールが所有するすべてのプロセスを検索するには、クリア、**プロセス**内のモジュール名を入力、**モジュール**ボックス。 使用して**次を検索**プロセスの検索を続行します。  
  
5.  選択**を**または**ダウン**検索の方向。  
  
6.  **[OK]** をクリックします。  
  
 強調表示されて、一致するプロセスが見つかった場合、**プロセス ビュー**ウィンドウです。