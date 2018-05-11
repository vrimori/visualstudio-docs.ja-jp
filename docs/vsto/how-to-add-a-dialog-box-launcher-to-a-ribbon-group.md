---
title: '方法: リボン グループにダイアログ ボックス起動ツールを追加 |Microsoft ドキュメント'
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
ms.openlocfilehash: d71124d0a3843053ad7558e0e1038b8d6626b5e1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>方法 : リボン グループにダイアログ ボックス起動ツールを追加する
  ダイアログ ボックス起動ツールは、リボン上の任意のグループに追加できます。 ダイアログ ボックス起動ツールは、グループに表示される小さなアイコンです。 ユーザーは、関連するダイアログ ボックスまたはグループに関連する他のオプションを提供する作業ウィンドウを開くには、このアイコンをクリックします。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>リボン グループにダイアログ ボックス起動ツールを追加するには  
  
1.  リボン コード ファイル (.vb または .cs ファイル) を選択**ソリューション エクスプ ローラー**です。  
  
2.  **ビュー**  メニューのをクリックして**デザイナー**です。  
  
3.  リボン デザイナーで任意のグループを右クリックし、をクリックして**追加 DialogBoxLauncher**です。  
  
     コードを追加して、<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick>カスタムまたは組み込みのダイアログ ボックスを開くグループのイベントです。  
  
## <a name="see-also"></a>関連項目  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン オブジェクト モデルの概要](../vsto/ribbon-object-model-overview.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [方法: リボン デザイナーからリボン XML にエクスポート](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [方法: リボンのタブの位置を変更](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [方法: 組み込みタブをカスタマイズします。](../vsto/how-to-customize-a-built-in-tab.md)   
 [方法: コントロール Backstage ビューを追加します。](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Outlook のリボンのカスタマイズ](../vsto/customizing-a-ribbon-for-outlook.md)   
 [方法: リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [方法: アドイン ユーザー インターフェイス エラーを表示します。](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [チュートリアル: リボン デザイナーを使用してカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル: 実行時にリボン コントロールの更新](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [チュートリアル: リボン XML によるカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  