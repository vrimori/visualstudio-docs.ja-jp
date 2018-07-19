---
title: '[データ ソース] ウィンドウにカスタム コントロールを追加する'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: af6e0521fa2beb266d2022b73278bc6b07ae7dc3
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843937"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>[データ ソース] ウィンドウにカスタム コントロールを追加する
項目をドラッグすると、**データソース**データ バインド コントロールを作成するデザイン サーフェイスにウィンドウを作成するコントロールの種類を選択できます。 ウィンドウ内の各項目から選択できるコントロールを表示するドロップダウン リストがあります。 各項目に関連付けられたコントロールのセットは、項目のデータ型によって決まります。 作成するコントロールが一覧に表示されない場合は、コントロールをリストに追加するのには、このトピックの手順に従うことができます。

 内の項目を作成するデータ バインド コントロールの選択の詳細については、**データソース**ウィンドウを参照してください[データ ソース ウィンドウからドラッグするときに作成するコントロールを設定](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。

> [!NOTE]
>  使用している設定またはエディションによっては、ヘルプの記載と異なるダイアログ ボックスやメニュー コマンドが表示される場合があります。 設定を変更する、**ツール**メニューの **インポートおよびエクスポート設定**します。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

##  <a name="customizinglist"></a> データ型のバインド可能なコントロールのリストをカスタマイズします。
 追加または使用可能なコントロール内の項目の一覧からコントロールを削除する、**データ ソース**を次の手順を実行して、特定のデータ型を持つウィンドウです。

#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>データ型の一覧表示するコントロールを選択するには

1.  WPF デザイナーまたは Windows フォーム デザイナーが開いていることを確認します。

2.  **データソース**ウィンドウでは、ウィンドウに追加したデータ ソースの一部である項目をクリックし、項目のドロップダウン メニューをクリックします。

3.  ドロップダウン メニューでクリックして**カスタマイズ**します。 次のダイアログ ボックスのいずれかが開きます。

    -   場合、 **Windows フォーム デザイナー**が開いて、**データ UI カスタマイズ**のページ、**オプション** ダイアログ ボックスが表示されます。

    -   場合、 **WPF デザイナー**が開いて、**コントロールのバインドのカスタマイズ** ダイアログ ボックスが表示されます。

4.  データ型の選択 ダイアログ ボックスで、**データ型**ドロップダウン リスト。

    -   テーブルまたはオブジェクトをコントロールのリストをカスタマイズするには、次のように選択します。 **[一覧]** します。

    -   テーブルの列またはオブジェクトのプロパティのコントロールのリストをカスタマイズするには、基になるデータ ストアで列またはプロパティのデータ型を選択します。

    -   ユーザー定義の図形を持つデータ オブジェクトを表示するコントロールのリストをカスタマイズするには、次のように選択します。 **[その他]** します。 たとえば、 **[その他]** アプリケーションに特定のオブジェクトの 1 つ以上のプロパティからデータを表示するカスタム コントロールがある場合。

5.  **コントロールに関連付けられている**ボックスで、選択したデータの種類、使用可能にする各コントロールを選択するか、一覧から削除するすべてのコントロールの選択を解除します。

    > [!NOTE]
    >  を選択するコントロールが表示されないかどうか、**コントロールに関連付けられている**ボックスで、一覧に、コントロールを追加する必要があります。 詳細については、次を参照してください。[データ型のコントロールが関連付けられているコントロールの一覧を追加する](#addingcontrols)します。

6.  **[OK]** をクリックします。

7.  **データソース**ウィンドウで、クリック データの項目を 1 つまたは複数のコントロールをだけ関連付けられている入力項目のドロップダウン メニューをクリックします。

     選択したコントロール、**コントロールに関連付けられている**ボックスは、項目のドロップダウン メニューで表示されます。

##  <a name="addingcontrols"></a> コントロールをデータ型に関連付けられたコントロールの一覧に追加します。
 データ型を含むコントロールを関連付けるコントロールはで表示されていない場合、**関連付けられているコントロール**ボックスで、一覧に、コントロールを追加する必要があります。 コントロールは、現在のソリューションまたは参照先アセンブリにあるである必要があります。 使用する必要がありますも、**ツールボックス**コントロールのデータ バインディングの動作を指定する属性があるとします。

#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>関連付けられたコントロールのリストにコントロールを追加するには

1.  必要なコントロールを追加、**ツールボックス**を右クリックし、**ツールボックス**を選択して**アイテムの選択**します。

     コントロールは、次の属性のいずれかが必要です。

    |属性|説明|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|など、データの 1 つの列 (またはプロパティ) を表示する単純なコントロールでは、この属性の実装を<xref:System.Windows.Forms.TextBox>します。|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|など、データのリスト (またはテーブル) を表示するコントロールのこの属性の実装を<xref:System.Windows.Forms.DataGridView>します。|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|などのデータが 1 つの列またはプロパティを表示する必要があるのもリスト (またはテーブル) を表示するコントロールのこの属性の実装を<xref:System.Windows.Forms.ComboBox>します。|

2.  Windows フォームでは、上、**オプション** ダイアログ ボックスで、**データ UI カスタマイズ**ページ。 または、WPF では、開く、**コントロールのバインドのカスタマイズ** ダイアログ ボックス。 詳細については、次を参照してください。[データ型のバインド可能なコントロールのリストをカスタマイズ](#customizinglist)します。

3.  **コントロールに関連付けられている**ボックスに追加したコントロール、**ツールボックス**が表示されます。

    > [!NOTE]
    >  現在のソリューション内、または参照アセンブリに配置されている唯一のコントロールは、関連付けられたコントロールの一覧に追加できます。 (コントロールする必要がありますも実装データ バインディング属性の 1 つ前の表にします。)データがないカスタム コントロールをバインドする、**データ ソース**ウィンドウからコントロールをドラッグ、**ツールボックス**からバインド先の項目をドラッグ、デザイン画面上に、**データソース**コントロール ウィンドウ。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)