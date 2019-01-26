---
title: Outlook ソリューション
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5537b07263cbdf48da9a0ce2e5705b8bd71941e9
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870014"
---
# <a name="outlook-solutions"></a>Outlook ソリューション
  Visual Studio には、Microsoft Office Outlook の VSTO アドインを作成するために使用できるプロジェクト テンプレートが用意されています。 VSTO アドインを使用して、Outlook の自動化、Outlook の機能の拡張、または Outlook のユーザー インターフェイス (UI) のカスタマイズが可能です。 VSTO アドインについて詳しくは、「 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)」をご覧ください。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  [複数のプラットフォーム](https://dev.office.com/add-in-availability)にまたがる Office を拡張するソリューション開発に関心がありますか？ 新しい [Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)をチェックして下さい。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、HTML5、JavaScript、CSS3、XML などのほぼすべての web プログラミング テクノロジを使用して、ビルドすることができます。  
  
## <a name="create-an-outlook-vsto-add-in-project"></a>Outlook VSTO アドイン プロジェクトを作成します。  
 Outlook プロジェクトを作成するには、 **[新しいプロジェクト]** ダイアログ ボックスにある **[Outlook アドイン]** プロジェクト テンプレートを使用します。 このテンプレートには必要なアセンブリ参照とプロジェクト ファイルが含まれています。  
  
 VSTO アドイン プロジェクトを作成する方法の詳細については、次を参照してください。[方法。Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。 プロジェクト テンプレートの詳細については、次を参照してください。 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)します。  
  
## <a name="outlook-vsto-add-in-programming-model"></a>Outlook VSTO アドインのプログラミング モデル  
 Outlook VSTO アドイン プロジェクトを作成すると、 `ThisAddIn`と呼ばれる、ソリューションの基礎となるクラスが Visual Studio によって生成されます。 このクラスは、コードを記述する際の開始点となり、Outlook のオブジェクト モデルを VSTO アドインに公開します。  
  
 詳細については、`ThisAddIn`クラスと、VSTO アドインで使用できるその他の機能を参照してください[プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)します。  
  
## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Outlook オブジェクト モデルを使用して Outlook を自動化します。  
 Outlook オブジェクト モデルでは、Outlook の自動化に使用できる型が多数公開されています。 それらの型によって、次のような一般的なタスクを実行するコードを作成できます。  
  
- プログラムで電子メール メッセージを作成し、送信する。  
  
- 新しい会議出席依頼を送信する。  
  
- Outlook フォルダー内のアイテムを検索する。  
  
  詳細については、次を参照してください。 [Outlook オブジェクト モデルの概要](../vsto/outlook-object-model-overview.md)します。  
  
## <a name="customize-the-user-interface-of-an-outlook-application"></a>Outlook アプリケーションのユーザー インターフェイスをカスタマイズします。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|Outlook インスペクターのリボンにカスタム タブを追加する。|[リボンの概要](../vsto/ribbon-overview.md)|  
|Outlook インスペクターの組み込みタブにカスタム グループを追加する。|[方法: 組み込みタブをカスタマイズします。](../vsto/how-to-customize-a-built-in-tab.md)|  
|Outlook インスペクターに表示されるカスタム作業ウィンドウを追加する。|[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)します。|  
|既存の Outlook フォームを拡張または置換するフォーム領域を追加する。|[Outlook フォーム領域を作成します。](../vsto/creating-outlook-form-regions.md)|  
  
 Outlook の UI およびその他の Microsoft Office アプリケーションをカスタマイズする方法の詳細については、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)します。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[Outlook オブジェクト モデルの概要](../vsto/outlook-object-model-overview.md)|Outlook オブジェクト モデルによって提供されるオブジェクトの概要を説明します。|  
|[Outlook フォーム領域を作成します。](../vsto/creating-outlook-form-regions.md)|フォーム領域のデザイン、開発、およびデバッグを簡単に実行できる、Visual Studio によって提供されるツールについて説明します。|  
|[チュートリアル: 初めて VSTO アドイン Outlook の作成します。](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Microsoft Office Outlook 用の VSTO アドインを作成する方法について説明します。|  
|[Office 開発における outlook 2010](http://go.microsoft.com/fwlink/?LinkId=199013)|この MSDN ライブラリの領域では、Outlook ソリューションの開発に関する記事やリファレンス ドキュメントを参照できます (Visual Studio を使用した Office 開発以外のトピックも含まれています)。|  
