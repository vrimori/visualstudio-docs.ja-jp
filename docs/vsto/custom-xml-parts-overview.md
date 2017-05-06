---
title: "カスタム XML 部分の概要"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "カスタム XML 部分 [Visual Studio での Office 開発]"
  - "カスタム XML 部分 [Visual Studio での Office 開発], 概要"
  - "データ [Visual Studio での Office 開発], カスタム XML 部分"
  - "ドキュメント [Visual Studio での Office 開発], カスタム XML 部分"
  - "埋め込み (XML データをドキュメントに) [Visual Studio での Office 開発]"
  - "Excel [Visual Studio での Office 開発], カスタム XML 部分"
  - "Office ドキュメント [Visual Studio での Office 開発, カスタム XML 部分"
  - "Office Open XML Formats [Visual Studio での Office 開発]"
  - "Word [Visual Studio での Office 開発], カスタム XML 部分"
  - "XML [Visual Studio での Office 開発], カスタム XML 部分"
  - "XML ファイル形式 [Visual Studio での Office 開発]"
  - "XML 部分 [Visual Studio での Office 開発]"
ms.assetid: a14119dc-59e8-4614-94f1-08c92bdf7300
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# カスタム XML 部分の概要
  一部の Microsoft Office アプリケーションのドキュメントに XML データを埋め込むことができます。  ドキュメントに XML データを埋め込む場合、そのデータには「*カスタム XML 部分*」という名前が付きます。  
  
 Visual Studio で VSTO アドインまたはドキュメント レベルのソリューションを使用して、ドキュメントのカスタム XML 部分を作成または変更できます。  カスタム XML 部分を作成または変更するために Microsoft Office アプリケーションを開始する必要はありません。  
  
 **対象:** このトピックの情報は、Excel、PowerPoint、および Word のドキュメント レベルのプロジェクトおよび VSTO アドインのプロジェクトに適用されます。  詳細については、「[Office アプリケーションおよびプロジェクト タイプ別の使用可能な機能](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。  
  
> [!NOTE]  
>  Visual Studio では、ドキュメント レベルのカスタマイズ内のデータ オブジェクトをキャッシュすることもできます。  いくつかの類似点はありますが、この機能はカスタム XML 部分とは異なります。  詳細については、「[ドキュメント レベルのカスタマイズのキャッシュ データ](../vsto/cached-data-in-document-level-customizations.md)」を参照してください。  
  
## カスタム XML 部分について  
 カスタム XML 部分は、2007 Microsoft Office system で Open XML 形式とともに導入されました。  これらの形式には Excel、PowerPoint、および Word 用の新しい XML ベースのファイル形式 \(.xlsx、.pptx、.docx\) が含まれます。  これらの形式のドキュメントは、ZIP アーカイブ内のフォルダーに編成される XML ファイル \(「*XML 部分*」とも呼ばれます\) で構成されます。  XML 部分のほとんどは、ドキュメントの構造と状態を定義するのに役立つ組み込みの部分です。  ただし、ドキュメントにはカスタム XML 部分を含めることができ、ユーザーはこれを使用して、ドキュメントに任意の XML データを格納できます。  
  
 XML ファイル形式により、アプリケーションは古いバイナリ ファイル形式 \( .xls、.ppt、.doc\) ではできない方法でドキュメントを操作できます。  ZIP アーカイブを読み取ることができるすべてのアプリケーションは、Microsoft Office がインストールされていない場合でも、ドキュメントの内容を検証し、変更できます。  
  
 Open XML およびカスタム XML 部分の構造の詳細については、次の記事をご覧ください。  
  
-   [Office \(2007\) Open XML ファイル形式の概要](http://msdn.microsoft.com/ja-jp/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [方法: Open XML 形式のドキュメントを操作する](http://msdn.microsoft.com/ja-jp/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [チュートリアル: Word 2007 の XML 形式](http://msdn.microsoft.com/ja-jp/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [Open XML 形式を使用して、Word 2007 ドキュメントを作成する](http://msdn.microsoft.com/ja-jp/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Excel、Word、および PowerPoint ではバイナリ ファイル形式で保存されているドキュメント内のカスタム XML 部分を使用することもできます。  ただし、バイナリ形式でドキュメントを保存する場合は、Microsoft Office アプリケーションを起動せずにカスタム XML 部分を追加または変更することはできません。  
  
## カスタム XML 部分の作成および変更  
 ドキュメントが Office アプリケーションで開いているとき、またはドキュメントが閉じているとき \(Microsoft Office がインストールされていない場合でも\)、カスタム XML 部分を作成または変更できます。  
  
### Office アプリケーションの実行中に、XML 部分を変更する  
 ドキュメント レベルのカスタマイズまたは VSTO アドインを使用して、カスタム XML 部分を操作できます。  ドキュメント レベルのカスタマイズを使用している場合は、通常、カスタマイズされたドキュメント内にあるカスタム XML 部分を操作します。  VSTO アドインを使用している場合は、アプリケーションで開いているすべてのドキュメントのカスタム XML 部分を作成、または変更できます。  
  
 Visual Studio を使用してカスタム XML 部分を作成するには、新しい <xref:Microsoft.Office.Core.CustomXMLPart> をドキュメントの <xref:Microsoft.Office.Core.CustomXMLParts> コレクションに追加します。  詳細については、次のトピックを参照してください。  
  
-   [方法 : ドキュメント レベルのカスタマイズにカスタム XML 部分を追加する](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [方法: VSTO アドインを使用してドキュメントにカスタム XML 部分を追加する](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### Office アプリケーション起動せずに XML 部分を変更する  
 Excel、PowerPoint、または Word を起動しないでカスタム XML 部分を変更できます。  これは、Microsoft Office アプリケーションがインストールされていないサーバーなどのコンピューターで、ドキュメント内の XML データを使用する場合に便利です。  
  
 Microsoft Office を起動せずにカスタム XML 部分を追加するには Open XML SDK のクラスを使用します。  これらのクラスは、Office ドキュメントに固有の Open XML コンテンツにアクセスするために設計されています。  たとえば、カスタム XML 部分を Excel ブックに追加するには、[WorkbookPart](http://msdn.microsoft.com/ja-jp/d011e6f4-77dd-d02d-66ef-dc4a9e7b26f2) オブジェクトの [AddNewPart\<T\>](http://msdn.microsoft.com/ja-jp/47c348c0-77ab-a504-5097-bcd6a213921a) メソッドを使用します。  詳細については、「[Open XML SDK 2.0](http://msdn.microsoft.com/ja-jp/f6a9ae68-7989-4208-97f5-3c945137a0ab)」を参照してください。  
  
## Word のコンテンツ コントロールへのカスタム XML 部分のバインディング  
 Word ソリューションのコンテンツ コントロールをカスタム XML 部分の要素にバインドできます。  カスタム XML 部分にコンテンツ コントロールがバインドされると、カスタム XML 部分のデータがコンテンツ コントロールのユーザー インターフェイス \(UI\) に表示されます。  ユーザーがコントロール内のテキストを編集すると、対応する XML 要素が自動的に更新されます。  同様に、カスタム XML 部分の要素の値が変更されると、その XML 要素にバインドされているコンテンツ コントロールに新しいデータが表示されます。  詳細については、「[コンテンツ コントロール](../vsto/content-controls.md)」を参照してください。  
  
## 参照  
 [ドキュメント レベルのカスタマイズにおける XML スキーマとデータ](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [方法 : ドキュメント レベルのカスタマイズにカスタム XML 部分を追加する](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [方法: VSTO アドインを使用してドキュメントにカスタム XML 部分を追加する](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [コンテンツ コントロール](../vsto/content-controls.md)   
 [チュートリアル : カスタム XML 部分へのコンテンツ コントロールのバインド](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  