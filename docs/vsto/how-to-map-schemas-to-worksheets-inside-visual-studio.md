---
title: '方法: Visual Studio 内のワークシートにスキーマをマップ |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b2d0caadfc08d7fa1d2ea29d04e84a5d954a42fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>方法 : Visual Studio 内でワークシートにスキーマを割り当てる
  ワークシートが Visual Studio で開いている間は、ワークシートに XML スキーマをマップできます。 ブックが Visual Studio の外部で開いているときに使用するのと同じ Microsoft Office Excel ツールを使用するとします。 Office プロジェクトは、前に、ワークシートにスキーマをマップするかどうか、または、Excel ソリューションを作成した後に、同じオブジェクトを作成します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Excel ソリューションでマルチパートの XML スキーマを使用することはできません。  
  
### <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Visual Studio で Excel ワークシートに XML スキーマをマップするには  
  
1.  Visual Studio 内の Excel ブックまたはテンプレート プロジェクトを開きます。  
  
2.  デザイナーにフォーカスを移動するワークシートをクリックします。  
  
3.  リボンの **[開発]** タブをクリックします。  
  
    > [!NOTE]  
    >  **[開発]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、「 [方法 : [開発] タブをリボンに表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)」を参照してください。  
  
4.  **XML**グループで、**ソース**です。  
  
     **XML ソース**ウィンドウが開きます。  
  
5.  **XML ソース**ウィンドウで、をクリックして**XML マップ**です。  
  
     **XML マップ** ダイアログ ボックスが表示されます。  
  
6.  **XML マップ**ダイアログ ボックスで、をクリックして**追加**です。  
  
7.  スキーマは、ファイルを参照、選択し、をクリックして**開く**です。  
  
8.  **[OK]**をクリックします。  
  
     スキーマで表される、 **XML ソース**ウィンドウです。 プロジェクトで、型指定された<xref:System.Data.DataSet>は、スキーマに基づいて生成と<xref:System.Windows.Forms.BindingSource>を作成します。  
  
9. 要素をドラッグして、 **XML ソース**対応するコントロールを作成する場合、ワークシート内の場所にウィンドウです。  
  
     Office プロジェクトで生成される繰り返しのないスキーマ要素をドラッグする場合、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>に自動的にバインドされているコントロール、<xref:System.Windows.Forms.BindingSource>です。  
  
     Office プロジェクトで生成される繰り返しスキーマ要素をドラッグする場合、<xref:Microsoft.Office.Tools.Excel.ListObject>コントロールをデータ ソースに自動的にバインドされていません。 詳細については、次を参照してください。 [XML スキーマとドキュメント レベルのカスタマイズでデータ](../vsto/xml-schemas-and-data-in-document-level-customizations.md)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: Visual Studio 内で Word 文書にスキーマをマップ](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [ドキュメント レベルのカスタマイズにおける XML スキーマとデータ](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  