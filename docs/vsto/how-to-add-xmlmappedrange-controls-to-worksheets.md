---
title: "方法: ワークシートに XMLMappedRange コントロールを追加する |Microsoft ドキュメント"
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
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 90050da5f5105ab3be4c42bedb1751d9f1664958
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>方法 : ワークシートに XMLMappedRange コントロールを追加する
  Microsoft Office Excel のセルに XML 要素をマップすると、Visual Studio は自動的に追加、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>をワークシートにコントロールできます。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールでは使用できません、**ツールボックス**または**データソース**ウィンドウです。 また、作成することはできません<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>プログラムで制御します。  
  
### <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>ワークシートに XMLMappedRange コントロールを追加するには  
  
1.  Visual Studio デザイナーで Excel ブックを開きます。  
  
2.  コントロールを追加するワークシートを開きます。  
  
3.  **開発者** タブで、をクリックして**ソース**です。  
  
    > [!NOTE]  
    >  場合、**開発者** タブがリボンに表示されていない、有効にする必要があります。 詳細については、「 [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)」を参照してください。  
  
     **XML ソース**タスク ウィンドウが表示されます。  
  
4.  **XML ソース**タスク ウィンドウで、をクリックして**XML マップ**です。  
  
5.  **XML マップ**ダイアログ ボックスで、をクリックして**追加**です。  
  
     **XML ソース** ダイアログ ボックスが表示されます。  
  
6.  XML スキーマを選択、 **XML ソース** ダイアログ ボックスをクリック**開く**です。  
  
     スキーマを追加、 **XML マップ** ダイアログ ボックス。  
  
7.  **XML マップ**ダイアログ ボックスで、をクリックして**OK**です。  
  
8.  要素をドラッグ、 **XML ソース**ワークシートのセルに作業ウィンドウ。  
  
     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>が作成され、プロジェクトに追加します。  
  
    > [!NOTE]  
    >  親要素をドラッグする場合、 **XML ソース**タスク ウィンドウで、<xref:Microsoft.Office.Tools.Excel.ListObject>コントロールを作成します。  
  
## <a name="see-also"></a>参照  
 [XmlMappedRange コントロール](../vsto/xmlmappedrange-control.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [方法: Visual Studio 内でワークシートにスキーマを割り当てる](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  