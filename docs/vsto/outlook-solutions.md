---
title: "Outlook ソリューション | Microsoft Docs"
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
  - "ソリューション [Visual Studio での Office 開発]、Outlook"
  - "Office プロジェクト [Visual Studio での Office 開発]、Outlook"
  - "Office ソリューション [Visual Studio での Office 開発]、Outlook"
  - "テンプレート [Visual Studio での Office 開発]、Outlook"
  - "プロジェクト [Visual Studio での Office 開発]、Outlook"
  - "Outlook [Visual Studio での Office 開発]"
  - "メール [Visual Studio での Office 開発]、Outlook ソリューション"
ms.assetid: 2ae3cd9c-bf31-4efa-8b18-b6b1c34a8d93
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Outlook ソリューション
  Visual Studio には、Microsoft Office Outlook の VSTO アドインを作成するために使用できるプロジェクト テンプレートが用意されています。 VSTO アドインを使用して、Outlook の自動化、Outlook の機能の拡張、または Outlook のユーザー インターフェイス \(UI\) のカスタマイズが可能です。 VSTO アドインについて詳しくは、「[VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)」をご覧ください。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Outlook VSTO アドイン プロジェクトの作成  
 Outlook プロジェクトを作成するには、**\[新しいプロジェクト\]** ダイアログ ボックスにある **\[Outlook アドイン\]** プロジェクト テンプレートを使用します。 このテンプレートには必要なアセンブリ参照とプロジェクト ファイルが含まれています。  
  
 VSTO アドイン プロジェクトを作成する方法について詳しくは、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」をご覧ください。 プロジェクト テンプレートについて詳しくは、「[Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)」をご覧ください。  
  
## Outlook VSTO アドインのプログラミング モデル  
 Outlook VSTO アドイン プロジェクトを作成すると、`ThisAddIn` と呼ばれる、ソリューションの基礎となるクラスが Visual Studio によって生成されます。 このクラスは、コードを記述する際の開始点となり、Outlook のオブジェクト モデルを VSTO アドインに公開します。  
  
 `ThisAddIn` クラスおよび VSTO アドインで使用できる他の機能について詳しくは、「[VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)」をご覧ください。  
  
## Outlook オブジェクト モデルを使用した Outlook の自動化  
 Outlook オブジェクト モデルでは、Outlook の自動化に使用できる型が多数公開されています。 それらの型によって、次のような一般的なタスクを実行するコードを作成できます。  
  
-   プログラムで電子メール メッセージを作成し、送信する。  
  
-   新しい会議出席依頼を送信する。  
  
-   Outlook フォルダー内のアイテムを検索する。  
  
 詳細については、「[Outlook オブジェクト モデルの概要](../vsto/outlook-object-model-overview.md)」を参照してください。  
  
## Outlook アプリケーションのユーザー インターフェイスのカスタマイズ  
  
|タスク|詳細情報|  
|---------|----------|  
|Outlook インスペクターのリボンにカスタム タブを追加する。|[リボンの概要](../vsto/ribbon-overview.md)|  
|Outlook インスペクターの組み込みタブにカスタム グループを追加する。|[方法 : 組み込みタブをカスタマイズする](../vsto/how-to-customize-a-built-in-tab.md)|  
|Outlook インスペクターに表示されるカスタム作業ウィンドウを追加する。|[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)。|  
|既存の Outlook フォームを拡張または置換するフォーム領域を追加する。|[Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)|  
  
 Outlook およびその他の Microsoft Office アプリケーションの UI をカスタマイズする方法について詳しくは、「[Office UI のカスタマイズ](../vsto/office-ui-customization.md)」をご覧ください。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[Outlook オブジェクト モデルの概要](../vsto/outlook-object-model-overview.md)|Outlook オブジェクト モデルによって提供されるオブジェクトの概要を説明します。|  
|[Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)|フォーム領域のデザイン、開発、およびデバッグを簡単に実行できる、Visual Studio によって提供されるツールについて説明します。|  
|[チュートリアル : 初めての Outlook 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Microsoft Office Outlook 用の VSTO アドインを作成する方法について説明します。|  
|[Office 開発における Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=199013)|この MSDN ライブラリの領域では、Outlook ソリューションの開発に関する記事やリファレンス ドキュメントを参照できます \(Visual Studio を使用した Office 開発以外のトピックも含まれています\)。|  
  
  