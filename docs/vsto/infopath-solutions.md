---
title: InfoPath ソリューション
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 078bbbf448b1a940461f2859601944627b7c2394
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671844"
---
# <a name="infopath-solutions"></a>InfoPath ソリューション
  Visual Studio には、Microsoft Office InfoPath 2013 および InfoPath 2010 の VSTO アドインの作成に使用できるプロジェクト テンプレートが用意されています。 InfoPath は、Office 2016 では使用できません。  
  
> [!NOTE]  
>  引き続き作成できます VSTO アドインを InfoPath の Office 2016 をインストールした場合でもです。 InfoPath 2013 または Office 2013 を Office 2016 とサイドバイサイドにインストールするだけです。  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
> [!NOTE]  
>  [複数のプラットフォーム](https://dev.office.com/add-in-availability)にまたがる Office を拡張するソリューション開発に関心がありますか？ 新しい [Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)をチェックして下さい。 Office アドインは、小さなフット プリントが VSTO アドインとソリューションの比較を持ち、ほぼすべての web テクノロジ、HTML5、JavaScript、CSS3、XML などのプログラミングを使用して、それらをビルドすることができます。  
  
 InfoPath 用の VSTO アドインは、他の Microsoft Office アプリケーションの VSTO アドインと似ています。 このようなソリューションは、アプリケーションが読み込むアセンブリで構成されます。 エンド ユーザーは、どのフォームまたはフォーム テンプレートが開いているかに関係なく、このアセンブリの機能にアクセスできます。 VSTO アドインの詳細については、次を参照してください。 [VSTO アドインのプログラミングを始める](../vsto/getting-started-programming-vsto-add-ins.md)と[Architecture of VSTO アドイン](../vsto/architecture-of-vsto-add-ins.md)します。  
  
> [!NOTE]  
>  Visual Studio 2015 には、以前のバージョンの Visual Studio で提供されていた InfoPath フォーム テンプレート プロジェクトは含まれていません。 また、Visual Studio 2015 を使用して、以前のバージョンの Visual Studio で作成した InfoPath フォーム テンプレート プロジェクトを開いて編集することもできません。 ただし、Visual Studio Tools for Applications を使用すると、InfoPath フォーム テンプレート プロジェクトを開いて編集できます。 詳細については、次を参照してください。 [InfoPath 2010 の VSTO 2008 プロジェクトを操作します。](http://go.microsoft.com/fwlink/?LinkID=218903)します。  
  
## <a name="automate-infopath-by-using-an-add-in"></a>アドインを使用して、InfoPath を自動化します。  
 Visual Studio の Office 開発ツールを使用して作成した Office VSTO アドインから InfoPath オブジェクト モデルにアクセスするには、プロジェクトの `Application` クラスの `ThisAddIn` フィールドを使用します。 `Application` フィールドは InfoPath の現在のインスタンスを表す <xref:Microsoft.Office.Interop.InfoPath.Application> オブジェクトを返します。 詳細については、次を参照してください。[プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)します。  
  
 ときに、VSTO アドインから InfoPath オブジェクト モデルを呼び出すことは、InfoPath のプライマリ相互運用機能アセンブリに用意されている型を使用します。 プライマリ相互運用機能アセンブリは、VSTO アドインのマネージド コードと InfoPath の COM オブジェクト モデルとの仲介役を果たします。 InfoPath プライマリ相互運用機能アセンブリ内の型は、すべて <xref:Microsoft.Office.Interop.InfoPath> 名前空間に定義されています。 InfoPath プライマリ相互運用機能アセンブリの詳細については、次を参照してください。 [Microsoft Office InfoPath のプライマリ相互運用機能アセンブリ](http://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72)します。 プライマリ相互運用機能アセンブリの詳細については一般に、表示[Office ソリューション開発の概要&#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md)と[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)します。  
  
## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>アドインを使用して、InfoPath のユーザー インターフェイスをカスタマイズします。  
 InfoPath の VSTO アドインを作成するときに、いくつかの異なる UI カスタマイズ オプションがあります。 次の表は、主なカスタマイズ方法を示しています。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|カスタム作業ウィンドウを作成する。|[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)|  
|InfoPath のリボンにカスタム タブを追加する。|[InfoPath のリボンをカスタマイズします。](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 UI の InfoPath およびその他の Microsoft Office アプリケーションをカスタマイズする方法の詳細については、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Microsoft Office InfoPath プライマリ相互運用機能アセンブリについて](http://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [VSTO アドインのプログラミングを始める](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO アドインをプログラミングします。](../vsto/programming-vsto-add-ins.md)   
 [Office ソリューションでコードを記述します。](../vsto/writing-code-in-office-solutions.md)   
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Office 開発における InfoPath 2010](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  