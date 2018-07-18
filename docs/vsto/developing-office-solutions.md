---
title: Office ソリューションを開発します。
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fd5829a3d09d96ad0ed9cfce3dd4bc329e70f907
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268189"
---
# <a name="develop-office-solutions"></a>Office ソリューションを開発します。
  Visual Studio の Office Developer Tools を使用してプロジェクトを設計し、プロジェクト ファイルを設定すると、コードとカスタム ユーザー インターフェイス (UI) の実装に集中できるようになります。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインでは、VSTO アドインと、ソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
## <a name="office-solutions-programming-model"></a>Office ソリューションのプログラミング モデル  
 Office オブジェクト モデルは、プログラミングできるさまざまなオブジェクトを公開します。 ユーザーはマネージ コードを使用して Office ソリューションをプログラミングするたびに、Office プライマリ相互運用機能アセンブリの型を使用するコードを記述します。 また、Visual Studio の Office プロジェクト テンプレートを使用して作成したソリューションでは、プロジェクトに生成されたクラスに直接コードを記述します。 詳細については、次を参照してください。 [Office ソリューションでコードを記述](../vsto/writing-code-in-office-solutions.md)です。  
  
## <a name="program-different-types-of-office-solutions"></a>Office ソリューションのさまざまな種類のプログラム  
 作成しているソリューションの種類は、プロジェクトで使用できる機能を決定します。 たとえば、デザイン時に Visual Studio の *[ツールボックス]* から項目をドラッグして、Windows フォーム コントロールおよび拡張された Office コントロール ( **ホスト コントロール** という名前) をドキュメント レベルのカスタマイズに追加することができます。 ただし、VSTO アドインを開発している場合は、コードを記述することで、これらのコントロールのみを実行時にドキュメントに追加できます。  
  
 さまざまな種類のソリューションに固有の機能の詳細については、次のトピックを参照してください。  
  
-   [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)です。  
  
-   [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)です。  
  
-   [Office UI のカスタマイズ](../vsto/office-ui-customization.md)です。  
  
 Office ソリューションおよびプロジェクトを作成するための手順を計画に役立つ背景情報については、次を参照してください。[デザインおよび Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)です。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[Office ソリューションでコードを記述します。](../vsto/writing-code-in-office-solutions.md)|Office ソリューションのコードの記述に関するさまざまな側面について説明します。|  
|[VSTO アドインをプログラミングします。](../vsto/programming-vsto-add-ins.md)|VSTO アドインおよび関連するプログラミング タスクのプログラミング モデルの概要を示します。|  
|[ドキュメント レベルのカスタマイズをプログラミングします。](../vsto/programming-document-level-customizations.md)|ドキュメント レベルのカスタマイズのプログラミング モデルおよび関連するプログラミング タスクの概要を示します。|  
|[Office UI のカスタマイズ](../vsto/office-ui-customization.md)|VSTO アドインおよびドキュメント レベルのカスタマイズを使用して、Office アプリケーションの UI をカスタマイズできるさまざまな方法について説明します。|  
|[Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)|コントロールへのデータ バインドおよびドキュメント レベルのカスタマイズのデータ キャッシュなど、Office ソリューションのデータを処理できるさまざまな方法について説明します。|  
|[Office ソリューションの自動保存の影響](./how-autosave-impacts-office-solutions.md)|自動保存が有効にすると、Office ソリューションに作成する必要がありますの調整について説明します。|
|[Office ソリューションをトラブルシューティングします。](../vsto/troubleshooting-office-solutions.md)|Office ソリューションの作成時に発生する可能性がある一般的な問題を解決するためのヒントを提供します。|  
|[スレッド処理のオフィスのサポート](../vsto/threading-support-in-office.md)|Office ソリューションで複数のスレッドを操作する概要を示します。|  
|[Office プロジェクトのユーザー補助機能](../vsto/accessibility-in-office-projects.md)|Office ソリューションで使用できるユーザー補助機能について説明します。|  
  
## <a name="see-also"></a>関連項目  
 [方法: を作成し、カスタム ドキュメント プロパティの変更](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [方法: ドキュメント プロパティに書き込み、読み取りと](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [方法: Office の多言語ユーザー インターフェイス ターゲット](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Excel 用チュートリアル: を初めて VSTO アドインの作成します。](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [チュートリアル: 初めての Excel 用ドキュメント レベルのカスタマイズを作成します。](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [チュートリアル: は、最初に VSTO アドイン Outlook の作成します。](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [チュートリアル: 初めて VSTO アドインの PowerPoint を作成します。](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [チュートリアル: は、最初に VSTO アドイン プロジェクトの作成します。](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [チュートリアル: 初めて VSTO アドインの Word の作成します。](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [チュートリアル: 初めての Word 用ドキュメント レベルのカスタマイズを作成します。](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  