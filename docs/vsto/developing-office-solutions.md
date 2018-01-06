---
title: "Office ソリューションの開発 |Microsoft ドキュメント"
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
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
ms.assetid: 7361cfe0-dee4-48d7-a066-232f87f093ca
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b15c9fbf2815132ac4ad84e3b321bb22db199ed2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="developing-office-solutions"></a>Office ソリューションの開発
  Visual Studio の Office Developer Tools を使用してプロジェクトを設計し、プロジェクト ファイルを設定すると、コードとカスタム ユーザー インターフェイス (UI) の実装に集中できるようになります。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
## <a name="office-solutions-programming-model"></a>Office ソリューションのプログラミング モデル  
 Office オブジェクト モデルは、プログラミングできるさまざまなオブジェクトを公開します。 ユーザーはマネージ コードを使用して Office ソリューションをプログラミングするたびに、Office プライマリ相互運用機能アセンブリの型を使用するコードを記述します。 また、Visual Studio の Office プロジェクト テンプレートを使用して作成したソリューションでは、プロジェクトに生成されたクラスに直接コードを記述します。 詳細については、「 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)」を参照してください。  
  
## <a name="programming-different-types-of-office-solutions"></a>Office ソリューションのさまざまな種類のプログラミング  
 作成しているソリューションの種類は、プロジェクトで使用できる機能を決定します。 たとえば、デザイン時に Visual Studio の *[ツールボックス]*から項目をドラッグして、Windows フォーム コントロールおよび拡張された Office コントロール ( **ホスト コントロール** という名前) をドキュメント レベルのカスタマイズに追加することができます。 ただし、VSTO アドインを開発している場合は、コードを記述することで、これらのコントロールのみを実行時にドキュメントに追加できます。  
  
 さまざまな種類のソリューションに固有の機能の詳細については、次のトピックを参照してください。  
  
-   [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)」を参照してください。  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)。  
  
-   [Office UI のカスタマイズ](../vsto/office-ui-customization.md)です。  
  
 Office ソリューションの計画に役立つ背景情報およびプロジェクトの作成に役立つ手順については、「 [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md)」を参照してください。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)|Office ソリューションのコードの記述に関するさまざまな側面について説明します。|  
|[Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)|VSTO アドインおよび関連するプログラミング タスクのプログラミング モデルの概要を示します。|  
|[Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)|ドキュメント レベルのカスタマイズのプログラミング モデルおよび関連するプログラミング タスクの概要を示します。|  
|[Office UI のカスタマイズ](../vsto/office-ui-customization.md)|VSTO アドインおよびドキュメント レベルのカスタマイズを使用して、Office アプリケーションの UI をカスタマイズできるさまざまな方法について説明します。|  
|[Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)|コントロールへのデータ バインドおよびドキュメント レベルのカスタマイズのデータ キャッシュなど、Office ソリューションのデータを処理できるさまざまな方法について説明します。|  
|[Office ソリューションの自動保存の影響](./how-autosave-impacts-office-solutions.md)|自動保存が有効にすると、Office ソリューションに作成する必要がありますの調整について説明します。|
|[Office ソリューションのトラブルシューティング](../vsto/troubleshooting-office-solutions.md)|Office ソリューションの作成時に発生する可能性がある一般的な問題を解決するためのヒントを提供します。|  
|[Office でのスレッドのサポート](../vsto/threading-support-in-office.md)|Office ソリューションで複数のスレッドを操作する概要を示します。|  
|[Office プロジェクトのユーザー補助機能](../vsto/accessibility-in-office-projects.md)|Office ソリューションで使用できるユーザー補助機能について説明します。|  
  
## <a name="see-also"></a>参照  
 [方法: を作成し、カスタム ドキュメント プロパティの変更](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [方法: 読み取りし、書き込みのプロパティを文書化するには](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [方法: Office Multilingual User Interface のターゲット](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [チュートリアル : 初めての Excel 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [チュートリアル: 初めての Excel 用ドキュメント レベルのカスタマイズの作成](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [チュートリアル: 初めての Outlook 用 VSTO の追加の作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [チュートリアル: 初めての PowerPoint 用 VSTO の追加の作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [チュートリアル: は、初めて VSTO アドイン プロジェクトの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [チュートリアル: 初めての Word 用 VSTO の追加の作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [チュートリアル: 初めての Word 用ドキュメント レベルのカスタマイズの作成](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  