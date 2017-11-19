---
title: "Office ソリューションで WPF コントロールの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: WPF [Office development in Visual Studio]
ms.assetid: 305a212b-0a95-40ad-87aa-22896fe80a04
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f15eea2c0f1e7e62990d860007a7efc4966cb8cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="using-wpf-controls-in-office-solutions"></a>Office ソリューションでの WPF コントロールの使用
  Visual Studio の Office 開発ツールを使用して作成されたソリューションは、Windows フォーム コントロールを使用して直接操作することを前提としていますが、ソリューションで WPF コントロールを使用することもできます。 Windows Presentation Foundation (WPF) は、ユーザー インターフェイスをデザインするときに Windows フォームの代わりとして使用できます。 WPF では、UI、メディア、および文書を取り込むための新しい手法として、Extensible Application Markup Language (XAML) というマークアップ言語を使用します。 詳細については、次を参照してください。 [Visual Studio 2015 での WPF の概要](/dotnet/framework/wpf/getting-started/introduction-to-wpf-in-vs)です。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Office ソリューションの Windows フォーム コントロールをホストする UI 要素は、WPF コントロールもホストできます。 そうした UI 要素には次のようなものがあります。  
  
-   ドキュメント レベルのカスタマイズに含まれる文書およびワークシート  
  
-   ドキュメント レベルのカスタマイズに含まれる操作ウィンドウ  
  
-   VSTO アドインにおけるカスタム作業ウィンドウ  
  
-   Outlook 用 VSTO アドインのフォーム領域  
  
## <a name="adding-wpf-controls-to-office-projects-at-design-time"></a>デザイン時における Office プロジェクトへの WPF コントロールの追加  
 Office ソリューションの UI 要素に WPF コントロールを直接追加することはできません。 代わりに、追加、**ユーザー コントロール (WPF)**をプロジェクトに項目を WPF コントロールのデザイン画面として使用します。 次に、WPF ユーザー コントロールをプロジェクトの UI 要素に追加します。  
  
#### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>操作ウィンドウ、カスタム作業ウィンドウ、またはフォーム領域に WPF コントロールを追加するには  
  
1.  カスタム作業ウィンドウ、操作ウィンドウ、またはフォーム領域を追加するプロジェクトを開きます。  
  
2.  追加、**ユーザー コントロール (WPF)**をプロジェクトに項目。  
  
3.  **ツールボックス**、WPF ユーザー コントロールのデザイン画面に WPF コントロールを追加します。  
  
     既定では、WPF ユーザー コントロール デザイナーが開いている場合、**ツールボックス**WPF コントロールだけが含まれています。  
  
4.  プロジェクトをビルドします。  
  
5.  操作ウィンドウ、フォーム領域、またはカスタム作業ウィンドウをプロジェクトに追加します。  
  
    -   フォーム領域を追加、 **Outlook フォーム領域**プロジェクト項目です。 詳細については、次を参照してください。[する方法: フォーム領域を Outlook アドイン プロジェクトに追加](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)です。  
  
    -   操作ウィンドウ、追加、**操作ウィンドウ コントロール**または**ユーザー コントロール**プロジェクト項目です。 詳細については、次を参照してください。[する方法: Word 文書や Excel ブックに操作ウィンドウを追加](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)と[する方法: Word 文書や Excel ブックに操作ウィンドウを追加](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)です。  
  
    -   カスタム作業ウィンドウは、追加、**ユーザー コントロール**プロジェクト項目です。 詳細については、次を参照してください。[する方法: カスタム作業ウィンドウをアプリケーションに追加](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)です。  
  
6.  *ProjectName* **WPF ユーザー コントロール**のタブ、**ツールボックス**、操作ウィンドウ、フォーム領域、またはカスタム作業ウィンドウのデザイナーに WPF ユーザー コントロールをドラッグします。  
  
     UI 要素内の WPF ユーザー コントロールをホストする <xref:System.Windows.Forms.Integration.ElementHost> オブジェクトが自動的に作成されます。  
  
7.  プロジェクトをリビルドします。  
  
#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>ドキュメント レベルのプロジェクト内の文書またはワークシートに WPF コントロールを追加するには  
  
1.  Word または Excel のドキュメント レベルのプロジェクトを開きます。  
  
2.  追加、**ユーザー コントロール (WPF)**をプロジェクトに項目。  
  
3.  **ツールボックス**、WPF ユーザー コントロールのデザイン画面に WPF コントロールを追加します。  
  
4.  プロジェクトをビルドします。  
  
5.  追加、**ユーザー コントロール**をプロジェクトに項目 (つまり、Windows フォーム ユーザー コントロール)。  
  
6.  Windows フォーム ユーザー コントロールのデザイナーを開きます。  
  
7.  *ProjectName* **WPF ユーザー コントロール**のタブ、**ツールボックス**、WPF ユーザー コントロールをデザイナーにドラッグします。  
  
     Windows フォーム ユーザー コントロール内の WPF ユーザー コントロールをホストする <xref:System.Windows.Forms.Integration.ElementHost> オブジェクトが自動的に作成されます。  
  
8.  Windows フォーム ユーザー コントロールを文書またはブックにプログラムで追加するコードを作成します。 詳細については、「 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
    > [!NOTE]  
    >  Windows フォーム ユーザー コントロールをデザイナー上の文書またはワークシートにドラッグすることはできません。  
  
9. プロジェクトをリビルドします。  
  
## <a name="hosting-wpf-controls-by-using-the-elementhost-class"></a>ElementHost クラスによる WPF コントロールのホスト  
 Visual Studio には Office ソリューションで Windows フォーム コントロールを使用できるようにする機能がありますが、WPF コントロールを対象とする同様の機能はありません。 たとえば、する Windows フォーム コントロールを追加できます文書とワークシート デザイン時からコントロールをドラッグして、**ツールボックス**、またはヘルパー メソッドを使用して、実行時にします。 それに対し、これらの機能は WPF コントロールには使用できません。  
  
 WPF コントロールでは、Windows フォーム コントロールまたはフォームと WPF コントロールとの間の統合レイヤーとして <xref:System.Windows.Forms.Integration.ElementHost> クラスを使用します。 デザイン時に WPF コントロールをソリューションに追加すると、<xref:System.Windows.Forms.Integration.ElementHost> オブジェクトが自動的に作成されます。  
  
## <a name="wpf-resources"></a>WPF リソース  
 Windows フォーム コントロールおよびフォーム上での WPF のホストに関連するアーキテクチャおよびデザイン上の問題の詳細については、以下のトピックを参照してください。  
  
-   [Windows フォームと WPF の相互運用性入力アーキテクチャ](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)  
  
-   [Windows フォームと WPF プロパティの割り当て](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)  
  
-   [WPF と Windows フォームの相互運用性](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)  
  
-   [Windows フォーム コントロールおよび同等の WPF コントロール](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)  
  
 Visual Studio でデザイン時に WPF コントロールを Windows フォーム コントロールおよびフォームに追加する方法の詳細については、以下のトピックを参照してください。  
  
-   [チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)  
  
-   [チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの配置](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)  
  
-   [チュートリアル: WPF コンテンツへのスタイルの適用](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)  
  
## <a name="see-also"></a>関連項目  
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Windows フォームでコントロールの Office ドキュメントの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [カスタム作業ウィンドウ](../vsto/custom-task-panes.md)   
 [Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)   
 [方法: Word 文書や Excel ブックに操作ウィンドウを追加](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [方法: Word 文書や Excel ブックに操作ウィンドウを追加](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [方法: カスタム作業ウィンドウをアプリケーションに追加します。](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [方法: フォーム領域を Outlook アドイン プロジェクトに追加する](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  