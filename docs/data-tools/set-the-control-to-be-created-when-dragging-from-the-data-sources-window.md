---
title: '[データ ソース] ウィンドウからドラッグしたときに作成されるコントロールを設定する'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: daceedd2709de7882ecff5b29a657f706c96175d
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305469"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>[データ ソース] ウィンドウからドラッグしたときに作成されるコントロールを設定する

[データ ソース]** ウィンドウから WPF デザイナーまたは Windows フォーム デザイナーに項目をドラッグすることにより、データ バインド コントロールを作成できます。 [データ ソース]** ウィンドウの各項目には、その項目をデザイナーにドラッグしたときに作成される既定のコントロールが関連付けられています。 ただし、別のコントロールが作成されるようにすることもできます。

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>データ テーブルまたはオブジェクトに対して作成されるコントロールを設定するには

データ テーブルまたはオブジェクトを表す項目を [データ ソース]** ウィンドウからドラッグする前に、すべてのデータを 1 つのコントロールに表示するか、それぞれの列またはプロパティを個別のコントロールに表示するかを選択できます。

ここで、オブジェクト*という用語は、カスタム ビジネス オブジェクト、エンティティ (Entity Data Model のエンティティ)、またはサービスによって返されるオブジェクトを意味します。

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>データ テーブルまたはオブジェクトに対して作成されるコントロールを設定するには

1. 必ず、 **WPF**デザイナーまたは**Windows フォーム**デザイナーが開きます。

2. [データ ソース]** ウィンドウで、設定するデータ テーブルまたはオブジェクトを表す項目を選択します。

   > [!TIP]
   > 場合、**データソース**ウィンドウが開いていない、選択して開くことができます**ビュー** > **その他の Windows** > **のデータソース**.

3. 項目のドロップダウン メニューをクリックし、メニューの次の項目のいずれかをクリックします。

    - 各データ フィールドを個別のコントロールに表示するには、[詳細]** をクリックします。 データ項目をデザイナーにドラッグすると、このアクションにより、親のデータ テーブルまたはオブジェクトの列またはプロパティごとに異なるデータ バインド コントロールが作成され、各コントロールのラベルが作成されます。

    - すべてのデータを単一のコントロールに表示するには、リストで別のコントロールを選択します。たとえば、WPF アプリケーションでは [DataGrid] **または [List]** を選択し、Windows フォーム アプリケーションでは [DataGridView]** を選択します。

    利用できるコントロールのリストは、開いたデザイナー、プロジェクトのターゲットである .NET Framework のバージョン、およびデータ バインディングをサポートするカスタム コントロールをツールボックス**に追加したかどうかによって異なります。 利用可能なコントロールの一覧で、作成するコントロールがない場合は、一覧に、コントロールを追加できます。 詳細については、次を参照してください。[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)します。

    データ テーブルまたはオブジェクトのコントロールの一覧に追加できるカスタム Windows フォーム コントロールを作成する方法については、**データ ソース**ウィンドウを参照してください[複雑なデータをサポートする Windows フォーム ユーザー コントロールの作成バインド](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)します。

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>データ列またはプロパティに対して作成されるコントロールを設定します。

オブジェクトの列またはプロパティを表す項目を [データ ソース]** ウィンドウからデザイナーにドラッグする前に、作成されるコントロールを設定できます。

### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>列またはプロパティに対して作成されるコントロールを設定するには

1. 必ず、 **WPF**デザイナーまたは**Windows フォーム**デザイナーが開きます。

2. [データ ソース]** ウィンドウで、目的のテーブルまたはオブジェクトを展開してその列またはプロパティを表示します。

3. 作成されるコントロールを設定する各列または各プロパティを選択します。

4. 列またはプロパティのドロップダウン メニューをクリックし、項目をデザイナーにドラッグしたときに作成されるコントロールを選択します。

     利用できるコントロールのリストは、開いたデザイナー、プロジェクトのターゲットである .NET Framework のバージョン、およびツールボックス**に追加したデータ バインディングをサポートするカスタム コントロールによって異なります。 作成するコントロールが利用できるコントロールのリストに含まれている場合、コントロールをリストに追加できます。 詳細については、次を参照してください。[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)します。

     データ列またはプロパティのコントロールのリストに追加できるカスタム コントロールを作成する方法については、**データソース**ウィンドウを参照してください[の単純データバインディングをサポートするWindowsフォームユーザーコントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     列またはプロパティのコントロールを作成しない場合は、選択**None**ドロップダウン メニュー。 これは、親のテーブルまたはオブジェクトをデザイナーにドラッグする必要があり、かつ特定の列またはプロパティを含める必要がない場合に便利です。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)