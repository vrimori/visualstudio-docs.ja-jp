---
title: 'チュートリアル : データセット デザイナーでの DataTable の作成'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2cff383b6e06d8793a7730c36df01e2538b02c36
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174497"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>チュートリアル: データセット デザイナーでの DataTable を作成します。

このチュートリアルを作成する方法を説明する、 <xref:System.Data.DataTable> (せずに、TableAdapter) を使用して、**データセット デザイナー**。 Tableadapter を含むデータ テーブルを作成する方法の詳細については、次を参照してください。[作成し、Tableadapter 構成](../data-tools/create-and-configure-tableadapters.md)します。

## <a name="create-a-new-windows-forms-application"></a>新しい Windows フォーム アプリケーションを作成します。

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

2. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

3. 中央のペインで選択、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**DataTableWalkthrough**を選び、 **OK**。

     **DataTableWalkthrough**プロジェクトが作成されに追加**ソリューション エクスプ ローラー**します。

## <a name="add-a-new-dataset-to-the-application"></a>アプリケーションに新しいデータセットを追加します。

1.  **プロジェクト**メニューの **新しい項目の追加**します。

     **[新しい項目の追加]** ダイアログ ボックスが表示されます。

2.  左側のウィンドウで次のように選択します。**データ**を選択し、**データセット**中央のペインでします。

3.  **[追加]** をクリックします。

     Visual Studio がという名前のファイルを追加します**DataSet1.xsd**プロジェクトで開くと、**データセット デザイナー**。

## <a name="add-a-new-datatable-to-the-dataset"></a>データセットに新しい DataTable を追加します。

1.  ドラッグ、 **DataTable**から、**データセット**のタブ、**ツールボックス**上に、**データセット デザイナー**します。

     という名前のテーブル**DataTable1**データセットに追加されます。

2.  タイトル バーをクリックします。 **DataTable1**名前を変更および`Music`します。

## <a name="add-columns-to-the-datatable"></a>列を DataTable に追加します。

1.  右クリックし、**音楽**テーブル。 をポイント**追加**、 をクリックし、**列**します。

2.  列の名前を付けます`SongID`します。

3.  **プロパティ**ウィンドウで、設定、<xref:System.Data.DataColumn.DataType%2A>プロパティを<xref:System.Int16?displayProperty=fullName>します。

4.  このプロセスを繰り返して、次の列を追加します。

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>テーブルの主キーを設定します。

すべてのデータ テーブルには、主キーを持つ必要があります。 主キーは、データ テーブル内の特定のレコードを一意に識別します。

主キーを設定するを右クリックし、 **SongID**列、およびクリック**主キーの設定**します。 鍵のアイコンが横に表示されます、 **SongID**列。

## <a name="save-your-project"></a>プロジェクトを保存します。

保存する、 **DataTableWalkthrough**プロジェクトで、**ファイル**メニューの **すべて保存**します。

## <a name="see-also"></a>関連項目

- [Visual Studio でデータセットを作成および構成する](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [データの検証](../data-tools/validate-data-in-datasets.md)