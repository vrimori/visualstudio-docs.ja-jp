---
title: '方法: ワークシートに XMLMappedRange コントロールを追加します。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d7cc26c0170c2a20e27026ebcbc6d8705d34ce2
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646717"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>方法: ワークシートに XMLMappedRange コントロールを追加します。
  Microsoft Office Excel のセルに XML 要素をマップすると、Visual Studio は自動的に追加、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールをワークシートにします。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールでは使用できません、**ツールボックス**または**データソース**ウィンドウ。 さらに、作成することはできません<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>プログラムで制御します。  
  
## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>ワークシートに XMLMappedRange コントロールを追加するには  
  
1.  Visual Studio デザイナーで Excel ブックを開きます。  
  
2.  コントロールを追加するワークシートを開きます。  
  
3.  **開発者**] タブで [**ソース**します。  
  
    > [!NOTE]  
    >  場合、**開発者**タブがリボンに表示されない、有効にする必要があります。 詳細については、「[方法 :リボンの [開発] タブを表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)します。  
  
     **XML ソース**タスク ウィンドウが表示されます。  
  
4.  **XML ソース**タスク ウィンドウで、をクリックして**XML マップ**します。  
  
5.  **XML マップ**ダイアログ ボックスで、をクリックして**追加**します。  
  
     **XML ソース** ダイアログ ボックスが表示されます。  
  
6.  XML スキーマを選択、 **XML ソース** ダイアログ ボックスをクリックします**オープン**します。  
  
     スキーマを追加、 **XML マップ** ダイアログ ボックス。  
  
7.  **XML マップ**ダイアログ ボックスで、をクリックして**OK**。  
  
8.  要素をドラッグ、 **XML ソース**ワークシートのセルに作業ウィンドウ。  
  
     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>が作成され、プロジェクトに追加します。  
  
    > [!NOTE]  
    >  親要素をドラッグする場合、 **XML ソース** 作業ウィンドウ、<xref:Microsoft.Office.Tools.Excel.ListObject>コントロールが作成されます。  
  
## <a name="see-also"></a>関連項目  
 [XmlMappedRange コントロール](../vsto/xmlmappedrange-control.md)   
 [拡張オブジェクトを使用して Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [方法: Visual Studio 内でワークシートにスキーマを割り当てる](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  