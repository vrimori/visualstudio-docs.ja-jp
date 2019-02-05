---
title: '手順 1: Windows フォーム アプリケーション プロジェクトの作成'
ms.date: 01/26/2019
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbd6fb3733b95a92057b626f79db62698435b7c2
ms.sourcegitcommit: 447f2174bdecdd471d8a8e11c19554977db620a0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2019
ms.locfileid: "55089254"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>手順 1: Windows フォーム アプリケーション プロジェクトの作成

ピクチャ ビューアーを作成する場合、最初の手順は、Windows フォーム アプリケーション プロジェクトを作成することです。

 ![ビデオへのリンク](../data-tools/media/playvideo.gif)このトピックのビデオ版については、「[Tutorial 1:Create a picture viewer in Visual Basic - Video 1](http://go.microsoft.com/fwlink/?LinkId=205209)」(チュートリアル 1: Visual Basic でピクチャ ビューアーを作成する - ビデオ 1) または「[Tutorial 1:Create a picture viewer in C# - Video 1](http://go.microsoft.com/fwlink/?LinkId=205199)」(チュートリアル 1: C# でピクチャ ビューアーを作成する - ビデオ 1) をご覧ください。 これらのビデオでは、旧バージョンの Visual Studio を使用しているため、一部のメニュー コマンドやその他のユーザー インターフェイス要素が若干異なります。 ただし、概念および手順は、現在のバージョンの Visual Studio でも同様です。

## <a name="to-create-a-windows-forms-application-project"></a>Windows フォーム アプリケーション プロジェクトを作成するには

1. メニュー バーで、**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。 ダイアログ ボックスは次のようになります。

     ![[新しいプロジェクト] ダイアログ ボックス](../ide/media/newprojectdialogcallouts.png)<br/>
***[新しいプロジェクト]** ダイアログ ボックス*

2. **[新しいプロジェクト]** ダイアログ ボックスの左側で、**[Visual C#]** または **[Visual Basic]** のいずれかを選択します。

3. テンプレート リストで、**[Windows フォーム アプリケーション (.NET Framework)]** を選択します。 新しいフォームに「**PictureViewer**」という名前を付け、**[OK]** をクリックします。

    >[!NOTE]
    >**[Windows フォーム アプリケーション (.NET Framework)]** テンプレートが表示されない場合は、Visual Studio インストーラーを使用して **[.NET デスクトップ開発]** ワークロードをインストールします。<br/><br/>![Visual Studio インストーラーでの [.NET デスクトップ開発] ワークロード](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> 詳細については、「[Visual Studio 2017 のインストール](../install/install-visual-studio.md)」を参照してください。

     Visual Studio はプログラムのソリューションを作成します。 ソリューションは、プログラムに必要なすべてのプロジェクトとファイルのコンテナーとして機能します。 これらについては、このチュートリアルで後ほど詳しく説明します。

4. 次の図は、Visual Studio に表示される内容を示しています。

    > [!NOTE]
    > ウィンドウ レイアウトは、この図とは多少異なる場合があります。 実際のウィンドウ レイアウトは、Visual Studio のバージョン、使用しているプログラミング言語、その他の要素によって異なります。 ただし、3 つのウィンドウがすべて表示されることを確認する必要があります。

     ![IDE ウィンドウ](../ide/media/express_ideoverview_visio.png)<br/>***IDE** ウィンドウ*

     インターフェイスには、3 つのウィンドウ (メイン ウィンドウ、**ソリューション エクスプローラー**、**[プロパティ]** ウィンドウ) があります。

     これらのウィンドウのいずれかが表示されていない場合は、メニュー バーで **[ウィンドウ]** > **[ウィンドウ レイアウトのリセット]** の順に選択して、既定のウィンドウ レイアウトを復元します。 メニュー コマンドを使用してウィンドウを表示することもできます。 メニュー バーで、**[表示]** > **[プロパティ ウィンドウ]** または **[ソリューション エクスプローラー]** の順に選択します。 他のウィンドウが開いている場合は、右上隅の **[閉じる]** (x) ボタンを選択して閉じます。

5. 図に表示されているウィンドウは次のとおりです (左上から時計回り順)。

    - **メイン ウィンドウ** このウィンドウでは、フォームの操作やコードの編集など、ほとんどの作業を行います。 図では、このウィンドウで**フォーム エディター**にフォームが表示されています。 ウィンドウの上部には、**[スタート ページ]** タブと **[Form1.cs [デザイン]]** タブが表示されています  (Visual Basic では、タブの名前は *.cs* ではなく *.vb* で終わります)。

    - **ソリューション エクスプローラーウィンドウ** このウィンドウでは、ソリューション内のすべての項目を確認し、各項目に移動できます。 ファイルを選択すると、**[プロパティ]** ウィンドウの内容が変わります。 コード ファイル (Visual C# の場合は *.cs*、Visual Basic の場合は *.vb* で終わるファイル) を開くと、コード ファイルまたはコード ファイルのデザイナーが表示されます。 デザイナーは、ボタンやリストなどのコントロールを追加できるビジュアル サーフェイスです。 Visual Studio のフォームでは、デザイナーは **Windows フォーム デザイナー**と呼ばれます。

    - **[プロパティ] ウィンドウ** このウィンドウでは、他のウィンドウで選択した項目のプロパティを変更できます。 たとえば、Form1 を選択した場合、**Text** プロパティを設定してタイトルを変更し、**Backcolor** プロパティを設定して背景色を変更することができます。

    > [!NOTE]
    > **ソリューション エクスプローラー**の先頭行には、"**ソリューション 'PictureViewer' (1 プロジェクト)**" と表示されています。これは、Visual Studio によってソリューションが作成されたことを意味します。 ソリューションには複数のプロジェクトを含めることができますが、ここでは、プロジェクトを 1 つだけ含むソリューションを使用します。

6. メニュー バーで、**[ファイル]** > **[すべてを保存]** の順に選択します。

     または、次の図に示すツール バーの **[すべて保存]** ボタンを選択します。

     ![[すべてを保存] ツール バー ボタン](../ide/media/express_iconsaveall.png)<br/>
***[すべてを保存]** ツール バー ボタン*

     Visual Studio によって自動的にフォルダー名およびプロジェクト名が指定され、projects フォルダーにプロジェクトが保存されます。

## <a name="to-continue-or-review"></a>続行または確認するには

- チュートリアルの次の手順に進むには、「[手順 2:プログラムを実行する](../ide/step-2-run-your-program.md)」を参照してください。

- 概要のトピックに戻るには、「[チュートリアル 1: ピクチャ ビューアーの作成](../ide/tutorial-1-create-a-picture-viewer.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [新しい Windows フォームの作成](/dotnet/framework/winforms/creating-a-new-windows-form/)