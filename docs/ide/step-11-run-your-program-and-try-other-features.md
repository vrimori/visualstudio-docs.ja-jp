---
title: '手順 11: プログラムの実行とその他の機能の使用'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87992bb8ab2557dbca4c8e7e3a94dd99e5de7682
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671925"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>手順 11: プログラムの実行とその他の機能の使用
プログラムが完成し、実行する準備が整いました。 プログラムを実行して <xref:System.Windows.Forms.PictureBox> の背景色を設定できます。 さらに詳しく学習するには、フォームの色の変更、ボタンとチェック ボックスのカスタマイズ、フォームのプロパティの変更などを行って、プログラムを変更してみてください。

 サンプルの完全バージョンをダウンロードするには、「[Complete Picture Viewer tutorial sample](https://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8)」 (画像ビューアーのチュートリアルの完全なサンプル) を参照してください。

 ![ビデオへのリンク](../data-tools/media/playvideo.gif)このトピックのビデオ版については、「[チュートリアル 1: Visual Basic によるピクチャ ビューアーの作成 - ビデオ 5](http://go.microsoft.com/fwlink/?LinkId=205216)」または「[チュートリアル 1: C# によるピクチャ ビューアーの作成 - ビデオ 5](http://go.microsoft.com/fwlink/?LinkId=205206)」をご覧ください。 これらのビデオでは、旧バージョンの Visual Studio を使用しているため、一部のメニュー コマンドやその他のユーザー インターフェイス要素が若干異なります。 ただし、概念および手順は、現在のバージョンの Visual Studio でも同様です。

## <a name="to-run-your-program-and-set-the-background-color"></a>プログラムを実行して背景色を設定するには

1.  **F5** キーを押すか、メニュー バーで **[デバッグ]** > **[デバッグ開始]** の順にクリックします。

2.  ピクチャを開く前に、**[Set the background color]** ボタンをクリックします。 **[色]** ダイアログ ボックスが表示されます。

     ![[色] ダイアログ ボックス](../ide/media/express_colordialog.png)
 **[色]** ダイアログ ボックス

3.  色を選択して PictureBox の背景色を設定します。 `backgroundButton_Click()` メソッドを詳しく調べて動作を確認します。

    > [!NOTE]
    >  ピクチャは、**[ファイルを開く]** ダイアログ ボックスに URL を貼り付けることでインターネットから読み込むことができます。 背景色の表示を確認するには、背景が透明な画像を探してみてください。

4.  **[Clear the picture]** ボタンをクリックして、ピクチャが消去されることを確認します。 次に、**[閉じる]** ボタンをクリックしてプログラムを終了します。

## <a name="to-try-other-features"></a>その他の機能を試すには

-   **BackColor** プロパティを使用して、フォームとボタンの色を変更します。

-   **Font** プロパティと **ForeColor** プロパティを使用して、ボタンとチェック ボックスをカスタマイズします。

-   フォームの **FormBorderStyle** プロパティと **ControlBox** プロパティを変更します。

-   フォームの **AcceptButton** プロパティと **CancelButton** プロパティを使用して、ユーザーが **Enter** キーまたは **Esc** キーを押したときに自動的にそれらのボタンが選択されるようにします。 **[ファイルを開く]** ダイアログ ボックスが、ユーザーが **Enter** キーを押したときに開き、**Esc** キーを押したときに閉じるようにプログラムを設定します。

## <a name="to-continue-or-review"></a>続行または確認するには

-   Visual Studio でのプログラミングの詳細については、「[プログラミングの概念](https://msdn.microsoft.com/Library/65c12cca-af4f-4017-886e-2dbc00a189d6)」を参照してください。

-   Visual Basic の詳細については、「[Visual Basic でのアプリケーションの開発](/dotnet/visual-basic/developing-apps/index)」を参照してください。

-   Visual C# の詳細については、「[C# 言語と .NET Framework の概要](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework)」を参照してください。

-   次のチュートリアルに進むには、「[チュートリアル 2: 制限時間ありの計算クイズの作成](../ide/tutorial-2-create-a-timed-math-quiz.md)」を参照してください。

-   チュートリアルの前の手順に戻るには、「[手順 10: その他のボタンおよびチェック ボックスに対するコードの記述](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)」を参照してください。
