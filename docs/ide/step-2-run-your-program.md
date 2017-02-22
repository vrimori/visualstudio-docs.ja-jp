---
title: "手順 2: プログラムの実行 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a8fe90e-c97b-4e98-b6c8-0c6b3962c49d
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 手順 2: プログラムの実行
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

新しいソリューションを作成すると、実際には実行するプログラムが作成されます。  まだ実行される処理は少なく、タイトル バーに **Form1** と表示された空のウィンドウを表示するだけのプログラムですが、  もうおわかりのように実行することはできます。  
  
 ![ビデオへのリンク](../data-tools/media/playvideo.png "PlayVideo") このトピックのビデオ版については、「[Tutorial 1: Create a Picture Viewer in Visual Basic \- Video 1 \(チュートリアル 1: Visual Basic によるピクチャ ビューアーの作成 \- ビデオ 1\)](http://go.microsoft.com/fwlink/?LinkId=205209)」または「[Tutorial 1: Create a Picture Viewer in C\# \- Video 1 \(チュートリアル 1: C\# によるピクチャ ビューアーの作成 \- ビデオ 1\)](http://go.microsoft.com/fwlink/?LinkId=205199)」を参照してください。  これらのビデオでは、旧バージョンの Visual Studio を使用しているため、一部のメニュー コマンドやその他のユーザー インターフェイス要素が若干異なります。  ただし、概念および手順は、現在のバージョンの Visual Studio でも同様です。  
  
### プログラムを実行するには  
  
1.  プログラムを実行するには、次のいずれかの方法を使用します。  
  
    -   **F5** キーを押します。  
  
    -   メニュー バーで、**\[デバッグ\]**、**\[デバッグ開始\]** の順に選択します。  
  
    -   ツール バーで、**\[デバッグ開始\]** ボタンをクリックします \(次の図を参照\)。  
  
         ![&#91;デバッグの開始&#93; ツール バー ボタン](../ide/media/express_icondebug.png "Express\_IconDebug")  
ツール バーの \[デバッグ開始\] ボタン  
  
2.  Visual Studio でプログラムが実行され、**Form1** というウィンドウが表示されます。  次の図は、作成したプログラムを示しています。  この実行中のプログラムに対し、これから機能を追加していきます。  
  
     ![実行中の Windows フォーム アプリケーション プログラム](../ide/media/express_firstrun.png "Express\_FirstRun")  
実行中の Windows フォーム アプリケーション プログラム  
  
3.  Visual Studio 統合開発環境 \(IDE\) に戻り、新しいツール バーを参照します。  プログラムを実行すると、追加ボタンがツール バーに表示されます。  これらのボタンを使用するとプログラムの停止や開始などの操作ができ、発生する可能性のあるエラー \(バグ\) の追跡に役立ちます。  この例では、単にプログラムを開始および停止するために使用します。  
  
     ![デバッグ ツール バー](../ide/media/express_debugtoolbar.png "Express\_DebugToolbar")  
デバッグ ツール バー  
  
4.  プログラムを停止するには、次のいずれかの方法を使用します。  
  
    -   ツール バーで、**\[デバッグの停止\]** のボタンをクリックします。  
  
    -   メニュー バーで、**\[デバッグ\]**、**\[デバッグの停止\]** の順に選択します。  
  
    -   **\[Form1\]** ウィンドウの上隅にある X ボタンをクリックします。  
  
    > [!NOTE]
    >  IDE 内からプログラムを実行する作業は、通常はプログラムでバグ \(エラー\) を特定して修正することが目的であるため*デバッグ*と呼ばれます。  このプログラムは小さくて、実際には何も実行しませんが、それでも実際のプログラムです。  同じ手順で他のプログラムを実行し、デバッグします。  デバッグの詳細については、「[デバッガーの基本事項](../debugger/debugger-basics.md)」を参照してください。  
  
### 続行または確認するには  
  
-   チュートリアルの次の手順に進むには、「[手順 3: フォームのプロパティの設定](../ide/step-3-set-your-form-properties.md)」を参照してください。  
  
-   チュートリアルの前の手順に戻るには、「[手順 1: Windows フォーム アプリケーション プロジェクトの作成](../ide/step-1-create-a-windows-forms-application-project.md)」を参照してください。