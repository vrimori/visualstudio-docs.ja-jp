---
title: '方法: Visual Studio 内でワークシートにスキーマを割り当てる'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1be044131ab7248e971e5030f0d35467773587e1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849930"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>方法: Visual Studio 内でワークシートにスキーマを割り当てる
  ワークシートが Visual Studio で開いている間は、ワークシートに XML スキーマをマップできます。 ブックが Visual Studio の外部で開いているときに使用するのと同じ Microsoft Office Excel ツールを使用するとします。 Office プロジェクトは、前に、ワークシートにスキーマをマップするかどうか、または Excel ソリューションを作成した後に、同じオブジェクトを作成します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Excel ソリューションでは、マルチパートの XML スキーマを使用できません。  
  
## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>XML スキーマを Visual Studio で Excel ワークシートにマップするには  
  
1.  Visual Studio 内で Excel ブックまたはテンプレート プロジェクトを開きます。  
  
2.  デザイナーにフォーカスを移動するワークシートをクリックします。  
  
3.  リボンの **[開発]** タブをクリックします。  
  
    > [!NOTE]  
    >  **[開発]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、「[方法 :リボンの [開発] タブを表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)します。  
  
4.  **XML**グループで、**ソース**します。  
  
     **XML ソース**ウィンドウが開きます。  
  
5.  **XML ソース**ウィンドウで、をクリックして**XML マップ**します。  
  
     **XML マップ** ダイアログ ボックスが表示されます。  
  
6.  **XML マップ**ダイアログ ボックスで、をクリックして**追加**します。  
  
7.  スキーマ ファイルを参照、それを選択してクリックして**オープン**します。  
  
8.  **[OK]** をクリックします。  
  
     表される、スキーマ、 **XML ソース**ウィンドウ。 プロジェクトで、型指定された<xref:System.Data.DataSet>スキーマに基づいて生成されると、<xref:System.Windows.Forms.BindingSource>が作成されます。  
  
9. 要素をドラッグして、 **XML ソース**対応するコントロールを作成する、ワークシート内の場所にウィンドウ。  
  
     Office プロジェクトで生成される非繰り返しスキーマ要素をドラッグする場合、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>に自動的にバインドされているコントロール、<xref:System.Windows.Forms.BindingSource>します。  
  
     Office プロジェクトで生成される繰り返しスキーマ要素をドラッグする場合、<xref:Microsoft.Office.Tools.Excel.ListObject>データ ソースに自動的にバインドされていないコントロール。 詳細については、次を参照してください。 [XML スキーマとデータをドキュメント レベルのカスタマイズ](../vsto/xml-schemas-and-data-in-document-level-customizations.md)します。  
  
## <a name="see-also"></a>関連項目  
 [方法: Visual Studio 内で Word 文書にスキーマを割り当てる](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [ドキュメント レベルのカスタマイズにおける XML スキーマとデータ](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
