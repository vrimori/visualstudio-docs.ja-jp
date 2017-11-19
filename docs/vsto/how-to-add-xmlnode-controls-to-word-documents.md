---
title: "方法: Word 文書に XMLNode コントロールを追加する |Microsoft ドキュメント"
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
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
ms.assetid: d583b9d4-bd13-46e3-9eb7-da18fcb7eb8c
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a24f5b4205a558e950a7fe941ac6f8a3e7c45068
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>方法 : Word 文書に XMLNode コントロールを追加する
  **重要な**Microsoft Word に関するこのトピックに設定された情報が、利点と個人ユーザーおよびユーザーは、米国およびその区域外部にあるまたはを使用しているユーザーは、組織の使用専用に示された、または開発上で実行されるプログラム、Microsoft が特定の機能の実装を削除する場合、2010 年 1 月前に Microsoft によってライセンス供与された Microsoft Word 製品に関連するカスタムの XML から Microsoft Word。 Microsoft Word に関する情報はこの可能性がありますいない読み取りまたは個人または米国またはその区域、2010 年 1 月 10 日後に Microsoft によってライセンス供与された Microsoft Word 製品上で実行されるプログラムの開発を使用して、ユーザーの組織で使用されます。;これらの製品では、その日付の前にライセンスまたは購入し、米国外の利用に対してライセンス供与の製品と同じ動作がしません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Microsoft Office Word 文書に非繰り返しの XML スキーマ要素をマップすると、Visual Studio は自動的に追加、<xref:Microsoft.Office.Tools.Word.XMLNode>をドキュメントにコントロールできます。 XML スキーマ要素の繰り返しのマッピングについては、次を参照してください。[する方法: Word 文書に XMLNodes コントロールを追加](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)です。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNode>コントロールからは使用できない、**ツールボックス**または**データソース**ウィンドウをプログラムで作成することはできません。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnode-control-to-a-document"></a>文書に XMLNode コントロールを追加するには  
  
1.  リボンで、Visual Studio デザイナーで、ドキュメント内をクリックして、**開発者**タブです。  
  
    > [!NOTE]  
    >  **[開発]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、「 [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)」を参照してください。  
  
2.  **XML**グループで、**スキーマ**です。  
  
     **テンプレートとアドイン** ダイアログ ボックスが表示されます。  
  
3.  クリックして、 **XML スキーマ**タブです。  
  
4.  をクリックして**スキーマを追加**です。  
  
     **スキーマの追加** ダイアログ ボックスが表示されます。  
  
5.  非繰り返しのスキーマ要素を格納する XML スキーマを選択、**スキーマの追加** ダイアログ ボックスをクリック**開く**です。  
  
     **スキーマ設定** ダイアログ ボックスが表示されます。  
  
6.  エイリアスを割り当てるかをクリックして**OK**エイリアスがなければ、スキーマを追加します。  
  
     スキーマを追加、**スキーマの追加** ダイアログ ボックス。  
  
7.  **スキーマの追加**ダイアログ ボックスで、をクリックして**OK**です。  
  
8.  **XML 構造**作業ウィンドウが表示されます。  
  
9. スキーマの非繰り返し要素をクリックして、 **XML 構造**ドキュメントに追加する作業ウィンドウ。  
  
     <xref:Microsoft.Office.Tools.Word.XMLNode>コントロールが作成され、プロジェクトに追加します。  
  
## <a name="see-also"></a>関連項目  
 [XMLNode コントロール](../vsto/xmlnode-control.md)   
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  