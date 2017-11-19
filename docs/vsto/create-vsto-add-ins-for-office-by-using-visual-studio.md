---
title: "Visual Studio を使用して Office 用の VSTO アドインを作成する |Microsoft ドキュメント"
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
ms.assetid: eabd0377-cb94-4c1e-a99c-f13ff8df1a87
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d3006ddafa743a5cd55a687895e894f3cbb068a9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="create-vsto-add-ins-for-office-by-using-visual-studio"></a>Visual Studio を使用して Office 用 VSTO アドインを作成する
  Visual Studio の Microsoft Office Developer Tools を使用して、Office を拡張する .NET Framework アプリケーションを作成できます。 このようなアプリケーションは、 *Office ソリューション*とも呼ばれます。  
  
 Office Developer Tools で提供される機能は、さまざまなビジネス要件に合った Office ソリューションを作成するのに役立ちます。 このツールには、Visual Basic または Visual C# を使用した Office ソリューションの作成に役立つプロジェクト テンプレートや、Office ソリューションで使用するカスタム ユーザー インターフェイスの作成に役立つビジュアルなデザイナーが含まれています。  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
 Office 開発の最新情報については、MSDN の次の開発センターを参照してください。  
  
-   [Visual Studio での Office 開発に関する開発者向けポータル](http://go.microsoft.com/fwlink/?LinkId=123844) では、Visual Studio を使用した、ソリューションの一部としての Office アプリケーションのカスタマイズに関する製品情報、コード サンプル、ビデオ、コミュニティ リソースへのリンクが提供されています。  
  
-   [Microsoft Office デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=83467) では、Office のカスタマイズと Office Business Application (OBA) に関する技術記事、コード サンプル、ダウンロード、コミュニティ情報、サポート、およびその他のドキュメントへのリンクが提供されています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [作業の開始 (&) #40 です。 Visual Studio &#41; での Office 開発](../vsto/getting-started-office-development-in-visual-studio.md)  
 Office ソリューションの作成用に開発コンピューターを構成する方法、Office ソリューションの作成を開始する方法、および Visual Studio での Office 開発を対象とする新機能に関する情報へのリンクを示します。  
  
 [Office ソリューションのアップグレードと移行](../vsto/upgrading-and-migrating-office-solutions.md)  
 Visual Studio の以前のバージョンを使用して作成されたプロジェクトのアップグレード プロセスに関する情報へのリンクを示します。  
  
 [Visual Studio の Office ソリューションのアーキテクチャ](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
 ドキュメント レベルのカスタマイズと VSTO アドインに関する情報など、Office ソリューションの動作に関する情報へのリンクを示します。  
  
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)  
 Visual Studio で Office プロジェクトを作成し、プロジェクトを構成する方法について説明します。  
  
 [Office ソリューションの開発](../vsto/developing-office-solutions.md)  
 Office ユーザー インターフェイスをカスタマイズする方法、データを処理する方法、問題のトラブルシューティングを行う方法など、Office ソリューションでマネージ コードを使用する方法について説明します。  
  
 [Excel ソリューション](../vsto/excel-solutions.md)  
 Excel を自動化する方法、Excel ソリューションを作成する方法、および Excel に固有のグローバリゼーションに関する問題を理解する方法について説明します。  
  
 [InfoPath ソリューション](../vsto/infopath-solutions.md)  
 InfoPath のフォーム テンプレートおよび VSTO アドインを作成する方法について説明します。  
  
 [Outlook ソリューション](../vsto/outlook-solutions.md)  
 Outlook を自動化し、Outlook VSTO アドインおよびフォーム領域を作成する方法について説明します。  
  
 [PowerPoint ソリューション](../vsto/powerpoint-solutions.md)  
 PowerPoint を自動化し、PowerPoint VSTO アドインを作成する方法について説明します。  
  
 [Project ソリューション](../vsto/project-solutions.md)  
 Microsoft Office プロジェクトを自動化し、Project VSTO アドインを作成する方法について説明します。  
  
 [Visio ソリューション](../vsto/visio-solutions.md)  
 Visio を自動化し、Visio VSTO アドインを作成する方法について説明します。  
  
 [Word ソリューション](../vsto/word-solutions.md)  
 Word を自動化し、Word ソリューションを作成する方法について説明します。  
  
 [Office ソリューションのビルド](../vsto/building-office-solutions.md)  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]における、Office プロジェクトのビルドと、その他の種類のプロジェクトのビルドとの間の相違点について説明します。  
  
 [Office Project のデバッグ](../vsto/debugging-office-projects.md)  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]における、Office プロジェクトのデバッグと、その他の種類のプロジェクトのデバッグとの間の相違点について説明します。  
  
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)  
 Office ソリューションにおけるセキュリティ機能のしくみについて説明します。  
  
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)  
 Office ソリューションをユーザーが使用できるようにする方法、および配置方法を選択するときに考慮する主な問題点について説明します。  
  
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)  
 サンプル アプリケーション、および一般的なタスクの詳細な手順を説明するトピックへのリンクを示します。  
  
 [全般リファレンス (&) #40 です。 Visual Studio &#41; での Office 開発](../vsto/general-reference-office-development-in-visual-studio.md)  
 Office プライマリ相互運用機能アセンブリ、マニフェスト、ユーザー インターフェイス要素、およびエラー メッセージに関する詳細情報へのリンクを示します。  
  
 [マネージ参照 (&) #40 です。 Visual Studio &#41; での Office 開発](../vsto/managed-reference-office-development-in-visual-studio.md)  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]を対象とする Office プロジェクトで使用される API の名前空間と型に関する情報へのリンクを示します。 .NET Framework 3.5 を対象とする Office プロジェクトで使用される名前空間と型に関する API リファレンス ドキュメントについては、Visual Studio 2008 ドキュメントのリファレンス セクション「 [2007 System マネージ参照](http://go.microsoft.com/fwlink/?LinkId=160658)」をご覧ください。  
  
 [アンマネージ API リファレンス (&) #40 です。 Visual Studio &#41; での Office 開発](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
 Office アプリケーションでマネージ VSTO アドインのロードとアンロードなどの操作を実行するために使用できる COM インターフェイスに関する情報へのリンクを示します。  
  
## <a name="related-sections"></a>関連項目  
 [Visual Studio での Office 開発に関する開発者向けポータル](http://go.microsoft.com/fwlink/?LinkId=123844)  
 技術記事、ビデオ、ブログなど、その他のリソースを提供します。  
  
 [Visual Studio デベロッパー センター](http://go.microsoft.com/fwlink/?LinkID=99124)  
 技術記事、ビデオ、ブログなど、Visual Studio に関するその他のリソースを提供します。  
  
 [Office Business Application デベロッパー ポータル](http://go.microsoft.com/fwlink/?LinkId=99125)  
 Office Business Application (OBA) について、および Office system プラットフォームを使用してそれらをビルドする方法について説明します。  
  
 [MSDN ライブラリの Microsoft Office 開発に関するセクション](http://go.microsoft.com/fwlink/?LinkId=149870)  
 この MSDN ライブラリの領域では、Office の複数のバージョンを対象とするソリューションの開発に関する記事やリファレンス ドキュメントを参照できます (Visual Studio を使用した Office 開発以外のトピックも含まれています)。  
  
 [Visual Studio でのアプリケーション開発](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68)  
 Visual Studio を使用して、Web アプリケーション、XML Web サービス、および従来のクライアント アプリケーションを設計、開発、デバッグ、および配置する方法に関するトピックへのリンクを示します。  
  
 [Visual Studio での .NET Framework プログラミング](http://msdn.microsoft.com/en-us/f3f63195-82c6-48e8-a4a0-612810e7d093)  
 Visual Basic および Visual C# での .NET Framework を使用したアプリケーション開発について説明します。  
  
  