---
title: '方法: Word 文書に XMLNodes コントロールを追加'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ff7a1966c9107fcd2a60b14c21b6a2dfbda09033
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258071"
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>方法: Word 文書に XMLNodes コントロールを追加
  **重要な**に関する Microsoft Word には、このトピックでまとめられている情報が提示の特典および個人や組織のユーザーは、米国およびその担当地域外部にあるまたはを使用しているユーザーの使用専用、または開発上で実行されるプログラム、Microsoft が特定の機能の実装を削除する場合、2010 年 1 月の前に、Microsoft によってライセンスされた Microsoft Word の製品に関連するカスタム XML から Microsoft Word です。 Microsoft Word に関するこの情報が読み取りまたは個人または組織、米国またはその区域を使用して、または、2010 年 1 月 10 日後に Microsoft によってライセンス供与された Microsoft Word の製品で実行されるプログラムの開発で使用しない可能性があります。;これらの製品では、その日付より前にライセンスまたは購入を米国外の使用ライセンスの製品と同じ動作はしません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Microsoft Office Word 文書に繰り返される XML スキーマ要素をマップすると、Visual Studio は自動的に追加、<xref:Microsoft.Office.Tools.Word.XMLNodes>コントロールをドキュメント。  
  
 XML スキーマ要素の非繰り返しのマッピングについては、次を参照してください。[方法: Word 文書にコントロールを追加 XMLNode](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)します。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNodes>コントロールはから使用できません、**ツールボックス**または**データ ソース**ウィンドウで、また、プログラムで作成します。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnodes-control-to-a-document"></a>文書に XMLNodes コントロールを追加するには  
  
1.  リボンで、Visual Studio デザイナーで文書のクリックして、**開発者**タブ。  
  
    > [!NOTE]  
    >  **[開発]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、次を参照してください。[方法: リボンの [開発] タブを表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)します。  
  
2.  **XML**グループで、**スキーマ**します。  
  
     **テンプレートとアドイン** ダイアログ ボックスが表示されます。  
  
3.  をクリックして、 **XML スキーマ**タブ。  
  
4.  クリックして**スキーマ追加**します。  
  
     **スキーマの追加** ダイアログ ボックスが表示されます。  
  
5.  繰り返しのスキーマの要素とクリックを含む XML スキーマを選択します。**オープン**します。  
  
     **スキーマ設定** ダイアログ ボックスが表示されます。  
  
6.  エイリアスを割り当てるか、をクリックして**OK**エイリアスなしのスキーマを追加します。  
  
     スキーマを追加、**スキーマの追加** ダイアログ ボックス。  
  
7.  **スキーマの追加**ダイアログ ボックスで、をクリックして**OK**します。  
  
     **XML 構造**作業ウィンドウが開きます。  
  
8.  繰り返されるスキーマ要素をクリックして、 **XML 構造**作業ウィンドウ、ドキュメントに追加します。  
  
     <xref:Microsoft.Office.Tools.Word.XMLNodes>コントロールが作成され、プロジェクトに追加します。  
  
## <a name="see-also"></a>関連項目  
 [XMLNodes コントロール](../vsto/xmlnodes-control.md)   
 [拡張オブジェクトを使用して Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  