---
title: '方法: Visual Studio 内で Word 文書にスキーマをマップ |Microsoft ドキュメント'
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
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 629149eab19dbd717cdc663a58a53659ae18a4af
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>方法 : Visual Studio 内で Word 文書にスキーマを割り当てる
  **重要な**Microsoft Word に関するこのトピックに設定された情報が、利点と個人ユーザーおよびユーザーは、米国およびその区域外部にあるまたはを使用しているユーザーは、組織の使用専用に示された、または開発上で実行されるプログラム、Microsoft が特定の機能の実装を削除する場合、2010 年 1 月前に Microsoft によってライセンス供与された Microsoft Word 製品に関連するカスタムの XML から Microsoft Word。 Microsoft Word に関する情報はこの可能性がありますいない読み取りまたは個人または米国またはその区域、2010 年 1 月 10 日後に Microsoft によってライセンス供与された Microsoft Word 製品上で実行されるプログラムの開発を使用して、ユーザーの組織で使用されます。;これらの製品では、その日付の前にライセンスまたは購入し、米国外の利用に対してライセンス供与の製品と同じ動作がしません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 文書が Visual Studio で開いている間は、ドキュメントに XML スキーマをマップできます。 ドキュメントを Visual Studio の外部で開いているときに使用するのと同じ Microsoft Office Word ツールを使用するとします。 Office プロジェクトは、前に文書にスキーマをマップするかどうか、または Word ソリューションを作成した後に、同じオブジェクトを作成します。  
  
### <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Visual Studio で Word 文書に XML スキーマをマップするには  
  
1.  Visual Studio で Word 文書またはテンプレート プロジェクトを開きます。  
  
2.  デザイナーにフォーカスを移動先のドキュメント内をクリックします。  
  
3.  リボンの **[開発]** タブをクリックします。  
  
    > [!NOTE]  
    >  **[開発]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、「 [方法 : [開発] タブをリボンに表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)」を参照してください。  
  
4.  **XML**グループで、**スキーマ**です。  
  
     **テンプレートとアドイン** ダイアログ ボックスが表示されます。  
  
5.  クリックして、 **XML スキーマ**タブです。  
  
6.  をクリックして**スキーマを追加**です。  
  
     **スキーマの追加** ダイアログ ボックスが表示されます。  
  
7.  スキーマは、ファイルを参照、選択し、をクリックして**開く**です。  
  
     **スキーマ設定** ダイアログ ボックスが表示されます。  
  
8.  エイリアスを割り当てるかをクリックして**OK**エイリアスがなければ、スキーマを追加します。  
  
9. **[OK]**をクリックします。  
  
     **XML 構造**ウィンドウが開きます。  
  
10. 要素をドラッグして、 **XML 構造**対応するコントロールを作成する場合、ドキュメント内の場所にウィンドウです。  
  
## <a name="see-also"></a>関連項目  
 [方法: Visual Studio 内のワークシートにスキーマのマッピング](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [ドキュメント レベルのカスタマイズにおける XML スキーマとデータ](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  