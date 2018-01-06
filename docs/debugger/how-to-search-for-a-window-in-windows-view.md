---
title: "方法: ウィンドウ ビューでウィンドウの検索 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dfec3f78e9f95a55d453c45c5a264125152cbf1b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>方法: ウィンドウ ビューでウィンドウを検索する
Windows の表示で特定のウィンドウの検索条件として、ハンドル、キャプション、クラス、またはキャプションとクラスの組み合わせを使用して検索できます。 検索の最初の方向を指定することもできます。 ダイアログ ボックスで、フィールドは、ウィンドウのツリーで、選択したウィンドウの属性が表示されます。  
  
 (すべて windows デスクトップの子である)、2 番目のレベルまで展開されたツリーで始まるデスクトップ レベルで windows のクラス名とタイトルを識別できるように、します。 デスクトップ レベルのウィンドウを選択すると、特定の子ウィンドウを検索するには、そのレベルを展開できます。  
  
### <a name="to-search-for-a-window-in-windows-view"></a>ウィンドウ ビューでウィンドウを検索するには  
  
1.  ウィンドウを整列するため、spy++、[ウィンドウ ビュー](../debugger/windows-view.md)ウィンドウ、およびターゲット ウィンドウに表示されます。  
  
2.  **検索**] メニューの [選択**ウィンドウ検索**です。  
  
     [ウィンドウ検索 ダイアログ ボックス](../debugger/window-search-dialog-box.md)が開きます。  
  
    > [!TIP]
    >  見やすくするために画面を選択して、 **Spy++ を非表示**オプション。 このオプションを選択し、spy++、メイン ウィンドウを非表示にのみが残ります、**ウィンドウ検索** ダイアログ ボックスに、他のアプリケーションの上に表示します。 クリックすると、Spy++ でのメイン ウィンドウを復元**[ok]**または**キャンセル**、またはクリアすると、 **spy++ を非表示に**オプション。  
  
3.  ドラッグ、**ファインダー ツール**対象ウィンドウの上です。 このツールをドラッグすると、**ウィンドウ検索** ダイアログ ボックスでは、選択したウィンドウの詳細が表示されます。  
  
     - または  
  
     入力できます (たとえば、デバッガー) から表示ウィンドウのハンドルを把握している場合、**処理**ボックス。  
  
     - または  
  
     キャプションや表示ウィンドウのクラスがわかっている場合でそれを入力、**キャプション**と**クラス**テキスト ボックス、および消去、**処理**テキスト ボックス。  
  
4.  選択**を**または**ダウン**検索の方向。  
  
5.  **[OK]**をクリックします。  
  
     強調表示されて、一致するウィンドウが見つかった場合、[ウィンドウ ビュー](../debugger/windows-view.md)ウィンドウです。