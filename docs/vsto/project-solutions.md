---
title: "プロジェクトのソリューション |Microsoft ドキュメント"
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
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 39ee63d84ef0c7830da9c218a6e4c7b25f7bac99
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="project-solutions"></a>Project ソリューション
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] には、Microsoft Office Project の VSTO アドインを作成するために使用できるプロジェクト テンプレートが用意されています。 VSTO アドインを使用すると、Project の自動化、Project 機能の拡張、Project ユーザー インターフェイス (UI) のカスタマイズが可能です。  
  
 VSTO アドインの詳細については、「 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) 」および「 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)」を参照してください。Microsoft Office でのプログラミングに慣れていない場合は、次を参照してください。[作業の開始 (&) #40 です。 Visual Studio &#41; での Office 開発](../vsto/getting-started-office-development-in-visual-studio.md)です。  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
## <a name="automating-project-by-using-the-project-object-model"></a>Project オブジェクト モデルによる Project の自動化  
 Project オブジェクト モデルでは、Project の自動化に使用できる型が多数公開されています。 これらの型により、プロジェクト内のタスクをプログラムによって作成したり変更したりするなど、一般的なタスクを行うコードを記述できます。  
  
 VSTO アドインから Project オブジェクト モデルにアクセスするには、プロジェクト内の `Application` クラスの `ThisAddIn` フィールドを使用します。 `Application`フィールドは、プロジェクトの現在のインスタンスを表す Microsoft.Office.Interop.MsProject.Application オブジェクトを返します。 詳細については、「 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。  
  
 Project オブジェクト モデルを呼び出すときには、Project のプライマリ相互運用機能アセンブリに用意された型を使用します。 プライマリ相互運用機能アセンブリは、VSTO アドインのマネージ コードと Project の COM オブジェクト モデルとの仲介役を果たします。 Project プライマリ相互運用機能アセンブリのすべての型は、Microsoft.Office.Interop.MSProject 名前空間で定義されます。 プライマリ相互運用機能アセンブリの詳細については、次を参照してください。 [Office ソリューション開発の概要 &#40;です。VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)と[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)です。  
  
## <a name="using-the-project-object-model-documentation"></a>Project オブジェクト モデル ドキュメントの使用  
 Project オブジェクト モデルの詳細については、Project の VBA オブジェクト モデルのリファレンスを参照してください。 VBA オブジェクト モデルのリファレンスでは、Visual Basic for Applications (VBA) コードに公開される Project オブジェクト モデルについて説明しています。 詳細については、「 [Project 2010 オブジェクト モデルのリファレンス](http://go.microsoft.com/fwlink/?LinkId=199771)」を参照してください。  
  
 VBA オブジェクト モデルのリファレンス内のオブジェクトとメンバーはすべて、Project プライマリ相互運用機能アセンブリ (PIA) の型とメンバーに対応します。 たとえば、VBA オブジェクト モデルのリファレンス内の予定表オブジェクトは、Project pia Microsoft.Office.Interop.MSProject.Calendar 型に対応します。 VBA オブジェクト モデルのリファレンスでは、ほとんどのプロパティ、メソッド、およびイベントのコード例を紹介しています。ただし、Visual Studio を使用して作成した Project VSTO アドイン プロジェクトでこのリファレンス内の VBA コードを使用するには、それらを Visual Basic または Visual C# に変換する必要があります。  
  
> [!NOTE]  
>  現在のところ、Project プライマリ相互運用機能アセンブリに関するリファレンス ドキュメントは提供されていません。  
  
### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Project プライマリ相互運用機能アセンブリのインフラストラクチャの型  
 Project PIA を使用するコードを作成すると、VBA リファレンスには記載されていない型が多数あることに気付きます。 そうした追加の型は、Project の COM ベースのオブジェクト モデルに含まれるオブジェクトをマネージ コードに変換する場合に役立ちますが、コード内で直接使用することを目的としたものではありません。  
  
 詳細については、「[Office プライマリ相互運用機能アセンブリのクラスおよびインターフェイスの概要](http://go.microsoft.com/fwlink/?LinkId=189592)」を参照してください。  
  
## <a name="customizing-the-user-interface-of-project"></a>Project のユーザー インターフェイスのカスタマイズ  
 Project の UI は次の方法でカスタマイズできます。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|Project のリボンにカスタム タブを追加する。|[リボンの概要](../vsto/ribbon-overview.md)|  
  
 プロジェクトの UI およびその他の Microsoft Office アプリケーションのカスタマイズの詳細については、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)です。  
  
## <a name="see-also"></a>参照  
 [チュートリアル: は、初めて VSTO アドイン プロジェクトの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office ソリューション開発の概要 &#40;です。VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)   
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Project 2010 と Project Server 2010 での Office 開発](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  