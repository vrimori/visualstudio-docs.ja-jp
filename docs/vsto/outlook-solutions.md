---
title: "Outlook ソリューション |Microsoft ドキュメント"
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
helpviewer_keywords:
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
ms.assetid: 2ae3cd9c-bf31-4efa-8b18-b6b1c34a8d93
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3692e6b224297175d8466a993b0dc16cc7827294
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="outlook-solutions"></a>Outlook ソリューション
  Visual Studio には、Microsoft Office Outlook の VSTO アドインを作成するために使用できるプロジェクト テンプレートが用意されています。 VSTO アドインを使用して、Outlook の自動化、Outlook の機能の拡張、または Outlook のユーザー インターフェイス (UI) のカスタマイズが可能です。 VSTO アドインについて詳しくは、「 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)」をご覧ください。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
## <a name="creating-an-outlook-vsto-add-in-project"></a>Outlook VSTO アドイン プロジェクトの作成  
 Outlook プロジェクトを作成するには、 **[新しいプロジェクト]** ダイアログ ボックスにある **[Outlook アドイン]** プロジェクト テンプレートを使用します。 このテンプレートには必要なアセンブリ参照とプロジェクト ファイルが含まれています。  
  
 VSTO アドイン プロジェクトを作成する方法の詳細については、次を参照してください。[する方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)です。 プロジェクト テンプレートの詳細については、次を参照してください。 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)です。  
  
## <a name="outlook-vsto-add-in-programming-model"></a>Outlook VSTO アドインのプログラミング モデル  
 Outlook VSTO アドイン プロジェクトを作成すると、 `ThisAddIn`と呼ばれる、ソリューションの基礎となるクラスが Visual Studio によって生成されます。 このクラスは、コードを記述する際の開始点となり、Outlook のオブジェクト モデルを VSTO アドインに公開します。  
  
 詳細については、`ThisAddIn`クラスと、VSTO アドインで使用できるその他の機能を参照してください[VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)です。  
  
## <a name="automating-outlook-by-using-the-outlook-object-model"></a>Outlook オブジェクト モデルを使用した Outlook の自動化  
 Outlook オブジェクト モデルでは、Outlook の自動化に使用できる型が多数公開されています。 それらの型によって、次のような一般的なタスクを実行するコードを作成できます。  
  
-   プログラムで電子メール メッセージを作成し、送信する。  
  
-   新しい会議出席依頼を送信する。  
  
-   Outlook フォルダー内のアイテムを検索する。  
  
 詳細については、「 [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)」を参照してください。  
  
## <a name="customizing-the-user-interface-of-an-outlook-application"></a>Outlook アプリケーションのユーザー インターフェイスのカスタマイズ  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|Outlook インスペクターのリボンにカスタム タブを追加する。|[リボンの概要](../vsto/ribbon-overview.md)|  
|Outlook インスペクターの組み込みタブにカスタム グループを追加する。|[方法: 組み込みタブをカスタマイズする](../vsto/how-to-customize-a-built-in-tab.md)|  
|Outlook インスペクターに表示されるカスタム作業ウィンドウを追加する。|[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)します。|  
|既存の Outlook フォームを拡張または置換するフォーム領域を追加する。|[Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)|  
  
 Outlook の UI およびその他の Microsoft Office アプリケーションのカスタマイズの詳細については、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)です。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)|Outlook オブジェクト モデルによって提供されるオブジェクトの概要を説明します。|  
|[Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)|フォーム領域のデザイン、開発、およびデバッグを簡単に実行できる、Visual Studio によって提供されるツールについて説明します。|  
|[チュートリアル: 初めての Outlook 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Microsoft Office Outlook 用の VSTO アドインを作成する方法について説明します。|  
|[Office 開発における Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=199013)|この MSDN ライブラリの領域では、Outlook ソリューションの開発に関する記事やリファレンス ドキュメントを参照できます (Visual Studio を使用した Office 開発以外のトピックも含まれています)。|  
  
  