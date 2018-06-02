---
title: リボンの概要
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, multiple Ribbons
- Ribbon [Office development in Visual Studio], about Ribbon
- toolbars [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], multiple Ribbons
- toolbars [Office development in Visual Studio]
- custom Ribbon, multiple Ribbons
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6f78f55f1f36f23331a9e27228c0afa567429e30
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693021"
---
# <a name="ribbon-overview"></a>リボンの概要
  リボンは、簡単に見つけられるように、関連するコマンドを整理する方法です。 コマンドは、リボン上のコントロールとして表示されます。 コントロールがまとめ*グループ*アプリケーション ウィンドウの上端に水平方向のストリップに沿ったです。 関連するグループは、タブに整理されます。  
  
 以前のバージョンの Microsoft Office system でメニューおよびツールバーを使用してアクセスしていた機能の多くは、リボンを使用して今すぐアクセスできます。 詳細については、技術記事を参照してください。 [2007 Microsoft Office system のユーザー インターフェイスの開発者向け概要](http://go.microsoft.com/fwlink/?LinkID=70860)です。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="customize-the-microsoft-office-ribbon"></a>Microsoft Office のリボンをカスタマイズします。  
 リボンをカスタマイズするには、Office プロジェクトに次のリボン項目のいずれかを追加します。  
  
-   **リボン (ビジュアル デザイナー)**  
  
-   **リボン (XML)**  
  
 たとえば、Excel のリボンをカスタマイズするには、Excel VSTO アドイン プロジェクトにリボン項目を追加します。  
  
### <a name="ribbon-visual-designer-item"></a>リボン (ビジュアル デザイナー) 項目  
 **リボン (ビジュアル デザイナー)** 項目には、設計およびカスタム リボンを開発するためのより簡単にする高度なツールが用意されています。 使用して、**リボン (ビジュアル デザイナー)** 次の方法でリボンをカスタマイズする項目。  
  
-   カスタムまたは組み込みタブをリボンに追加します。  
  
-   カスタム タブまたは組み込みタブにカスタム グループを追加します。  
  
    > [!NOTE]  
    >  グループまたは組み込みタブは、Microsoft Office アプリケーションのリボンに既に存在する 1 つです。 たとえば、**データ**タブは、Excel の組み込みタブです。 **接続**のグループは組み込みグループ、**データ**タブです。  
  
-   カスタム コントロールをカスタム グループに追加します。  
  
-   Backstage ビューにカスタム コントロールを追加します。  
  
 使用してリボンをカスタマイズする方法について、**リボン (ビジュアル デザイナー)** 項目は、「[リボン デザイナー](../vsto/ribbon-designer.md)です。  
  
### <a name="ribbon-xml-item"></a>リボン (XML) 項目  
 使用して、**リボン (XML)** によってサポートされていない方法でリボンをカスタマイズする場合は項目、**リボン (ビジュアル デザイナー)** 項目。 使用して、**リボン (XML)** 次の方法でリボンをカスタマイズする項目。  
  
-   追加*組み込み*カスタム タブまたは組み込みタブにグループ。  
  
-   組み込みコントロールをカスタム グループに追加します。  
  
-   カスタム コードを追加して、組み込みコントロールのイベント ハンドラーをオーバーライドします。  
  
-   クイック アクセス ツールバーをカスタマイズします。  
  
-   修飾 ID を使用して、VSTO アドイン間でリボンのカスタマイズを共有します。  
  
 使用してリボンをカスタマイズする方法についての詳細、**リボン (XML)** 項目は、「[リボン XML](../vsto/ribbon-xml.md)です。  
  
## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>リボンをリボン デザイナーからリボン XML にエクスポートします。  
 場合は、リボン デザイナーを使用してリボンを作成しした方法でリボンをカスタマイズすることを**リボン (ビジュアル デザイナー)** 項目はサポートしていません、リボンを XML にエクスポートすることができます。  
  
 Visual Studio が自動的に作成、**リボン (XML)** し、項目をリボン上の各コントロールの要素と属性を持つリボン XML ファイルを追加します。  
  
 すべての内にあるプロパティ、**プロパティ**リボン デザイナーのウィンドウは、リボン XML ファイルに転送します。  たとえば、Visual Studio がの値をエクスポートしません、**イメージ**または**テキスト**プロパティです。 これは、コントロールのイメージを割り当てたり、コントロールのテキストを設定したりするには、エクスポートしたプロジェクトのリボン コード ファイルにコールバック メソッドを作成する必要があるためです。 Visual Studio で、エクスポート プロセスの一部としてコールバック メソッドが自動的に生成されることはありません。  
  
 また、既定値から変更されていないプロパティ値は、結果として得られるリボン XML ファイルには含められません。  
  
 リボンを XML にエクスポートする方法の詳細については、次を参照してください。[する方法: リボンをリボン デザイナーからリボン XML にエクスポート](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)です。  
  
### <a name="update-the-code"></a>コードを更新します。  
 新しいリボン コード ファイルに追加**ソリューション エクスプ ローラー**です。 このファイルにはリボン XML クラスが含まれています。 ボタンのクリックなどのユーザー操作を処理するには、このクラスの `Ribbon Callbacks` 領域にコールバック メソッドを作成する必要があります。 イベント ハンドラーからこれらのコールバック メソッドにコードを移動し、リボン機能拡張 (RibbonX) プログラミング モデルで動作するようにコードを変更します。 詳細については、「 [Ribbon XML](../vsto/ribbon-xml.md)」を参照してください。  
  
 さらに、`ThisAddIn`、`ThisWorkbook`、または `ThisDocument` のいずれかのクラスに、`CreateRibbonExtensibilityObject` メソッドをオーバーライドして Office アプリケーションにリボン XML クラスを返すコードを追加する必要もあります。  
  
 詳細については、「 [Ribbon XML](../vsto/ribbon-xml.md)」を参照してください。  
  
## <a name="add-multiple-ribbon-items-to-a-project"></a>複数のリボン項目をプロジェクトに追加します。  
 1 つのプロジェクトに複数のリボン項目を追加することができます。 これは、次の 2 つのタスクのいずれかを実行する場合に便利です。  
  
-   Outlook のリボンを作成*インスペクター*です。 詳細については、次を参照してください。 [Outlook のリボンをカスタマイズ](../vsto/customizing-a-ribbon-for-outlook.md)です。  
  
    > [!NOTE]  
    >  インスペクターは、ユーザーが電子メール メッセージを作成するなど、特定のタスクを実行するときに表示されるウィンドウです。  
  
-   実行時に表示するリボンを選択します。  
  
### <a name="select-which-ribbons-to-display-at-runtime"></a>実行時に表示するには、どのリボンを選択します。  
 プロジェクトには、1 つ以上のリボンを含めることができます、ためには、実行時に表示するリボンを選択できます。  
  
 実行時に表示するリボンを選択するには、上書き、`CreateRibbonExtensibilityObject`メソッドで、 `ThisAddin`、 `ThisWorkbook`、または`ThisDocument`プロジェクトと戻り値を表示するリボンのクラスです。 次の例は、という名前のフィールドの値を調べて`myCondition`し、適切なリボンを返します。  
  
> [!NOTE]  
>  この例で使用する構文を使用して作成されたリボンが返されます、**リボン (ビジュアル デザイナー)** 項目。 リボンを使用して作成されてを返すための構文、**リボン (XML)** 項目は若干異なります。 返すの詳細については、**リボン (XML)** 項目は、「[リボン XML](../vsto/ribbon-xml.md)です。  
  
 次のコードを追加します。  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs#1)]  
  
### <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[方法: リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)|Microsoft Office アプリケーションのリボンのカスタマイズを追加する方法を示します、**リボン (ビジュアル デザイナー)** または**リボン (XML)** を Office プロジェクトの項目。|  
|[リボン デザイナー](../vsto/ribbon-designer.md)|リボン デザイナーを使用して、Microsoft Office アプリケーションのリボンにカスタム タブ、グループ、およびコントロールを追加する方法を説明します。|  
|[チュートリアル: リボン デザイナーを使用してカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|リボン デザイナーを使用してカスタム リボン タブを作成する方法について説明します。 リボン デザイナーを使用すると、カスタム タブにコントロールを追加し、位置を設定することができます。|  
|[リボン オブジェクト モデルの概要](../vsto/ribbon-object-model-overview.md)|取得し、実行時にリボン コントロールのプロパティを設定に使用できる、厳密に型指定のオブジェクト モデルの概要を示します。|  
|[チュートリアル: 実行時にリボン上のコントロールを更新します。](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Office アプリケーションにリボンを読み込んだ後に、リボン オブジェクト モデルを使用してリボン上のコントロールを更新する方法について説明します。|  
|[Outlook のリボンをカスタマイズします。](../vsto/customizing-a-ribbon-for-outlook.md)|Microsoft Office Outlook でリボンをカスタマイズするためのガイダンスを提供します。|  
|[InfoPath のリボンをカスタマイズします。](../vsto/customizing-a-ribbon-for-infopath.md)|Microsoft Office InfoPath でリボンをカスタマイズするためのガイダンスを提供します。|  
|[実行時にリボンにアクセスします。](../vsto/accessing-the-ribbon-at-run-time.md)|表示、隠すには、リボンを変更し、カスタム作業ウィンドウ、[操作] ウィンドウまたは Outlook フォーム領域のコントロールからのコードを実行するユーザーを有効にする方法を示します。|  
|[方法: リボンのタブの位置を変更](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|リボン上のタブの順序を変更する方法を示します。|  
|[方法: 組み込みタブをカスタマイズします。](../vsto/how-to-customize-a-built-in-tab.md)|組み込みタブにグループやコントロールを追加する方法について説明します。|  
|[方法: コントロール Backstage ビューを追加します。](../vsto/how-to-add-controls-to-the-backstage-view.md)|クリックしたときに表示されるメニューにコントロールを追加する方法を示しています、**ファイル**です。|  
|[方法: リボン グループにダイアログ ボックス起動ツールを追加](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|リボン上の任意のグループにダイアログ ボックス起動ツールを追加するを示しています。|  
|[方法: リボンをリボン デザイナーからリボン XML にエクスポート](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|デザイナーからリボンをリボン XML にエクスポートすることによって、高度な方法でリボンをカスタマイズする方法を示します。|  
|[リボン XML](../vsto/ribbon-xml.md)|リボン XML を使用してリボンをカスタマイズする方法について説明します。|  
|[チュートリアル: リボン デザイナーを使用してカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|使用してカスタム リボン タブを作成する方法を示します、**リボン (XML)** 項目。|  
  
  