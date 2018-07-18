---
title: '手順 7: フォームへのダイアログ コンポーネントの追加'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed228c007d41d3c7a0815cb97ea9cd890b3a0c98
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748713"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>手順 7: フォームへのダイアログ コンポーネントの追加
この手順で、図ファイルを開き、背景色を選択するためにプログラムを有効にするには、<xref:System.Windows.Forms.OpenFileDialog> コンポーネントと <xref:System.Windows.Forms.ColorDialog> コンポーネントをフォームに追加します。

 コンポーネントは、いくつかの点でコントロールに似ています。 コンポーネントは**ツールボックス**を使用してフォームに追加し、そのプロパティの設定には **[プロパティ]** ウィンドウを使用します。 ただし、コントロールとは異なり、コンポーネントをフォームに追加しても、ユーザーに表示される項目がフォームに追加されるわけではありません。 代わりに、コードで発生させることができる特定の動作が提供されます。 ここで追加するのは、**[ファイルを開く]** ダイアログ ボックスを開くコンポーネントです。

 ![ビデオへのリンク](../data-tools/media/playvideo.gif)このトピックのビデオ版については、「[Tutorial 1: Create a picture viewer in Visual Basic - Video 3](http://go.microsoft.com/fwlink/?LinkId=205213)」(チュートリアル 1: Visual Basic によるピクチャ ビューアーの作成 - ビデオ 3) または「[Tutorial 1: Create a picture viewer in C# - Video 3](http://go.microsoft.com/fwlink/?LinkId=205202)」(チュートリアル 1: C# によるピクチャ ビューアーの作成 - ビデオ 3) をご覧ください。 これらのビデオでは、旧バージョンの Visual Studio を使用しているため、一部のメニュー コマンドやその他のユーザー インターフェイス要素が若干異なります。 ただし、概念および手順は、現在のバージョンの Visual Studio でも同様です。

## <a name="to-add-dialog-components-to-your-form"></a>フォームにダイアログ コンポーネントを追加するには

1.  **Windows フォーム デザイナー** (**Form1.cs [デザイン]** または **Form1.vb [デザイン]**) を選択し、**ツールボックス**の **[ダイアログ]** グループを開きます。

    > [!NOTE]
    >  **ツールボックス**の **[ダイアログ]** グループには、多数の便利なダイアログ ボックスを開くコンポーネントが含まれています。これらは、ファイルを開く、ファイルを保存する、フォルダーを参照する、フォントや色を選択するなど、さまざまな用途で使用できます。 このプロジェクトでは、OpenFileDialog と ColorDialog という 2 つのダイアログ コンポーネントを使用します。

2.  **openFileDialog1** というコンポーネントをフォームに追加するには、**[OpenFileDialog]** をダブルクリックします。 **colorDialog1** というコンポーネントをフォームに追加するには、**ツールボックス**の **[ColorDialog]** をダブルクリックします  (このコンポーネントはチュートリアルの次の手順で使用します)。**Windows フォーム デザイナー**の下部の領域 (**ピクチャ ビューアー** フォームの下) に、次の図に示すように、追加した 2 つのダイアログ コンポーネントのそれぞれに対応するアイコンが表示されます。

     ![ダイアログ コンポーネント](../ide/media/express_dialogsadded.png)
**ダイアログ** コンポーネント

3.  **Windows フォーム デザイナー**の下部にある領域で **[openFileDialog1]** アイコンを選択します。 2 つのプロパティを次のように設定します。

    -   **Filter** プロパティを次のように設定します (コピーして貼り付けることができます)。

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    -   **Title** プロパティを **Select a picture file** に設定します。

         **Filter** プロパティの設定は、**[Select a picture]** ファイル ダイアログ ボックスに表示されるファイルの種類を指定します。

    > [!NOTE]
    >  他のアプリケーションで **[ファイルを開く]** ダイアログ ボックスの例を確認するには、**メモ帳**または**ペイント**を開き、メニュー バーで、**[ファイル]** > **[開く]** の順に選択します。 下部にある **[ファイルの種類]** ドロップダウン リストに注目してください。 ここではそのボックスの内容を、**OpenFileDialog** コンポーネントの **Filter** プロパティを使用して設定しました。 また、**Title** プロパティと **Filter** プロパティが **[プロパティ]** ウィンドウで太字になっていることに注目してください。 IDE では、既定値とは異なる値に変更されたプロパティがわかるように、それらが太字で示されます。

## <a name="to-continue-or-review"></a>続行または確認するには

-   次のチュートリアルの手順に進む場合は、「[手順 8: [Show a Picture] ボタンのイベント ハンドラーのコードの記述](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)」をご覧ください。

-   前のチュートリアルの手順に戻る場合は、「[手順 6: ボタン コントロールの名前の設定](../ide/step-6-name-your-button-controls.md)」をご覧ください。
