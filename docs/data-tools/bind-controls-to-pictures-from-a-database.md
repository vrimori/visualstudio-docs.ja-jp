---
title: データベースの画像にコントロールをバインドする
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 803de097d05f472e7a5b585a8b58395c45a924ed
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914995"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>データベースの画像にコントロールをバインドする

**[データ ソース]** ウィンドウを使用して、データベースのイメージをアプリケーションのコントロールにバインドできます。 たとえば、WPF アプリケーションの <xref:System.Windows.Controls.Image> コントロールまたは Windows フォーム アプリケーションの <xref:System.Windows.Forms.PictureBox> コントロールにイメージをバインドできます。

データベースの画像は、通常はバイト配列として格納されます。 **[データ ソース]** ウィンドウ内のバイト配列として格納されている項目は、既定ではコントロール型が **[なし]** に設定されています。これは、バイト配列には、シンプルなバイトの配列から大規模なアプリケーションの実行可能ファイルまで、どのようなものでも含めることができるためです。 **[データ ソース]** ウィンドウ内のイメージを表すバイト配列項目のデータ バインド コントロールを作成するには、作成するコントロールを選択する必要があります。

次の手順では、イメージにバインドされている項目が既に **[データ ソース]** ウィンドウに作成されていると仮定します。

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>データベースの画像をコントロールにバインドするには

1.  コントロールを追加するデザイン サーフェイスが WPF デザイナーまたは Windows フォーム デザイナーで開いていることを確認します。

2.  **[データ ソース]** ウィンドウで、目的のテーブルまたはオブジェクトを展開して、その列またはプロパティを表示します。

   > [!TIP]
   > 場合、**データソース**を選択して開くウィンドウが開いていないことが**ビュー** > **その他の Windows** > **データソース**.

3.  イメージ データを含む列またはプロパティを選択し、ドロップダウン コントロール リストから次のいずれかのコントロールを選択します。

    - WPF デザイナーが開いている場合は、**[Image]** を選択します。

    - Windows フォーム デザイナーが開いている場合は、**[PictureBox]** を選択します。

    - または、データ バインディングをサポートし、かつイメージを表示できる、別のコントロールを選択することもできます。 使用するコントロールが利用できるコントロールのリストに含まれていない場合は、そのコントロールをリストに追加してから選択できます。 詳細については、次を参照してください。[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)します。

## <a name="see-also"></a>関連項目

- [Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)