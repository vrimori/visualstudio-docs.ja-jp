---
title: '方法: Visual Studio 内で Word 文書にスキーマを割り当てる'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 574f67343bfd2ef7319c1571e84703c4bbf5fe3e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867690"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>方法: Visual Studio 内で Word 文書にスキーマを割り当てる
  **重要な**に関する Microsoft Word には、このトピックでまとめられている情報が提示の特典および個人や組織のユーザーは、米国およびその担当地域外部にあるまたはを使用しているユーザーの使用専用、または開発上で実行されるプログラム、Microsoft が特定の機能の実装を削除する場合、2010 年 1 月の前に、Microsoft によってライセンスされた Microsoft Word の製品に関連するカスタム XML から Microsoft Word です。 Microsoft Word に関するこの情報が読み取りまたは個人または組織、米国またはその区域を使用して、または、2010 年 1 月 10 日後に Microsoft によってライセンス供与された Microsoft Word の製品で実行されるプログラムの開発で使用しない可能性があります。;これらの製品では、その日付より前にライセンスまたは購入を米国外の使用ライセンスの製品と同じ動作はしません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 文書が Visual Studio で開いている間は、ドキュメントに XML スキーマをマップできます。 ドキュメントを Visual Studio の外部で開いているときに使用する Microsoft Office Word のと同じツールを使用するとします。 Office プロジェクトは、前に、ドキュメントにスキーマをマップするかどうか、または Word ソリューションを作成した後に、同じオブジェクトを作成します。  
  
## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Visual Studio で Word 文書に XML スキーマをマップするには  
  
1.  Visual Studio 内で Word 文書またはテンプレート プロジェクトを開きます。  
  
2.  デザイナーにフォーカスを移動するためにドキュメントをクリックします。  
  
3.  リボンのクリックして、**開発者**タブ。  
  
    > [!NOTE]  
    >  **[開発]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、「[方法 :リボンの [開発] タブを表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)します。  
  
4.  **XML**グループで、**スキーマ**します。  
  
     **テンプレートとアドイン** ダイアログ ボックスが表示されます。  
  
5.  をクリックして、 **XML スキーマ**タブ。  
  
6.  クリックして**スキーマ追加**します。  
  
     **スキーマの追加** ダイアログ ボックスが表示されます。  
  
7.  スキーマ ファイルを参照、それを選択してクリックして**オープン**します。  
  
     **スキーマ設定** ダイアログ ボックスが表示されます。  
  
8.  エイリアスを割り当てるか、をクリックして**OK**エイリアスなしのスキーマを追加します。  
  
9. **[OK]** をクリックします。  
  
     **XML 構造**ウィンドウが開きます。  
  
10. 要素をドラッグして、 **XML 構造**対応するコントロールを作成するドキュメント内の場所にウィンドウ。  
  
## <a name="see-also"></a>関連項目  
 [方法: Visual Studio 内でワークシートにスキーマを割り当てる](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [ドキュメント レベルのカスタマイズにおける XML スキーマとデータ](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
