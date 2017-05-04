---
title: "Office アプリケーションおよびプロジェクト タイプ別の使用可能な機能 | Microsoft Docs"
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
  - "アドイン [Visual Studio での Office 開発]"
  - "アプリケーション レベルのアドイン [Visual Studio での Office 開発]"
  - "ドキュメント レベルのカスタマイズ [Visual Studio での Office 開発]"
  - "フォーム領域 [Visual Studio での Office 開発], 使用できる機能"
  - "Office アプリケーション [Visual Studio での Office 開発], 使用できる機能"
  - "Visual Studio での Office 開発, 機能"
  - "Office プロジェクト [Visual Studio での Office 開発], 使用できる機能"
  - "リボン [Visual Studio での Office 開発]"
ms.assetid: 3e9aa4d3-affb-4f76-bc67-49fe5f26a6a1
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Office アプリケーションおよびプロジェクト タイプ別の使用可能な機能
  Visual Studio には、次のように、Microsoft Office アプリケーションのさまざまなビジネス シナリオをサポートするプロジェクト テンプレートがいくつか用意されています。  
  
-   ドキュメントレベルのカスタマイズ。  
  
-   VSTO アドイン。  
  
 すべてのプロジェクトの種類を使用できないアプリケーションもあります。  たとえば、ドキュメントレベルのプロジェクトは、Microsoft Office Word と Microsoft Office Excel でのみ使用できます。  同様に、一部の機能は、特定の種類のプロジェクトまたはアプリケーションでのみ使用できます。  たとえば、操作ウィンドウは、ドキュメントレベルのプロジェクトでのみ使用できます。また、リボンの拡張機能は、一部のアプリケーションでのみ使用できます。  さまざまな種類のプロジェクトの詳細については、「[Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)」を参照してください。  
  
> [!NOTE]  
>  Office プロジェクト テンプレートは、一部のエディションの [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] でのみ使用できます。  詳細については、「[Office ソリューションを開発できるようにコンピューターを構成する](../vsto/configuring-a-computer-to-develop-office-solutions.md)」を参照してください。  
  
## 各 Microsoft Office アプリケーションで使用できるプロジェクトの種類  
 プロジェクトの種類ごとに使用できるアプリケーションを次の表に示します。  
  
|プロジェクトの種類|Microsoft Office アプリケーション|  
|---------------|-------------------------------|  
|ドキュメント レベルのカスタマイズ|Excel<br /><br /> Word|  
|VSTO アドイン|Excel<br /><br /> InfoPath \(InfoPath 2013 と InfoPath 2010 のみ\)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> プロジェクト<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|  
  
## 各プロジェクトで使用できる機能  
 プロジェクトの種類ごとに異なる機能を次の表に示します。  
  
|特性|機能を提供するプロジェクトの種類|関連項目|  
|--------|----------------------|----------|  
|\[操作\] ウィンドウ。|ドキュメントレベルのプロジェクト。|[操作ウィンドウの概要](../vsto/actions-pane-overview.md)|  
|ClickOnce 配置。|VS およびドキュメントレベルのプロジェクト。|[Office ソリューションの配置](../vsto/deploying-an-office-solution.md)|  
|カスタム作業ウィンドウ。|次のアプリケーション用の VSTO アドイン プロジェクト:<br /><br /> -   Excel<br />-   InfoPath \(InfoPath 2013 と InfoPath 2010 のみ\)<br />-   Outlook<br />-   PowerPoint<br />-   Word|[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)|  
|カスタム XML 部分。|ドキュメントレベルのプロジェクト。<br /><br /> 次のアプリケーション用のアプリケーション レベルのプロジェクト:<br /><br /> -   Excel<br />-   PowerPoint<br />-   Word|[カスタム XML 部分の概要](../vsto/custom-xml-parts-overview.md)|  
|データ キャッシュ。|ドキュメントレベルのプロジェクト。|[ドキュメント レベルのカスタマイズのキャッシュ データ](../vsto/cached-data-in-document-level-customizations.md)|  
|VSTO アドインのオブジェクトを他の Microsoft Office ソリューションに公開します。|VSTO アドイン プロジェクト。|[その他の Office ソリューションから VSTO アドインのコードを呼び出す](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|  
|次のホスト コントロール:<br /><br /> -   グラフ<br />-   ListObject<br />-   NamedRange<br />-   コンテンツ コントロール<br />-   ブックマーク|ドキュメントレベルのプロジェクト。<br /><br /> Word と Excel 用の VSTO アドイン プロジェクト。|[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)|  
|次のホスト コントロール:<br /><br /> -   XMLMappedRange<br />-   XMLNode<br />-   XMLNodes|ドキュメントレベルのプロジェクト。|[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)|  
|複数プロジェクトの配置。|ドキュメントレベルのプロジェクト。<br /><br /> VSTO アドイン プロジェクト。|[チュートリアル: 複数の Office ソリューションを単一の ClickOnce インストーラーで配置する](http://msdn.microsoft.com/ja-jp/051223c0-4082-4799-b78b-a4763a9def55)|  
|Outlook フォーム領域。|Outlook 用の VSTO アドイン プロジェクト。|[Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)|  
|配置後の動作。|ドキュメントレベルのプロジェクト。<br /><br /> VSTO アドイン プロジェクト。|[チュートリアル: ClickOnce によるインストール後にドキュメントをエンド ユーザーのコンピューターにコピーする](http://msdn.microsoft.com/ja-jp/100090f7-bc63-4152-b3e1-19b48bc27466)|  
|リボンのカスタマイズ。|ドキュメントレベルのプロジェクト。<br /><br /> 次のアプリケーション用の VSTO アドイン プロジェクト:<br /><br /> -   Excel<br />-   InfoPath \(InfoPath 2013 と InfoPath 2010 のみ\)<br />-   Outlook<br />-   PowerPoint<br />-   プロジェクト<br />-   Visio<br />-   Word|[リボンの概要](../vsto/ribbon-overview.md)|  
|視覚的なドキュメント デザイナー。|ドキュメントレベルのプロジェクト。|[Visual Studio 環境における Office プロジェクト](../vsto/office-projects-in-the-visual-studio-environment.md)|  
  
## 参照  
 [はじめに &#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [リボンの概要](../vsto/ribbon-overview.md)   
 [Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ドキュメント レベルのカスタマイズのキャッシュ データ](../vsto/cached-data-in-document-level-customizations.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)  
  
  