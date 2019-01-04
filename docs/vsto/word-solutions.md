---
title: Word ソリューション
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Word
- Office projects [Office development in Visual Studio], Word
- application-level add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio]
- projects [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], about Word solutions
- Office solutions [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], application-level add-ins
- documents [Office development in Visual Studio], Word
- Office development in Visual Studio, Word solutions
- add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Word
- Office documents [Office development in Visual Studio, Word
- document-level customizations [Office development in Visual Studio], Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 81154d0cab5760fa3b6a9d2418c9669258fca01f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986753"
---
# <a name="word-solutions"></a>Word ソリューション
  Visual Studio には、Microsoft Office Word のドキュメント レベルのカスタマイズおよび VSTO アドインの作成に使用できるプロジェクト テンプレートが用意されています。 これらのソリューションを使用して、Word の自動化、Word の機能拡張、Word のユーザー インターフェイス (UI) のカスタマイズを行うことができます。 ドキュメント レベルのカスタマイズと VSTO アドインの違いの詳細については、次の [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) を参照してください。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
> [!NOTE]  
>  [複数のプラットフォーム](https://dev.office.com/add-in-availability)にまたがる Office を拡張するソリューション開発に関心がありますか？ 新しい [Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)をチェックして下さい。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、HTML5、JavaScript、CSS3、XML などのほぼすべての web プログラミング テクノロジを使用して、ビルドすることができます。  
  
 ここでは、次の情報について説明します。  
  
-   [Word の自動化](#automating)します。  
  
-   [Word 用ドキュメント レベルのカスタマイズを開発](#doclevel)します。  
  
-   [Word 用 VSTO アドインの開発](#applevel)します。  
  
-   [Word のユーザー インターフェイスをカスタマイズ](#UI)します。  
  
##  <a name="automating"></a> Word を自動化します。  
 Word オブジェクト モデルでは、Word の自動化に使用できる型が多数公開されています。 たとえば、プログラムを使用して、表の作成、文書の書式設定、範囲内や段落内でのテキストの設定などを行うことができます。 詳細については、次を参照してください。 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)します。  
  
 Visual Studio で Word ソリューションを開発するときには、ソリューションの *ホスト項目* および *ホスト コントロール* を使用することもできます。 Word オブジェクト モデルには、 <xref:Microsoft.Office.Interop.Word.Document> や <xref:Microsoft.Office.Interop.Word.ContentControl> などのよく使用される特定のオブジェクトを拡張したオブジェクトがあります。 これらの拡張オブジェクトは、基になる Word オブジェクトと同じように動作しますが、基のオブジェクトにはないイベントとデータ バインディング機能が追加されています。 詳細については、次を参照してください。[拡張オブジェクトを使用して Word の自動化](../vsto/automating-word-by-using-extended-objects.md)します。  
  
##  <a name="doclevel"></a> Word 用ドキュメント レベル カスタマイズを開発します。  
 Microsoft Office Word のドキュメント レベルのカスタマイズは、特定の文書に関連付けられたアセンブリで構成されます。 このアセンブリは、一般には UI のカスタマイズと Word の自動化によってドキュメントの機能を拡張します。 Word 自体と関連付けられる VSTO アドインとは異なり、カスタマイズに実装した機能は、関連付けられた文書が Word で開かれている場合にのみ利用できます。  
  
 Word のドキュメント レベルのカスタマイズ プロジェクトを作成するには、Visual Studio の **[新しいプロジェクト]** ダイアログ ボックスで Word 文書または Word テンプレートのプロジェクト テンプレートを使用します。 詳細については、「[方法 :Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
 ドキュメント レベルのカスタマイズの動作の詳細については[のドキュメント レベル カスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)します。  
  
### <a name="word-customization-programming-model"></a>Word カスタマイズのプログラミング モデル  
 Word のドキュメント レベルのプロジェクトを作成すると、 `ThisDocument`と呼ばれる、ソリューションの基礎となるクラスが Visual Studio によって生成されます。 このクラスは、ソリューションに関連付けられたドキュメントを表し、コードを記述する際の開始点となります。  
  
 詳細については、`ThisDocument`クラスおよびドキュメント レベルのプロジェクトで使用できるその他の機能を参照してください[ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)します。  
  
##  <a name="applevel"></a> Word 用 VSTO アドインを開発します。  
 Microsoft Office Word の VSTO アドインは、Word によって読み込まれるアセンブリで構成されます。 このアセンブリは、一般には UI のカスタマイズと Word の自動化によって Word の機能を拡張します。 特定のドキュメントに関連付けられたドキュメント レベルのカスタマイズとは異なり、VSTO アドインに実装する機能の対象は 1 つの文書に制限されません。  
  
 Word 用の VSTO アドイン プロジェクトを作成するには、Visual Studio の **[新しいプロジェクト]** ダイアログ ボックスで Word アドイン プロジェクト テンプレートを使用します。 詳細については、「[方法 :Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
 VSTO アドインが機能するしくみの概要については、次の [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md) を参照してください。  
  
### <a name="word-add-in-programming-model"></a>Word アドインのプログラミング モデル  
 Word VSTO アドイン プロジェクトを作成すると、 `ThisAddIn`と呼ばれる、ソリューションの基礎となるクラスが Visual Studio によって生成されます。 このクラスは、コードを記述する際の開始点となり、Word のオブジェクト モデルを VSTO アドインに公開します。  
  
 詳細については、`ThisAddIn`クラスと、VSTO アドインで使用できるその他の機能を参照してください[プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)します。  
  
##  <a name="UI"></a> Word のユーザー インターフェイスをカスタマイズします。  
 Word のユーザー インターフェイスをカスタマイズする方法はいくつかあります。 一部のオプションはすべてのプロジェクト タイプで使用できますが、VSTO アドインまたはドキュメント レベルのカスタマイズでのみ使用できるオプションもあります。  
  
### <a name="options-for-all-project-types"></a>すべてのプロジェクトの種類のオプション  
 ドキュメント レベルのカスタマイズと VSTO アドインの両方に使用できるカスタマイズ オプションを次の表に示します。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|リボンをカスタマイズする。|[リボンの概要](../vsto/ribbon-overview.md)|  
|カスタマイズされた文書 (ドキュメント レベルのカスタマイズの場合) または開いている任意の文書 (VSTO アドインの場合) に Windows フォーム コントロールまたは拡張された Word コントロールを追加する。|[方法: Office ドキュメントへの Windows フォーム コントロールを追加します。](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [方法: コンテンツ コントロールを Word 文書に追加します。](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [方法: Word 文書に bookmark コントロールを追加します。](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|  
  
### <a name="options-for-document-level-customizations"></a>ドキュメント レベルのカスタマイズのオプション  
 ドキュメント レベルのカスタマイズにのみ使用できるカスタマイズ オプションを次の表に示します。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|文書に操作ウィンドウを追加する。|[操作ウィンドウの概要](../vsto/actions-pane-overview.md)<br /><br /> [方法: Word 文書または Excel ブックに操作ウィンドウを追加します。](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|拡張された XMLNode コントロールおよび XMLNodes コントロールをドキュメントに追加する。|[方法: Word 文書に XMLNode コントロールを追加します。](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [方法: Word 文書に XMLNodes コントロールを追加します。](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|  
  
### <a name="options-for-vsto-add-ins"></a>VSTO アドインのオプション  
 VSTO アドインにのみ使用できるカスタマイズ オプションを次の表に示します。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|カスタム作業ウィンドウを作成する。|[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)|Word オブジェクト モデルに用意されている主な型の概要について説明します。|  
|[拡張オブジェクトを使用して Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)|Word ソリューションで使用できる ( [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]に用意されている) 拡張オブジェクトについて説明します。|  
|[Office ドキュメントの概要での Windows フォーム コントロール](../vsto/windows-forms-controls-on-office-documents-overview.md)|Windows フォーム コントロールを Word 文書に追加する方法について説明します。|  
|[チュートリアル: 最初の Word 用ドキュメント レベルのカスタマイズを作成します。](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Word 用の基本的なドキュメント レベルのカスタマイズを作成する方法を示します。|  
|[チュートリアル: Word 用の最初の VSTO アドインの作成します。](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Word 用の基本的な VSTO アドインを作成する方法を示します。|  
|[チュートリアル: VSTO アドインにおける実行時のドキュメントにコントロールを追加します。](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|VSTO アドインを使用して、実行時に Windows フォームのボタンおよび <xref:Microsoft.Office.Tools.Word.RichTextContentControl> を文書に追加する方法を示します。|  
|[Office 開発における Word 2010](http://go.microsoft.com/fwlink/?LinkId=199020)|Word ソリューションの開発に関する文書やリファレンス ドキュメントへのリンクを示します (Visual Studio を使用した Office 開発に限定されません)。|  
