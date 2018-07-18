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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55b6c83624c3ccb6c28701cd97753ea155e37288
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263981"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>方法: ワークシートに XMLMappedRange コントロールを追加します。
  Microsoft Office Excel のセルに XML 要素をマップすると、Visual Studio は自動的に追加、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>をワークシートにコントロールできます。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールでは使用できません、**ツールボックス**または**データソース**ウィンドウです。 また、作成することはできません<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>プログラムで制御します。  
  
## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>ワークシートに XMLMappedRange コントロールを追加するには  
  
1.  Visual Studio デザイナーで Excel ブックを開きます。  
  
2.  コントロールを追加するワークシートを開きます。  
  
3.  **開発者** タブで、をクリックして**ソース**です。  
  
    > [!NOTE]  
    >  場合、**開発者** タブがリボンに表示されていない、有効にする必要があります。 詳細については、次を参照してください。[する方法: [開発] タブをリボンに表示](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)です。  
  
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
  
## <a name="see-also"></a>関連項目  
 [XmlMappedRange コントロール](../vsto/xmlmappedrange-control.md)   
 [拡張オブジェクトによる Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [方法: Visual Studio 内のワークシートにスキーマのマッピング](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  