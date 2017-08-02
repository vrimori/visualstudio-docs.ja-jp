---
title: "手順 7: フォームへのダイアログ コンポーネントの追加 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 手順 7: フォームへのダイアログ コンポーネントの追加
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この手順で、図ファイルを開き、背景色を選択するためにプログラムを有効にするには、**OpenFileDialog** コンポーネントと **ColorDialog** コンポーネントをフォームに追加します。  
  
 コンポーネントは、いくつかの点でコントロールに似ています。  コンポーネントはツールボックスを使用してフォームに追加し、そのプロパティの設定には **\[プロパティ\]** ウィンドウを使用します。  ただし、コントロールとは異なり、コンポーネントをフォームに追加しても、ユーザーに表示される項目がフォームに追加されるわけではありません。  代わりに、コードで発生させることができる特定の動作が提供されます。  ここで追加するのは、**\[ファイルを開く\]** ダイアログ ボックスを開くコンポーネントです。  
  
 ![ビデオへのリンク](~/docs/data-tools/media/playvideo.gif "PlayVideo") このトピックのビデオ版については、「[Tutorial 1: Create a Picture Viewer in Visual Basic \- Video 3 \(チュートリアル 1: Visual Basic によるピクチャ ビューアーの作成 \- ビデオ 3\)](http://go.microsoft.com/fwlink/?LinkId=205213)」または「[Tutorial 1: Create a Picture Viewer in C\# \- Video 3 \(チュートリアル 1: C\# によるピクチャ ビューアーの作成 \- ビデオ 3\)](http://go.microsoft.com/fwlink/?LinkId=205202)」を参照してください。  これらのビデオでは、旧バージョンの Visual Studio を使用しているため、一部のメニュー コマンドやその他のユーザー インターフェイス要素が若干異なります。  ただし、概念および手順は、現在のバージョンの Visual Studio でも同様です。  
  
### フォームにダイアログ コンポーネントを追加するには  
  
1.  Windows フォーム デザイナー \(Form1.cs \[デザイン\] または Form1.vb \[デザイン\]\) を選択し、ツールボックスの **\[ダイアログ\]** グループを開きます。  
  
    > [!NOTE]
    >  ツールボックスの **\[ダイアログ\]** グループには、多数の便利なダイアログ ボックスを開くコンポーネントが含まれています。これらは、ファイルを開く、ファイルを保存する、フォルダーを参照する、フォントや色を選択するなど、さまざまな用途で使用できます。  このプロジェクトでは、**OpenFileDialog** と **ColorDialog** という 2 つのダイアログ コンポーネントを使用します。  
  
2.  **openFileDialog1** というコンポーネントをフォームに追加するために、**\[OpenFileDialog\]** をダブルクリックします。  次に、**colorDialog1** というコンポーネントを追加するために、ツールボックスの **\[ColorDialog\]** をダブルクリックします  \(このコンポーネントはチュートリアルの次の手順で使用します\)。 Windows フォーム デザイナーの下部の領域 \(ピクチャ ビューアー フォームの下\) に、次の図に示すように、追加した 2 つのダイアログ コンポーネントのそれぞれに対応するアイコンが表示されます。  
  
     ![ダイアログ コンポーネント](../ide/media/express_dialogsadded.png "Express\_DialogsAdded")  
ダイアログ コンポーネント  
  
3.  Windows フォーム デザイナーの下部にある領域で **\[openFileDialog1\]** アイコンをクリックします。  2 つのプロパティを次のように設定します。  
  
    -   **Filter** プロパティを次のように設定します \(コピーして貼り付けることができます\)。  
  
        ```  
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*  
        ```  
  
    -   **Title** プロパティ: Select a picture file  
  
         **Filter** プロパティの設定は、**\[Select a picture\]** ファイル ダイアログ ボックスに表示されるファイルの種類を指定します。  
  
    > [!NOTE]
    >  他のアプリケーションで **\[ファイルを開く\]** ダイアログ ボックスの例を確認するには、メモ帳またはペイントを開き、メニュー バーで、**\[ファイル\]**、**\[開く\]** の順にクリックします。  下部にある **\[ファイルの種類\]** ボックスに注目してください。  ここではそのボックスの内容を、**OpenFileDialog** コンポーネントの **Filter** プロパティを使用して設定しました。  また、**Title** プロパティと **Filter** プロパティが **\[プロパティ\]** ウィンドウで太字になっていることに注目してください。  IDE では、既定値とは異なる値に変更されたプロパティがわかるように、それらが太字で示されます。  
  
### 続行または確認するには  
  
-   チュートリアルの次の手順に進むには、「[手順 8:ボタンのイベント ハンドラーのコードの記述](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)」を参照してください。  
  
-   チュートリアルの前の手順に戻るには、「[手順 6: ボタン コントロールの名前の設定](../ide/step-6-name-your-button-controls.md)」を参照してください。