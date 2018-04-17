---
title: データ ソース ウィンドウにカスタム コントロールを追加 |Microsoft ドキュメント
ms.custom: ''
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d00e818c0cfaa2659f55e5eb8bb8e4e4a87e8abc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>[データ ソース] ウィンドウにカスタム コントロールを追加する
項目をドラッグすると、**データソース**データ バインド コントロールを作成するデザイン サーフェイスにウィンドウを作成するコントロールの種類を選択することができます。 ウィンドウ内の各項目から選択できるコントロールを表示するドロップダウン リストがあります。 各アイテムに関連付けられたコントロールのセットは、アイテムのデータ型によって決定されます。 作成するコントロールが一覧に表示されない場合、コントロールをリストに追加するのには、このトピックの手順に従うことができます。  
  
 内の項目を作成するデータ バインド コントロールの選択の詳細については、**データソース**ウィンドウを参照してください[データ ソース ウィンドウからドラッグしたときに作成するコントロールを設定](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)です。  
  
> [!NOTE]
>  使用している設定またはエディションによっては、ヘルプの記載と異なるダイアログ ボックスやメニュー コマンドが表示される場合があります。 設定を変更する、**ツール**メニューの **インポートおよびエクスポート設定**です。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
##  <a name="customizinglist"></a> データ型にバインドできるコントロールのリストをカスタマイズします。  
 追加または使用可能なコントロール内の項目の一覧からコントロールを削除する、**データソース**以下の手順に従って、特定のデータ型を持つウィンドウです。  
  
#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>データ型の一覧表示するコントロールを選択するには  
  
1.  WPF デザイナーまたは Windows フォーム デザイナーが開いていることを確認します。  
  
2.  **データソース** ウィンドウで、ウィンドウに追加したデータ ソースの一部である項目をクリックし、項目のドロップダウン メニューをクリックします。  
  
3.  ドロップダウン メニューでクリックして**カスタマイズ**です。 次のダイアログ ボックスのいずれかが開きます。  
  
    -   Windows フォーム デザイナーが開いている場合、**データ UI カスタマイズ**のページ、**オプション** ダイアログ ボックスが表示されます。  
  
    -   WPF デザイナーが開いている場合、**コントロールのバインドのカスタマイズ** ダイアログ ボックスが表示されます。  
  
4.  データ型の選択 ダイアログ ボックスで、**データ型**ドロップダウン リスト。  
  
    -   テーブルまたはオブジェクトのコントロールのリストをカスタマイズするには、次のように選択します。 **[リスト]**です。  
  
    -   テーブルの 1 つ以上のオブジェクトのプロパティにコントロールのリストをカスタマイズするには、基になるデータ ストア内の列またはプロパティのデータ型を選択します。  
  
    -   ユーザー定義の形状を持つデータ オブジェクトを表示するコントロールのリストをカスタマイズするには、次のように選択します。 **[その他]**です。 たとえば、選択**[その他]**アプリケーションに特定のオブジェクトの 1 つ以上のプロパティからデータを表示するカスタム コントロールがある場合。  
  
5.  **関連付けられているコントロール**ボックスを選択したデータ型で利用できる各コントロールを選択または一覧から削除するすべてのコントロールの選択を解除します。  
  
    > [!NOTE]
    >  を選択するコントロールが表示されないかどうか、**関連付けられているコントロール**ボックス、一覧に、コントロールを追加する必要があります。 詳細については、次を参照してください。[コントロールのデータ型一覧の関連付けられたコントロールを追加する](#addingcontrols)です。  
  
6.  **[OK]**をクリックします。  
  
7.  **データソース**ウィンドウで、データの項目が 1 つまたは複数のコントロールをだけ関連付けられている入力し、項目のドロップダウン メニューをクリックします。  
  
     選択したコントロール、**関連付けられているコントロール**ボックスが項目のドロップダウン メニューに表示されます。  
  
##  <a name="addingcontrols"></a> データ型に関連付けられているコントロールのリストにコントロールを追加します。  
 コントロールをデータ型に関連付けるたいが、コントロールがない場合、**関連付けられているコントロール**ボックス、一覧に、コントロールを追加する必要があります。 コントロールは、現在のソリューションまたは参照先のアセンブリに存在する必要があります。 使用する必要もあります、**ツールボックス**コントロールのデータ バインディングの動作を指定する属性を持つとします。  
  
#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>関連付けられたコントロールのリストにコントロールを追加するには  
  
1.  必要なコントロールを追加、**ツールボックス**を右クリックして、**ツールボックス**を選択して**アイテムの選択**です。  
  
     コントロールは、次の属性のいずれかが必要です。  
  
    |属性|説明|  
    |---------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|など、データの 1 つの列 (またはプロパティ) を表示する簡単なコントロールのこの属性を実装する、<xref:System.Windows.Forms.TextBox>です。|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|などの一覧またはテーブル)、データを表示するコントロールのこの属性を実装する、<xref:System.Windows.Forms.DataGridView>です。|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|などの一覧またはテーブル)、1 つの列またはプロパティを表示する必要はデータを表示するコントロールのこの属性を実装する、<xref:System.Windows.Forms.ComboBox>です。|  
  
2.  Windows フォームの上、**オプション** ダイアログ ボックスで、**データ UI カスタマイズ**ページ。 あるいは、WPF では、開く、**コントロールのバインドのカスタマイズ** ダイアログ ボックス。 詳細については、次を参照してください。[データ型にバインドできるコントロールの一覧をカスタマイズする](#customizinglist)です。  
  
3.  **関連付けられているコントロール** ボックスに追加したコントロール、**ツールボックス**が表示されます。  
  
    > [!NOTE]
    >  現在のソリューションまたは参照先アセンブリ内に存在する唯一のコントロールは、関連付けられたコントロールの一覧に追加できます。 (コントロール必要がありますも実装データ バインディング属性の 1 つ前の表にします。)データでは使用できませんをカスタム コントロールをバインドする、**データ ソース** ウィンドウからコントロールをドラッグ、**ツールボックス**からバインド先の項目をドラッグ、デザイン画面上に、**データソース**ウィンドウからコントロールにします。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)