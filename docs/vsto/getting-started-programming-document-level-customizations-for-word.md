---
title: Word 用ドキュメント レベル カスタマイズのプログラミングを開始します。
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 36eedad9432738119b1993ba56ae46a363b166a0
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648414"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Word 用ドキュメント レベル カスタマイズのプログラミングを開始します。
  開始した場合は取得する Visual Studio を使用して Microsoft Office Word のドキュメント レベルのカスタマイズを作成する、次を知る必要がありますに示します。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-word-work"></a>Word 作業用のドキュメント レベルのカスタマイズを理解します。  
 作成する各単語のカスタマイズは、1 つのドキュメントに基づいています。 カスタマイズの使用を開始するには、エンドユーザーがドキュメントを開くまたは Word テンプレートからドキュメントを作成します。 たとえば特定の領域にカーソルを移動またはボタンおよびメニュー項目をクリックすると、ドキュメント内のイベントは、アセンブリ内のイベント処理メソッドを呼び出すことができます。 ドキュメントが閉じられたときに、カスタマイズによって提供される機能は Word では使用ではなくなりました。  
  
 詳細については、次を参照してください。[のドキュメント レベル カスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)します。  
  
## <a name="create-document-level-projects-for-word"></a>Word 用ドキュメント レベルのプロジェクトを作成します。  
 Word 用ドキュメント レベルのカスタマイズを作成する Word 文書または Word テンプレート プロジェクト テンプレートを使用して、**新しいプロジェクト** ダイアログ ボックス。 これらのテンプレートには必要なアセンブリ参照とプロジェクト ファイルが含まれています。  
  
 Word 用ドキュメント レベルのプロジェクトを作成する方法の詳細については、次を参照してください。[方法。Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。 プロジェクト テンプレートの詳細については、次を参照してください。 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)します。  
  
## <a name="program-word-documents-by-using-host-items-host-controls"></a>ホスト項目とホスト コントロールを使用して Word 文書をプログラム  
 *ホスト項目*と*ホスト コントロール*はドキュメント レベルのカスタマイズのプログラミング モデルを提供するクラス。  
  
 ホスト項目が、コードのエントリ ポイントを提供し、ホスト コントロールや Windows フォーム コントロールのコンテナーとしても機能できます。 Word 用ドキュメント レベルのプロジェクトでは、ホスト項目で表される、`ThisDocument`クラス。  
  
 ホスト コントロールは、コンテンツ コントロール、ブックマーク、および XML ノードなど、ネイティブな Word オブジェクトに基づいています。 ホスト コントロールは、ネイティブな Word オブジェクトと同様の機能を提供し、新しいイベント、デザイナー サポート、およびデータ バインディング機能も備えています。 プロジェクト コードでは、Word オブジェクト モデル内を移動することがなくコード内で直接特定のオブジェクトを参照しやすく、IntelliSense で最上位のオブジェクトとして表示されます。  
  
 詳細については、次のトピックを参照してください。  
  
-   [プログラムのドキュメント レベルのカスタマイズ](../vsto/programming-document-level-customizations.md)  
  
-   [拡張オブジェクトを使用して Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-word"></a>Word のユーザー インターフェイスをカスタマイズします。  
 ほとんどの Microsoft Office ソリューションでは、ソリューションとの対話をユーザーに対していくつかの方法を提供する Office アプリケーションのユーザー インターフェイス (UI) を変更します。 ドキュメント レベルのカスタマイズを使用して Word の UI を変更する方法はたくさんあります。 たとえば、コントロールは、リボンを追加することができ、操作ウィンドウを表示することができます。 詳細については、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)します。  
  
 Visual Studio で直接プロジェクトに関連付けられているドキュメントを開くこともできます。 文書が Visual Studio で開いているときは、Word のユーザー インターフェイスを使用して、ドキュメントを変更できます。 コントロールをドラッグすることができます、デザイン サーフェイスとしてドキュメントを使用することもできます。 詳細については、次を参照してください。 [Visual Studio 環境における Office プロジェクト](../vsto/office-projects-in-the-visual-studio-environment.md)します。  
  
## <a name="bind-controls-to-data"></a>データ コントロールをバインドします。  
 コンテンツ コントロールと<xref:Microsoft.Office.Tools.Word.Bookmark>からドラッグできるコントロールのリストでのコントロールは、**データソース**ウィンドウ。 コンテンツ コントロールや方法に自動的にこのブックマークを追加するウィンドウを使用して設定したデータ ソースにバインドします。 コードを記述せずには、データベース、サービス、およびビジネス オブジェクトからデータを表示できます。 詳細については、次を参照してください。 [Office ソリューションでのコントロールにデータをバインド](../vsto/binding-data-to-controls-in-office-solutions.md)します。  
  
## <a name="next-steps"></a>次の手順  
 Word 用ドキュメント レベルのカスタマイズを作成する方法についてを参照してください。[チュートリアル。最初の Word 用ドキュメント レベルのカスタマイズを作成する](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)します。 このチュートリアルでは、Visual Studio と Word のドキュメント レベルのカスタマイズのプログラミング モデルでの Office 開発ツールについて説明します。  
  
 Word プロジェクトで、一般的なタスクを解説しているトピックの一覧は、次を参照してください。 [Office プログラミングで一般的なタスク](../vsto/common-tasks-in-office-programming.md)します。  
  
## <a name="see-also"></a>関連項目  
 [方法: Visual Studio での Office プロジェクトを作成します。](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [プログラムのドキュメント レベルのカスタマイズ](../vsto/programming-document-level-customizations.md)   
 [Word ソリューション](../vsto/word-solutions.md)   
 [チュートリアル: 最初の Word 用ドキュメント レベルのカスタマイズを作成します。](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Word を使用したチュートリアル](../vsto/walkthroughs-using-word.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [Office ソリューションでコードを記述します。](../vsto/writing-code-in-office-solutions.md)  
  
  