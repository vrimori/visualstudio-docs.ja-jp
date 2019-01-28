---
title: Office ソリューションで WPF コントロールを使用します。
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 70c77e3b093947703680ab7253fdee0a6c3d60cd
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869763"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Office ソリューションで WPF コントロールを使用します。

Visual Studio の Office 開発ツールを使用して作成されたソリューションは、Windows フォーム コントロールを使用して直接操作することを前提としていますが、ソリューションで WPF コントロールを使用することもできます。 Windows Presentation Foundation (WPF) は、ユーザー インターフェイスをデザインするときに Windows フォームの代わりとして使用できます。 WPF では、UI、メディア、および文書を取り込むための新しい手法として、Extensible Application Markup Language (XAML) というマークアップ言語を使用します。 詳細については、次を参照してください。 [WPF の概要](../designers/introduction-to-wpf.md)します。

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Office ソリューションの Windows フォーム コントロールをホストする UI 要素は、WPF コントロールもホストできます。 そうした UI 要素には次のようなものがあります。

-   ドキュメント レベルのカスタマイズに含まれる文書およびワークシート

-   ドキュメント レベルのカスタマイズに含まれる操作ウィンドウ

-   VSTO アドインにおけるカスタム作業ウィンドウ

-   Outlook 用 VSTO アドインのフォーム領域

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>デザイン時に、Office プロジェクトに WPF コントロールを追加します。

Office ソリューションの UI 要素に WPF コントロールを直接追加することはできません。 代わりに、追加、**ユーザー コントロール (WPF)** アイテムをプロジェクト、および WPF コントロールのデザイン画面として使用します。 次に、WPF ユーザー コントロールをプロジェクトの UI 要素に追加します。

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>操作ウィンドウ、カスタム作業ウィンドウ、またはフォーム領域に WPF コントロールを追加するには

1.  カスタム作業ウィンドウ、操作ウィンドウ、またはフォーム領域を追加するプロジェクトを開きます。

2.  追加、**ユーザー コントロール (WPF)** 項目をプロジェクトにします。

3.  **ツールボックス**、WPF ユーザー コントロールのデザイン画面に WPF コントロールを追加します。

     既定では、WPF ユーザー コントロール デザイナーが開いているとき、**ツールボックス**WPF コントロールだけが含まれています。

4.  プロジェクトをビルドします。

5.  操作ウィンドウ、フォーム領域、またはカスタム作業ウィンドウをプロジェクトに追加します。

    -   フォーム領域を追加、 **Outlook フォーム領域**プロジェクト項目。 詳細については、「[方法 :フォーム領域を Outlook アドイン プロジェクトに追加](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)します。

    -   操作ウィンドウ、追加、**操作ウィンドウ コントロール**または**ユーザー コントロール**プロジェクト項目。 詳細については、「[方法 :Word 文書に操作ウィンドウを追加したり、Excel ブック](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)と[方法。Word 文書に操作ウィンドウを追加したり、Excel ブック](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)します。

    -   カスタム作業ウィンドウは、追加、**ユーザー コントロール**プロジェクト項目。 詳細については、「[方法 :カスタム作業ウィンドウをアプリケーションに追加](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)します。

6.  *ProjectName* **WPF ユーザー コントロール**のタブ、**ツールボックス**、操作ウィンドウ、フォーム領域、またはカスタム作業ウィンドウのデザイナーに WPF ユーザー コントロールをドラッグします。

     UI 要素内の WPF ユーザー コントロールをホストする <xref:System.Windows.Forms.Integration.ElementHost> オブジェクトが自動的に作成されます。

7.  プロジェクトをリビルドします。

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>ドキュメント レベルのプロジェクト内の文書またはワークシートに WPF コントロールを追加するには

1.  Word または Excel のドキュメント レベルのプロジェクトを開きます。

2.  追加、**ユーザー コントロール (WPF)** 項目をプロジェクトにします。

3.  **ツールボックス**、WPF ユーザー コントロールのデザイン画面に WPF コントロールを追加します。

4.  プロジェクトをビルドします。

5.  追加、**ユーザー コントロール**をプロジェクトに項目 (つまり、Windows フォーム ユーザー コントロール)。

6.  Windows フォーム ユーザー コントロールのデザイナーを開きます。

7.  *ProjectName* **WPF ユーザー コントロール**のタブ、**ツールボックス**デザイナーに WPF ユーザー コントロールをドラッグします。

     Windows フォーム ユーザー コントロール内の WPF ユーザー コントロールをホストする <xref:System.Windows.Forms.Integration.ElementHost> オブジェクトが自動的に作成されます。

8.  Windows フォーム ユーザー コントロールを文書またはブックにプログラムで追加するコードを作成します。 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)します。

    > [!NOTE]
    > Windows フォーム ユーザー コントロールをデザイナー上の文書またはワークシートにドラッグすることはできません。

9. プロジェクトをリビルドします。

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>ElementHost クラスを使用して WPF コントロールのホスト

Visual Studio には Office ソリューションで Windows フォーム コントロールを使用できるようにする機能がありますが、WPF コントロールを対象とする同様の機能はありません。 たとえば、追加できます Windows フォーム コントロールを文書とワークシート デザイン時からコントロールをドラッグして、**ツールボックス**、またはヘルパー メソッドを使用して実行時にします。 それに対し、これらの機能は WPF コントロールには使用できません。

WPF コントロールでは、Windows フォーム コントロールまたはフォームと WPF コントロールとの間の統合レイヤーとして <xref:System.Windows.Forms.Integration.ElementHost> クラスを使用します。 デザイン時に WPF コントロールをソリューションに追加すると、<xref:System.Windows.Forms.Integration.ElementHost> オブジェクトが自動的に作成されます。

## <a name="wpf-resources"></a>WPF リソース

Windows フォーム コントロールおよびフォーム上での WPF のホストに関連するアーキテクチャおよびデザイン上の問題の詳細については、以下のトピックを参照してください。

-   [Windows フォームと WPF の相互運用性入力アーキテクチャ](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

-   [Windows フォームと WPF プロパティのマッピング](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

-   [WPF と Windows フォームの相互運用性](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

-   [Windows フォーム コントロールおよび同等の WPF コントロール](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Visual Studio でデザイン時に WPF コントロールを Windows フォーム コントロールおよびフォームに追加する方法の詳細については、以下のトピックを参照してください。

-   [チュートリアル: デザイン時に Windows フォームで新しい WPF コンテンツを作成します。](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

-   [チュートリアル: デザイン時に Windows フォームでの WPF コンテンツを配置します。](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

-   [チュートリアル: WPF コンテンツのスタイル](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>関連項目

- [Office UI のカスタマイズ](../vsto/office-ui-customization.md)
- [Office ドキュメントの概要での Windows フォーム コントロール](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [操作ウィンドウの概要](../vsto/actions-pane-overview.md)
- [カスタム作業ウィンドウ](../vsto/custom-task-panes.md)
- [Outlook フォーム領域を作成します。](../vsto/creating-outlook-form-regions.md)
- [方法: Word 文書または Excel ブックに操作ウィンドウを追加します。](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [方法: アプリケーションにカスタム作業ウィンドウを追加します。](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [方法: フォーム領域を Outlook アドイン プロジェクトに追加します。](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
