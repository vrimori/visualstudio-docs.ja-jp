---
title: '方法: リボン グループにダイアログ ボックス起動ツールを追加'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2513113b473341f2ed099ef0c5ff5961694acb19
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548394"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>方法: リボン グループにダイアログ ボックス起動ツールを追加
  ダイアログ ボックス起動ツールは、リボン上の任意のグループに追加できます。 ダイアログ ボックス起動ツールは、グループに表示される小さなアイコンです。 ユーザーは、関連するダイアログ ボックスまたはグループに関連する他のオプションを提供する作業ウィンドウを開くには、このアイコンをクリックします。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>リボン グループにダイアログ ボックス起動ツールを追加するには  
  
1.  リボン コード ファイルを選択 (*.vb*または *.cs*ファイル) で**ソリューション エクスプ ローラー**です。  
  
2.  **ビュー**  メニューのをクリックして**デザイナー**です。  
  
3.  リボン デザイナーで任意のグループを右クリックし、をクリックして**追加 DialogBoxLauncher**です。  
  
     コードを追加して、<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick>カスタムまたは組み込みのダイアログ ボックスを開くグループのイベントです。  
  
## <a name="see-also"></a>関連項目  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [実行時にリボンにアクセスします。](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン オブジェクト モデルの概要](../vsto/ribbon-object-model-overview.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [方法: リボン デザイナーからリボン XML にエクスポート](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [方法: リボンのタブの位置を変更](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [方法: 組み込みタブをカスタマイズします。](../vsto/how-to-customize-a-built-in-tab.md)   
 [方法: コントロール backstage ビューを追加します。](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Outlook のリボンをカスタマイズします。](../vsto/customizing-a-ribbon-for-outlook.md)   
 [方法: リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [方法: アドインの表示は、ユーザー インターフェイス エラー](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [チュートリアル: リボン デザイナーを使用してカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル: 実行時にリボン上のコントロールを更新します。](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [チュートリアル: リボン XML によるカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  