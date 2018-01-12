---
title: "Visual Studio 環境における office プロジェクト |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.ProjectItem.WordDocument
- VST.ProjectItem.ExcelWorkbook
- VST.ProjectItem.ExcelTemplate
- VST.ProjectItem.ExcelSheet
- VST.ProjectItem.BlueprintCode
- VST.ProjectItem.Word
- VST.ProjectItem.Excel
- VST.ProjectItem.AddinProject
- Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner
- VST.ProjectItem.ExtendedBluePrint
- VST.ProjectItem.WordTemplate
- Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner
- VST.Designer.ExcelVST.Designer.Word
- VST.ProjectItem.ExtendedBlueprintCode
- VST.ProjectItem.BluePrint
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- hidden files [Office development in Visual Studio]
- project files [Office development in Visual Studio], hidden
- Office development in Visual Studio, documents in Visual Studio
- design view, Excel
- designers, Office development in Visual Studio
- Office documents [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], about documents in Visual Studio
- designers [Office development in Visual Studio]
- Word designer
- Word [Office development in Visual Studio], Word designer
- Visual Studio, Office documents in
- worksheets [Office development in Visual Studio]
- VST.Designer.ExcelVST.Designer.Word
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a937f98a11ab9c8cb9723637be902808dce86563
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="office-projects-in-the-visual-studio-environment"></a>Visual Studio 環境における Office プロジェクト
  Microsoft Office プロジェクトの開発環境は、Visual Studio の他の種類のプロジェクト (Windows フォーム プロジェクトなど) に似ています。 Office プロジェクトを作成したり、開いたりすると、 **ソリューション エクスプローラー**にプロジェクト項目が表示されます。 ドキュメント レベルのプロジェクトの場合は、ドキュメント (つまり、Word 文書または Excel ブック) が Visual Studio で開かれ、ビジュアルなデザイナーとして動作します。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="project-items-in-solution-explorer"></a>ソリューション エクスプローラーのプロジェクト項目  
 ドキュメント レベルのプロジェクトの場合、 **ソリューション エクスプローラー** には次の既定の項目が表示されます。  
  
-   プロジェクトでカスタマイズされた文書、ブック、およびシートのノード。 これらのノードは、文書、ブック、およびシートに関連付けられたコード ファイルのコンテナーとして機能します。  
  
-   プロジェクトでカスタマイズされた文書、ブック、およびシートに関連付けられたコード ファイル。 Word プロジェクトの場合、コード ファイルは Word 文書またはテンプレートに関連付けられます。 Excel プロジェクトの場合、コード ファイルは Excel ブックまたはテンプレート、およびブックまたはテンプレート内の各ワークシートとグラフ シートに関連付けられます。  
  
-   直接編集することを意図していない非表示のプロジェクト ファイル。 詳細については、「 [非表示のプロジェクト ファイル](#hiddenfiles)」を参照してください。  
  
 VSTO アドイン プロジェクトの場合、 **ソリューション エクスプローラー** には次の既定の項目が表示されます。  
  
-   アプリケーション ノード。 このノードの名前は、ホスト アプリケーション ( **Word**、 **Excel**、 **Outlook**など) と同じです。 アプリケーション ノードには ThisAddIn コード ファイルが含まれています。 **ホスト項目の名前空間** プロパティも用意されています。 このプロパティの詳細については、「 [Properties in Office Projects](../vsto/properties-in-office-projects.md)」を参照してください。  
  
-   ThisAddIn コード ファイル。 このファイルには、VSTO アドイン用に生成された `ThisAddIn` クラスが含まれています。 このクラスの詳細については、次を参照してください。 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)です。  
  
-   直接編集することを意図していない非表示のプロジェクト ファイル。 詳細については、「 [非表示のプロジェクト ファイル](#hiddenfiles)」を参照してください。  
  
### <a name="temporary-certificates"></a>一時的な証明書  
 Office プロジェクトには、 *プロジェクト名*_TemporaryKey.pfx という名前の一時的な証明書も含まれています。 この証明書は、開発時にプロジェクトのアプリケーション マニフェストおよび配置マニフェストに署名するために使用します。 詳細については、次を参照してください。 [Office ソリューションへの信頼の付与](../vsto/granting-trust-to-office-solutions.md)と[Office ソリューションのセキュリティで保護する](../vsto/securing-office-solutions.md)です。  
  
###  <a name="hiddenfiles"></a> 非表示のプロジェクト ファイル  
 いくつかのプロジェクト ファイルは、既定では非表示です。 これらのファイルは Visual Studio によって生成され、プロジェクト タイプごとに異なります。 隠しファイルを表示するには、 **ソリューション エクスプローラー** で **[すべてのファイルを表示]**をクリックします。  
  
 非表示のプロジェクト ファイルを変更しないでください。 これらのファイルを直接変更することはできません。変更すると、プロジェクトが破損するおそれがあります。 非表示のプロジェクト ファイルは、ドキュメントが変更されるたびに再生成されます。 非表示のプロジェクト ファイルを手動で変更しても、ファイルを再生成するときにその変更が失われます。  
  
## <a name="document-designer-in-document-level-projects"></a>ドキュメント レベルのプロジェクト内のドキュメント デザイナー  
 Excel および Word のドキュメント レベルのプロジェクトには、Visual Studio 内のプロジェクトに関連付けられたドキュメントをホストするデザイナーが用意されています。 デザイナーでは、Visual Studio 環境から出ることなくドキュメントを変更できます。  
  
 ドキュメントをデザイナーで開くには、ドキュメントに関連付けられた **ソリューション エクスプローラー** でコード ファイルをダブルクリックします。 たとえば、Excel プロジェクトのワークシート **Sheet1** をデザイナーで開くには、 **Sheet1** コード ファイルをダブルクリックします。  
  
 デザイナーでドキュメントを変更する場合、Office アプリケーションのネイティブ機能を利用できます。 たとえば、ドキュメントやワークシートにテキストを入力したり、リボンを使用してテーブルやグラフの追加などのタスクを実行したりできます。 既定では、ショートカット キーの割り当ては Visual Studio の割り当てに設定されています。 Office のショートカット キーの割り当てを代わりに使用するには、 **[ツール]** メニューの **[オプション]** ダイアログ ボックスを開き、 **[Microsoft Office Keyboard 設定]** ノードの設定を変更します。  
  
### <a name="controls-on-documents"></a>ドキュメントのコントロール  
 Visual Studio の *[ツールボックス]* から **ホスト コントロール** や Windows フォーム コントロールをドキュメント デザイン サーフェイスにドラッグできます。 ホスト コントロール (Word コンテンツ コントロール、Excel 範囲など) は特殊なバージョンの Office オブジェクトで、Visual Studio を使用して作成された Office プロジェクトで使用できます。 ホスト コントロールには、対応する Office オブジェクトでは使用できない機能 (データ バインド、追加イベントなど) があります。  
  
 詳細については、 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md) および [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md)を参照してください。  
  
### <a name="excel-worksheets-and-workbooks-in-the-designer"></a>デザイナーでの Excel ワークシートとブック  
 ワークシートをデザイナーで開くと、Excel で直接開く場合と同じ方法でワークシートを変更できます。 ワークシート セルをダブルクリックすると、そのセルが編集モードに変わります。 ホスト コントロールを格納したセルをダブルクリックすると、コード エディターが開かれ、そのコントロールの既定のイベント ハンドラーが生成されます。 他のワークシートに移動するには、デザイナーの下部にあるワークシート タブをクリックします。  
  
 ブックをデザイナーで開いても、デザイン サーフェイスは表示されません。 ブックのデザイン ビューは、デザイナーの領域を占めている大きなコンポーネント トレイです。  
  
 ブックやブック内の各シートには、関連付けられたコード ファイルがあります。 各コード ファイルには、生成された *ホスト項目* クラスがあり、ブックまたはシートを表します。 詳細については、「 [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)」を参照してください。  
  
### <a name="word-documents-in-the-designer"></a>デザイナーでの Word 文書  
 文書をデザイナーで開くと、Word で直接開く場合と同じ方法で文書を変更できます。 文書内の単語をダブルクリックすると、その単語が選択されます。 ただし、単語がホスト コントロールの内部にある場合は、コード エディターが開かれ、そのコントロールの既定のイベント ハンドラーが生成されます。  
  
 文書には、関連付けられたコード ファイルがあります。 コード ファイルには、生成された *ホスト項目* クラスがあり、文書を表します。 詳細については、「 [Document Host Item](../vsto/document-host-item.md)」を参照してください。  
  
### <a name="design-mode-vs-run-time-mode"></a>デザイン モードと実行時モード  
 Visual Studio 環境でドキュメントを開くと、常に *デザイン モード*になります。 ホスト コントロールをドキュメントにドラッグするなど、一部のタスクは、デザイン モードでのみ実行できます。  
  
 ドキュメントを *実行時モード*で表示するには、アプリケーションとドキュメントを Visual Studio の外部で開く必要があります。 また、プロジェクトをビルドおよび実行することもできます。その場合、ドキュメントとアプリケーションは Visual Studio の外部で自動的に開かれます。  
  
## <a name="code-editor"></a>コード エディター  
 コード エディターを使用すると、ソリューション内の表示コード ファイルを表示および変更できます。 これらのファイルには、ソリューションの動作を定義するコードが含まれています。  
  
 コード エディターの詳細については、次を参照してください。[コード エディターとテキスト エディターでコードを記述](/visualstudio/ide/writing-code-in-the-code-and-text-editor)です。 Office プロジェクトのコードを記述する方法の詳細については、「 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)」を参照してください。  
  
## <a name="properties-window"></a>[プロパティ] ウィンドウ  
 **プロパティ** ウィンドウには、 **ソリューション エクスプローラー**で選択されたプロジェクト項目のプロパティ、およびデザイナーで選択された UI 要素 (ドキュメント レベル プロジェクトのコントロールや文書など) のプロパティが表示されます。 アプリケーションとドキュメントに固有のプロパティと、すべてのプロジェクトで共通のプロパティがあります。  
  
## <a name="data-sources-window"></a>データ ソース ウィンドウ  
 ドキュメント レベルの Office プロジェクトで **データ ソース** ウィンドウを使用すると、データ ソースをドキュメントにドラッグし、そのデータ ソースにバインドされているコントロールを作成できます。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインド](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)です。  
  
## <a name="see-also"></a>参照  
 [設計と、Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)   
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)   
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Office プロジェクトのプロパティ](../vsto/properties-in-office-projects.md)  
  
  