---
title: '方法: Windows ビューでウィンドウの検索 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60eb467a24c85d176dae7727a476cc45dac6c876
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782974"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>方法: ウィンドウ ビューでウィンドウを検索する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows のビューで特定のウィンドウを検索するには、検索条件として、ハンドル、キャプション、クラス、またはキャプションとクラスの組み合わせを使用します。 検索の最初の方向を指定することもできます。 ダイアログ ボックスのフィールドは、ウィンドウのツリーで、選択したウィンドウの属性を紹介します。  
  
 (すべて windows デスクトップの子である)、2 番目のレベルに展開されたツリーで始まり、クラス名とタイトルによってデスクトップ レベルのウィンドウを識別できるように、します。 デスクトップ レベルのウィンドウを選択すると、特定の子ウィンドウを検索するには、そのレベルを展開できます。  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Windows のビューでウィンドウを検索するには  
  
1.  ウィンドウを整列するようにその spy++、 [Windows ビュー](../debugger/windows-view.md)ウィンドウ、[ターゲット] が表示されます。  
  
2.  **検索**] メニューの [選択**ウィンドウ検索**します。  
  
     [ウィンドウ検索 ダイアログ ボックス](../debugger/window-search-dialog-box.md)が開きます。  
  
    > [!TIP]
    >  画面の煩雑さを減らすためには、選択、 **Spy++ を非表示**オプション。 このオプションを選択し、メインの spy++ ウィンドウを非表示にのみが残ります、**ウィンドウ検索**ダイアログ ボックスで、他のアプリケーションの上に表示します。 クリックすると、spy++ のメイン ウィンドウが復元**OK**または**キャンセル**、またはオフにすると、 **spy++ を非表示にする**オプション。  
  
3.  ドラッグ、**ファインダー ツール**ターゲット枠。 このツールをドラッグすると、**ウィンドウ検索** ダイアログ ボックスでは、選択したウィンドウの詳細が表示されます。  
  
     または  
  
     入力できます (たとえば、デバッガー) から表示ウィンドウのハンドルをわかっている場合、**処理**ボックス。  
  
     または  
  
     キャプションや表示ウィンドウのクラスがわかっている場合は、それらを入力、**キャプション**と**クラス**テキスト ボックス、およびクリア、**処理**テキスト ボックス。  
  
4.  選択**を**または**ダウン**方向を検索します。  
  
5.  **[OK]** をクリックします。  
  
     強調表示されて、一致するウィンドウが見つかった場合、 [Windows ビュー](../debugger/windows-view.md)ウィンドウ。



