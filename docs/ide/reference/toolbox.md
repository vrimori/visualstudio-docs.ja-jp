---
title: Visual Studio のツールボックス ウィンドウ
ms.date: 01/18/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f296349a6dfda80ff402b1ede0f1da591f6caa9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947090"
---
# <a name="toolbox"></a>ツールボックス

**ツールボックス** ウィンドウには、Visual Studio プロジェクトに追加できるコントロールが表示されます。 ツールボックスを開くには、**[表示]** メニューで **[ツールボックス]** を選択します。

![[ツールボックス] ウィンドウ](media/toolbox.png)

使用しているデザイナー画面にさまざまなコントロールをドラッグ アンド ドロップし、コントロールのサイズや位置を変更できます。

ツールボックスは、XAML ファイルのデザイナー ビューなど、デザイナー ビューと組み合わせて表示されます。 ツールボックスには、現在のデザイナーで使用できるコントロールのみが表示されます。 [ツールボックス] 内で検索し、表示される項目をさらにフィルター処理できます。

> [!NOTE]
> プロジェクトの種類によっては、ツールボックスに項目が表示されない場合もあります。

プロジェクトが対象とする .NET Framework バージョンも、ツールボックスに表示されるコントロール セットに影響します。 プロジェクトのプロパティ ページから、別のバージョンの .NET Framework を対象とするようにプロジェクトを設定できます。 **ソリューション エクスプローラー**でプロジェクト ノードを選択し、メニュー バーで **[プロジェクト]** > **\<[プロジェクト]\> [プロパティ]** の順に選択します。 **[アプリケーション]** タブの **[ターゲット フレームワーク]** ドロップ ダウンを使用します。

## <a name="managing-the-toolbox-window-and-its-controls"></a>ツールボックス ウィンドウと含まれるコントロールの管理

既定では、ツールボックスは、Visual Studio IDE の左側に沿って折りたたまれており、カーソルをそこに移動すると開きます。 カーソルを移動したときに開いたままになるように、ツールボックスを固定することもできます (ツールボックスのツール バー上の **[ピン]** アイコンをクリック)。 また、ツールボックス ウィンドウをドッキング解除して、画面上の任意の場所にドラッグすることもできます。 ツールボックスのツール バーを右クリックし、いずれかのオプションを選択することで、ツールボックスのドッキング、ドッキング解除、および非表示を設定できます。

コンテキスト メニューの次のコマンドを使用すると、ツールボックス タブの項目を再配置することも、カスタム タブやカスタム項目を追加することもできます。

- **[項目名の変更]** - 選択された項目の名前を変更します。

- **[すべて表示]** - 使用可能なコントロールをすべて (現在のデザイナーに適用されるコントロール以外も) 表示します。

- **[一覧の表示]** - コントロールを垂直方向に一覧表示します。 オフの場合は、コントロールが水平方向に表示されます。

- **[アイテムの選択]** - **[ツールボックス アイテムの選択]** ダイアログ ボックスが開き、**[ツールボックス]** に表示する項目を指定できます。 チェック ボックスをオンまたはオフにすることで、項目の表示と非表示を切り替えることができます。

- **[アイテムをアルファベット順に並べ替え]** - 項目を名前順に並べ替えます。

- **[ツール バーのリセット]** - 既定のツールボックス設定および項目を復元します。

- **[タブの追加]** - 新しいツールボックス タブを追加します。

- **[上へ移動]** - 選択した項目を上へ移動します。

- **[下へ移動]** - 選択した項目を下へ移動します。

## <a name="creating-and-distributing-custom-toolbox-controls"></a>カスタム ツールボックス コントロールの作成と配布

[Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) または [Windows フォーム](../../extensibility/creating-a-windows-forms-toolbox-control.md)に基づくプロジェクト テンプレートを使用して、カスタム ツールボックス コントロールを作成できます。 これで、[ツールボックス コントロール インストーラー](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx)を使用してカスタム コントロールをチームメイトに配信したり、Web 上に公開したりできるようになります。

## <a name="help-on-toolbox-tabs"></a>[ツールボックス] のタブに関するヘルプ

次のトピックでは、使用可能な一部の **[ツールボックス]** タブの詳細について説明します。

- [ツールボックス、[データ] タブ](../../ide/reference/toolbox-data-tab.md)

- [ツールボックス、[コンポーネント] タブ](../../ide/reference/toolbox-components-tab.md)

- [ツールボックス、[HTML] タブ](../../ide/reference/toolbox-html-tab.md)
