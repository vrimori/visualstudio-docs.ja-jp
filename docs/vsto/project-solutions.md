---
title: プロジェクトから成るソリューション
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3364c778b8dfc290ef06b7daa5ba063ac31f3db
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692601"
---
# <a name="project-solutions"></a>プロジェクトから成るソリューション
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] には、Microsoft Office Project の VSTO アドインを作成するために使用できるプロジェクト テンプレートが用意されています。 VSTO アドインを使用すると、Project の自動化、Project 機能の拡張、Project ユーザー インターフェイス (UI) のカスタマイズが可能です。  
  
 詳細については、VSTO アドインは、次を参照してください。 [VSTO アドインのプログラミングを始める](../vsto/getting-started-programming-vsto-add-ins.md)と[アーキテクチャの VSTO アドイン](../vsto/architecture-of-vsto-add-ins.md)です。Microsoft Office でのプログラミングに慣れていない場合は、次を参照してください。[開始&#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)です。  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
## <a name="automate-project-by-using-the-project-object-model"></a>Project オブジェクト モデルを使用して、project を自動化します。  
 Project オブジェクト モデルでは、Project の自動化に使用できる型が多数公開されています。 これらの型により、プロジェクト内のタスクをプログラムによって作成したり変更したりするなど、一般的なタスクを行うコードを記述できます。  
  
 VSTO アドインから Project オブジェクト モデルにアクセスするには、プロジェクト内の `Application` クラスの `ThisAddIn` フィールドを使用します。 `Application`フィールドを返します、`Microsoft.Office.Interop.MsProject.Application`プロジェクトの現在のインスタンスを表すオブジェクト。 詳細については、次を参照してください。[プログラムは、VSTO アドイン](../vsto/programming-vsto-add-ins.md)です。  
  
 Project オブジェクト モデルを呼び出すときには、Project のプライマリ相互運用機能アセンブリに用意された型を使用します。 プライマリ相互運用機能アセンブリは、VSTO アドインのマネージ コードと Project の COM オブジェクト モデルとの仲介役を果たします。 Project プライマリ相互運用機能アセンブリ内の型は、すべて `Microsoft.Office.Interop.MSProject` 名前空間に定義されています。 プライマリ相互運用機能アセンブリの詳細については、次を参照してください。 [Office ソリューション開発の概要&#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md)と[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)です。  
  
## <a name="use-the-project-object-model-documentation"></a>Project オブジェクト モデル ドキュメントを使用します。  
 Project オブジェクト モデルの詳細については、Project の VBA オブジェクト モデルのリファレンスを参照してください。 VBA オブジェクト モデルのリファレンスでは、Visual Basic for Applications (VBA) コードに公開される Project オブジェクト モデルについて説明しています。 詳細については、次を参照してください。 [Project 2010 オブジェクト モデル リファレンス](http://go.microsoft.com/fwlink/?LinkId=199771)です。  
  
 VBA オブジェクト モデルのリファレンス内のオブジェクトとメンバーはすべて、Project プライマリ相互運用機能アセンブリ (PIA) の型とメンバーに対応します。 たとえば、VBA オブジェクト モデルのリファレンス内の予定表オブジェクトに対応しています。、 `Microsoft.Office.Interop.MSProject.Calendar` 、Project pia の型。 VBA オブジェクト モデルのリファレンスでは、ほとんどのプロパティ、メソッド、およびイベントのコード例を紹介しています。ただし、Visual Studio を使用して作成した Project VSTO アドイン プロジェクトでこのリファレンス内の VBA コードを使用するには、それらを Visual Basic または Visual C# に変換する必要があります。  
  
> [!NOTE]  
>  現在のところ、Project プライマリ相互運用機能アセンブリに関するリファレンス ドキュメントは提供されていません。  
  
### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Project プライマリ相互運用機能アセンブリで型のインフラストラクチャ  
 Project PIA を使用するコードを作成すると、VBA リファレンスには記載されていない型が多数あることに気付きます。 そうした追加の型は、Project の COM ベースのオブジェクト モデルに含まれるオブジェクトをマネージ コードに変換する場合に役立ちますが、コード内で直接使用することを目的としたものではありません。  
  
 詳細については、次を参照してください。 [Office プライマリ相互運用機能アセンブリのクラスおよびインターフェイスの概要](http://go.microsoft.com/fwlink/?LinkId=189592)です。  
  
## <a name="customize-the-user-interface-of-project"></a>プロジェクトのユーザー インターフェイスをカスタマイズします。  
 Project の UI は次の方法でカスタマイズできます。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|Project のリボンにカスタム タブを追加する。|[リボンの概要](../vsto/ribbon-overview.md)|  
  
 プロジェクトの UI およびその他の Microsoft Office アプリケーションのカスタマイズの詳細については、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)です。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: は、最初に VSTO アドイン プロジェクトの作成します。](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [VSTO アドインのプログラミングを始める](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO アドインをプログラミングします。](../vsto/programming-vsto-add-ins.md)   
 [Office ソリューションでコードを記述します。](../vsto/writing-code-in-office-solutions.md)   
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Project 2010 と Project Server 2010 での Office 開発](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  