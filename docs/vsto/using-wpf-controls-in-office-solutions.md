---
title: "Office ソリューションでの WPF コントロールの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "WPF [Visual Studio での Office 開発]"
ms.assetid: 305a212b-0a95-40ad-87aa-22896fe80a04
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Office ソリューションでの WPF コントロールの使用
  Visual Studio の Office 開発ツールを使用して作成されたソリューションは、Windows フォーム コントロールを使用して直接操作することを前提としていますが、ソリューションで WPF コントロールを使用することもできます。  Windows Presentation Foundation \(WPF\) は、ユーザー インターフェイスをデザインするときに Windows フォームの代わりとして使用できます。  WPF では、UI、メディア、および文書を取り込むための新しい手法として、Extensible Application Markup Language \(XAML\) というマークアップ言語を使用します。  詳細については、「[Visual Studio 2015 での WPF の概要](../Topic/Introduction%20to%20WPF%20in%20Visual%20Studio%202015.md)」を参照してください。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Office ソリューションの Windows フォーム コントロールをホストする UI 要素は、WPF コントロールもホストできます。  そうした UI 要素には次のようなものがあります。  
  
-   ドキュメント レベルのカスタマイズに含まれる文書およびワークシート  
  
-   ドキュメント レベルのカスタマイズに含まれる操作ウィンドウ  
  
-   VSTO アドインにおけるカスタム作業ウィンドウ  
  
-   Outlook 用 VSTO アドインのフォーム領域  
  
## デザイン時における Office プロジェクトへの WPF コントロールの追加  
 Office ソリューションの UI 要素に WPF コントロールを直接追加することはできません。  直接追加する代わりに、**ユーザー コントロール \(WPF\)** アイテムをプロジェクトに追加し、それを WPF コントロールのデザイン画面として使用します。  次に、WPF ユーザー コントロールをプロジェクトの UI 要素に追加します。  
  
#### 操作ウィンドウ、カスタム作業ウィンドウ、またはフォーム領域に WPF コントロールを追加するには  
  
1.  カスタム作業ウィンドウ、操作ウィンドウ、またはフォーム領域を追加するプロジェクトを開きます。  
  
2.  プロジェクトに**ユーザー コントロール \(WPF\)** アイテムを追加します。  
  
3.  **\[ツールボックス\]** から WPF ユーザー コントロールのデザイン画面に WPF コントロールを追加します。  
  
     既定では、WPF ユーザー コントロール デザイナーを開くと、**\[ツールボックス\]** には WPF コントロールだけが含まれています。  
  
4.  プロジェクトをビルドします。  
  
5.  操作ウィンドウ、フォーム領域、またはカスタム作業ウィンドウをプロジェクトに追加します。  
  
    -   フォーム領域の場合は、プロジェクトに **Outlook フォーム領域**アイテムを追加します。  詳細については、「[方法 : フォーム領域を Outlook アドイン プロジェクトに追加する](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)」を参照してください。  
  
    -   操作ウィンドウの場合は、プロジェクトに**操作ウィンドウ コントロール** アイテムまたは**ユーザー コントロール** アイテムを追加します。  詳細については、「[方法: Word 文書または Excel ブックに操作ウィンドウを追加する](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)」と「[方法: Word 文書または Excel ブックに操作ウィンドウを追加する](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)」を参照してください。  
  
    -   カスタム作業ウィンドウの場合は、プロジェクトに**ユーザー コントロール** アイテムを追加します。  詳細については、「[方法 : カスタム作業ウィンドウをアプリケーションに追加する](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)」を参照してください。  
  
6.  **\[ツールボックス\]** の \[*プロジェクト名* **WPF ユーザー コントロール\]** タブから、操作ウィンドウ、フォーム領域、またはカスタム作業ウィンドウのデザイナーに、WPF ユーザー コントロールをドラッグします。  
  
     UI 要素内の WPF ユーザー コントロールをホストする <xref:System.Windows.Forms.Integration.ElementHost> オブジェクトが自動的に作成されます。  
  
7.  プロジェクトをリビルドします。  
  
#### ドキュメント レベルのプロジェクト内の文書またはワークシートに WPF コントロールを追加するには  
  
1.  Word または Excel のドキュメント レベルのプロジェクトを開きます。  
  
2.  プロジェクトに**ユーザー コントロール \(WPF\)** アイテムを追加します。  
  
3.  **\[ツールボックス\]** から WPF ユーザー コントロールのデザイン画面に WPF コントロールを追加します。  
  
4.  プロジェクトをビルドします。  
  
5.  **ユーザー コントロール** アイテム \(Windows フォーム ユーザー コントロール\) をプロジェクトに追加します。  
  
6.  Windows フォーム ユーザー コントロールのデザイナーを開きます。  
  
7.  **\[ツールボックス\]** の \[*プロジェクト名* **WPF ユーザー コントロール\]** タブからデザイナーに WPF ユーザー コントロールをドラッグします。  
  
     Windows フォーム ユーザー コントロール内の WPF ユーザー コントロールをホストする <xref:System.Windows.Forms.Integration.ElementHost> オブジェクトが自動的に作成されます。  
  
8.  Windows フォーム ユーザー コントロールを文書またはブックにプログラムで追加するコードを作成します。  詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
    > [!NOTE]  
    >  Windows フォーム ユーザー コントロールをデザイナー上の文書またはワークシートにドラッグすることはできません。  
  
9. プロジェクトをリビルドします。  
  
## ElementHost クラスによる WPF コントロールのホスト  
 Visual Studio には Office ソリューションで Windows フォーム コントロールを使用できるようにする機能がありますが、WPF コントロールを対象とする同様の機能はありません。  たとえば、Windows フォーム コントロールは、デザイン時には **\[ツールボックス\]** からのドラッグによって、また実行時にはヘルパー メソッドを使用して、文書やワークシートに追加できます。  それに対し、これらの機能は WPF コントロールには使用できません。  
  
 WPF コントロールでは、Windows フォーム コントロールまたはフォームと WPF コントロールとの間の統合レイヤーとして <xref:System.Windows.Forms.Integration.ElementHost> クラスを使用します。  デザイン時に WPF コントロールをソリューションに追加すると、<xref:System.Windows.Forms.Integration.ElementHost> オブジェクトが自動的に作成されます。  
  
## WPF リソース  
 Windows フォーム コントロールおよびフォーム上での WPF のホストに関連するアーキテクチャおよびデザイン上の問題の詳細については、以下のトピックを参照してください。  
  
-   [Windows フォームと WPF の相互運用性入力アーキテクチャ](../Topic/Windows%20Forms%20and%20WPF%20Interoperability%20Input%20Architecture.md)  
  
-   [Windows フォームと WPF プロパティの割り当て](../Topic/Windows%20Forms%20and%20WPF%20Property%20Mapping.md)  
  
-   [WPF と Windows フォームの相互運用性](../Topic/WPF%20and%20Windows%20Forms%20Interoperation.md)  
  
-   [Windows フォーム コントロールおよび同等の WPF コントロール](../Topic/Windows%20Forms%20Controls%20and%20Equivalent%20WPF%20Controls.md)  
  
 Visual Studio でデザイン時に WPF コントロールを Windows フォーム コントロールおよびフォームに追加する方法の詳細については、以下のトピックを参照してください。  
  
-   [チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成](../Topic/Walkthrough:%20Creating%20New%20WPF%20Content%20on%20Windows%20Forms%20at%20Design%20Time.md)  
  
-   [チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの配置](../Topic/Walkthrough:%20Arranging%20WPF%20Content%20on%20Windows%20Forms%20at%20Design%20Time.md)  
  
-   [チュートリアル: WPF コンテンツへのスタイルの適用](../Topic/Walkthrough:%20Styling%20WPF%20Content.md)  
  
## 参照  
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Office ドキュメントでの Windows フォーム コントロールの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [カスタム作業ウィンドウ](../vsto/custom-task-panes.md)   
 [Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)   
 [方法: Word 文書または Excel ブックに操作ウィンドウを追加する](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [方法: Word 文書または Excel ブックに操作ウィンドウを追加する](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [方法 : カスタム作業ウィンドウをアプリケーションに追加する](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [方法 : フォーム領域を Outlook アドイン プロジェクトに追加する](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  