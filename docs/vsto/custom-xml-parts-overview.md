---
title: "カスタム XML 部分の概要 |Microsoft ドキュメント"
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
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8dc3e4b1abc5f60f9ca63e374ab8870df6bb0d41
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="custom-xml-parts-overview"></a>Custom XML Parts Overview
  一部の Microsoft Office アプリケーションのドキュメントに XML データを埋め込むことができます。 データがという名前のドキュメントに XML データを埋め込む場合、*カスタム XML 部分*です。  
  
 Visual Studio で VSTO アドインまたはドキュメント レベルのソリューションを使用して、ドキュメントのカスタム XML 部分を作成または変更できます。 カスタム XML 部分を作成または変更するために Microsoft Office アプリケーションを開始する必要はありません。  
  
 **適用されます:** Excel、PowerPoint、および Word のドキュメント レベルのプロジェクトおよび VSTO アドイン プロジェクトに、このトピックの情報が適用されます。 詳細については、「 [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。  
  
> [!NOTE]  
>  Visual Studio では、ドキュメント レベルのカスタマイズ内のデータ オブジェクトをキャッシュすることもできます。 いくつかの類似点はありますが、この機能はカスタム XML 部分とは異なります。 詳細については、次を参照してください。[ドキュメント レベルのカスタマイズでキャッシュ データ](../vsto/cached-data-in-document-level-customizations.md)です。  
  
## <a name="understanding-custom-xml-parts"></a>カスタム XML 部分について  
 カスタム XML 部分は、2007 Microsoft Office system で Open XML 形式とともに導入されました。 これらの形式には Excel、PowerPoint、および Word 用の新しい XML ベースのファイル形式 (.xlsx、.pptx、.docx) が含まれます。 これらの形式のドキュメントは、XML ファイルで構成されます (とも呼ば*XML 部分*) ZIP アーカイブ内のフォルダーに編成されます。 XML 部分のほとんどは、ドキュメントの構造と状態を定義するのに役立つ組み込みの部分です。 ただし、ドキュメントにはカスタム XML 部分を含めることができ、ユーザーはこれを使用して、ドキュメントに任意の XML データを格納できます。  
  
 XML ファイル形式により、アプリケーションは古いバイナリ ファイル形式 ( .xls、.ppt、.doc) ではできない方法でドキュメントを操作できます。 ZIP アーカイブを読み取ることができるすべてのアプリケーションは、Microsoft Office がインストールされていない場合でも、ドキュメントの内容を検証し、変更できます。  
  
 Open XML およびカスタム XML 部分の構造の詳細については、次の記事をご覧ください。  
  
-   [Office (2007) Open XML ファイル形式の概要](http://msdn.microsoft.com/en-us/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [方法: Open XML 形式のドキュメントの操作](http://msdn.microsoft.com/en-us/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [チュートリアル: Word 2007 の XML の形式](http://msdn.microsoft.com/en-us/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [Open XML を使用して Word 2007 ドキュメントのビルドの書式します。](http://msdn.microsoft.com/en-us/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Excel、Word、および PowerPoint ではバイナリ ファイル形式で保存されているドキュメント内のカスタム XML 部分を使用することもできます。 ただし、バイナリ形式でドキュメントを保存する場合は、Microsoft Office アプリケーションを起動せずにカスタム XML 部分を追加または変更することはできません。  
  
## <a name="creating-and-modifying-custom-xml-parts"></a>カスタム XML 部分の作成および変更  
 ドキュメントが Office アプリケーションで開いているとき、またはドキュメントが閉じているとき (Microsoft Office がインストールされていない場合でも)、カスタム XML 部分を作成または変更できます。  
  
### <a name="modifying-xml-parts-while-the-office-application-is-running"></a>Office アプリケーションの実行中に、XML 部分を変更する  
 ドキュメント レベルのカスタマイズまたは VSTO アドインを使用して、カスタム XML 部分を操作できます。 ドキュメント レベルのカスタマイズを使用している場合は、通常、カスタマイズされたドキュメント内にあるカスタム XML 部分を操作します。 VSTO アドインを使用している場合は、アプリケーションで開いているすべてのドキュメントのカスタム XML 部分を作成、または変更できます。  
  
 Visual Studio を使用してカスタム XML 部分を作成するには、新しい <xref:Microsoft.Office.Core.CustomXMLPart> をドキュメントの <xref:Microsoft.Office.Core.CustomXMLParts> コレクションに追加します。 詳細については、次のトピックを参照してください。  
  
-   [方法: ドキュメント レベルのカスタマイズにカスタム XML 部分を追加する](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [方法: VSTO アドインを使用してドキュメントにカスタム XML 部分を追加する](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modifying-xml-parts-without-starting-the-office-application"></a>Office アプリケーション起動せずに XML 部分を変更する  
 Excel、PowerPoint、または Word を起動しないでカスタム XML 部分を変更できます。 これは、Microsoft Office アプリケーションがインストールされていないサーバーなどのコンピューターで、ドキュメント内の XML データを使用する場合に便利です。  
  
 Microsoft Office を起動せずにカスタム XML 部分を追加するには Open XML SDK のクラスを使用します。 これらのクラスは、Office ドキュメントに固有の Open XML コンテンツにアクセスするために設計されています。 たとえば、Excel ブックにカスタム XML 部分を追加するに使用する、 [AddNewPart\<T >](http://msdn.microsoft.com/en-us/47c348c0-77ab-a504-5097-bcd6a213921a)のメソッド、 [WorkbookPart](http://msdn.microsoft.com/en-us/d011e6f4-77dd-d02d-66ef-dc4a9e7b26f2)オブジェクト。 詳細については、次を参照してください。 [Open XML SDK 2.0](http://msdn.microsoft.com/en-us/f6a9ae68-7989-4208-97f5-3c945137a0ab)です。  
  
## <a name="binding-custom-xml-parts-to-word-content-controls"></a>Word のコンテンツ コントロールへのカスタム XML 部分のバインディング  
 Word ソリューションのコンテンツ コントロールをカスタム XML 部分の要素にバインドできます。 カスタム XML 部分にコンテンツ コントロールがバインドされると、カスタム XML 部分のデータがコンテンツ コントロールのユーザー インターフェイス (UI) に表示されます。 ユーザーがコントロール内のテキストを編集すると、対応する XML 要素が自動的に更新されます。 同様に、カスタム XML 部分の要素の値が変更されると、その XML 要素にバインドされているコンテンツ コントロールに新しいデータが表示されます。 詳細については、「 [Content Controls](../vsto/content-controls.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML スキーマとドキュメント レベルのカスタマイズ内のデータ](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [方法: ドキュメント レベルのカスタマイズにカスタム XML 部分を追加します。](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [方法: VSTO アドインを使用してドキュメントにカスタム XML 部分を追加](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [コンテンツ コントロール](../vsto/content-controls.md)   
 [チュートリアル: カスタム XML 部分へのコンテンツ コントロールのバインド](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  