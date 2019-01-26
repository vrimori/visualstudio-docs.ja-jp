---
title: '方法: Word 文書に XMLNode コントロールを追加します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1fc1f236604fa0ccd439756dc2c0b1368a534356
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868902"
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>方法: Word 文書に XMLNode コントロールを追加します。
  **重要な**に関する Microsoft Word には、このトピックでまとめられている情報が提示の特典および個人や組織のユーザーは、米国およびその担当地域外部にあるまたはを使用しているユーザーの使用専用、または開発上で実行されるプログラム、Microsoft が特定の機能の実装を削除する場合、2010 年 1 月の前に、Microsoft によってライセンスされた Microsoft Word の製品に関連するカスタム XML から Microsoft Word です。 Microsoft Word に関するこの情報が読み取りまたは個人または組織、米国またはその区域を使用して、または、2010 年 1 月 10 日後に Microsoft によってライセンス供与された Microsoft Word の製品で実行されるプログラムの開発で使用しない可能性があります。;これらの製品では、その日付より前にライセンスまたは購入を米国外の使用ライセンスの製品と同じ動作はしません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Visual Studio が自動的に追加の非繰り返しの XML スキーマ要素を Microsoft Office Word 文書にマップするときに、<xref:Microsoft.Office.Tools.Word.XMLNode>コントロールをドキュメント。 XML スキーマ要素の繰り返しのマッピングについては、次を参照してください。[方法。Word 文書に XMLNodes コントロールを追加](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)します。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNode>コントロールはから使用できません、**ツールボックス**または**データソース**ウィンドウをプログラムで作成することはできません。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnode-control-to-a-document"></a>文書に XMLNode コントロールを追加するには  
  
1.  リボンで、Visual Studio デザイナーで文書のクリックして、**開発者**タブ。  
  
    > [!NOTE]  
    >  **[開発]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、「[方法 :リボンの [開発] タブを表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)します。  
  
2.  **XML**グループで、**スキーマ**します。  
  
     **テンプレートとアドイン** ダイアログ ボックスが表示されます。  
  
3.  をクリックして、 **XML スキーマ**タブ。  
  
4.  クリックして**スキーマ追加**します。  
  
     **スキーマの追加** ダイアログ ボックスが表示されます。  
  
5.  非繰り返しスキーマ要素を含む XML スキーマの選択、**スキーマの追加** ダイアログ ボックスをクリックします**オープン**します。  
  
     **スキーマ設定** ダイアログ ボックスが表示されます。  
  
6.  エイリアスを割り当てるか、をクリックして**OK**エイリアスなしのスキーマを追加します。  
  
     スキーマを追加、**スキーマの追加** ダイアログ ボックス。  
  
7.  **スキーマの追加**ダイアログ ボックスで、をクリックして**OK**します。  
  
8.  **XML 構造**作業ウィンドウが開きます。  
  
9. 非繰り返しスキーマ要素のクリックして、 **XML 構造**作業ウィンドウ、ドキュメントに追加します。  
  
     <xref:Microsoft.Office.Tools.Word.XMLNode>コントロールが作成され、プロジェクトに追加します。  
  
## <a name="see-also"></a>関連項目  
 [XMLNode コントロール](../vsto/xmlnode-control.md)   
 [拡張オブジェクトを使用して Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
