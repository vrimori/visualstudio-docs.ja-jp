---
title: "InfoPath ソリューション |Microsoft ドキュメント"
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
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
ms.assetid: 20ac6bee-b17f-4217-9f78-11304a11236a
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5c5dbcc0a83d94864858da04bdfe46e5b9ae39e3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="infopath-solutions"></a>InfoPath ソリューション
  Visual Studio には、Microsoft Office InfoPath 2013 および InfoPath 2010 の VSTO アドインの作成に使用できるプロジェクト テンプレートが用意されています。 InfoPath は、Office 2016 では使用できません。  
  
> [!NOTE]  
>  作成できます VSTO アドインで InfoPath の Office 2016 をインストールしている場合でもです。 InfoPath 2013 または Office 2013 を Office 2016 とサイドバイサイドにインストールするだけです。  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
 InfoPath 用の VSTO アドインは、他の Microsoft Office アプリケーションの VSTO アドインと似ています。 このようなソリューションは、アプリケーションが読み込むアセンブリで構成されます。 エンド ユーザーは、どのフォームまたはフォーム テンプレートが開いているかに関係なく、このアセンブリの機能にアクセスできます。 VSTO アドインについて詳しくは、「 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) 」および「 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)」をご覧ください。  
  
> [!NOTE]  
>  Visual Studio 2015 には、以前のバージョンの Visual Studio で提供されていた InfoPath フォーム テンプレート プロジェクトは含まれていません。 また、Visual Studio 2015 を使用して、以前のバージョンの Visual Studio で作成した InfoPath フォーム テンプレート プロジェクトを開いて編集することもできません。 ただし、Visual Studio Tools for Applications を使用すると、InfoPath フォーム テンプレート プロジェクトを開いて編集できます。 詳しくは、「 [InfoPath 2010 での VSTO 2008 プロジェクトの使用](http://go.microsoft.com/fwlink/?LinkID=218903)」をご覧ください。  
  
## <a name="automating-infopath-by-using-an-add-in"></a>アドイン使用による InfoPath の自動化  
 Visual Studio の Office 開発ツールを使用して作成した Office VSTO アドインから InfoPath オブジェクト モデルにアクセスするには、プロジェクトの `Application` クラスの `ThisAddIn` フィールドを使用します。 `Application` フィールドは InfoPath の現在のインスタンスを表す <xref:Microsoft.Office.Interop.InfoPath.Application> オブジェクトを返します。 詳細については、「 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)」を参照してください。  
  
 VSTO アドインから InfoPath オブジェクト モデルを呼び出すときには、InfoPath のプライマリ相互運用機能アセンブリに用意された型を使用します。 プライマリ相互運用機能アセンブリは、VSTO アドインのマネージ コードと InfoPath の COM オブジェクト モデルとの仲介役を果たします。 InfoPath プライマリ相互運用機能アセンブリ内の型は、すべて <xref:Microsoft.Office.Interop.InfoPath> 名前空間に定義されています。 InfoPath プライマリ相互運用機能アセンブリの詳細については、「 [Microsoft Office InfoPath プライマリ相互運用機能アセンブリについて](http://msdn.microsoft.com/en-us/1b3ae03c-6951-49e4-a489-4712d3f7ba72)」を参照してください。 プライマリ相互運用機能アセンブリの詳細については一般を参照してください[Office ソリューション開発の概要 &#40;です。VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)と[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)です。  
  
## <a name="customizing-the-user-interface-of-infopath-by-using-an-add-in"></a>アドインによる InfoPath のユーザー インターフェイスのカスタマイズ  
 InfoPath の VSTO アドインを作成するときには、さまざまな方法で UI をカスタマイズできます。 次の表は、主なカスタマイズ方法を示しています。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|カスタム作業ウィンドウを作成する。|[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)|  
|InfoPath のリボンにカスタム タブを追加する。|[InfoPath のリボンのカスタマイズ](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 InfoPath の UI およびその他の Microsoft Office アプリケーションのカスタマイズの詳細については、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Microsoft Office InfoPath プライマリ相互運用機能アセンブリについて](http://msdn.microsoft.com/en-us/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office ソリューション開発の概要 &#40;です。VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)   
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Office 開発における InfoPath 2010](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  