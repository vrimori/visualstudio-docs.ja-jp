---
title: "方法 : リボン グループにダイアログ ボックス起動ツールを追加する"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ダイアログ ボックス起動ツール [Visual Studio での Office 開発]"
  - "リボン [Visual Studio での Office 開発], ダイアログ ボックス起動ツール"
ms.assetid: 5972664f-4e37-4dc6-90d0-69cedd057e60
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# 方法 : リボン グループにダイアログ ボックス起動ツールを追加する
  リボンの任意のグループにダイアログ ボックス起動ツールを追加できます。  ダイアログ ボックス起動ツールは、グループ内に表示される小さいアイコンです。  ユーザーがこのアイコンをクリックすると、関連付けられたダイアログ ボックスまたは作業ウィンドウが開き、そのグループに関連のある他のオプションが表示されます。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### リボン グループにダイアログ ボックス起動ツールを追加するには  
  
1.  **ソリューション エクスプローラー**でリボン コード ファイル \(.vb ファイルまたは .cs ファイル\) を選択します。  
  
2.  **\[表示\]** メニューの **\[デザイナー\]** をクリックします。  
  
3.  リボン デザイナーで、任意のグループを右クリックし、**\[DialogBoxLauncher の追加\]** をクリックします。  
  
     グループの <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> イベントにコードを追加し、カスタム ダイアログ ボックスまたは組み込みダイアログ ボックスを開きます。  
  
## 参照  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [実行時のリボンへのアクセス](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン オブジェクト モデルの概要](../vsto/ribbon-object-model-overview.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [方法 : リボンをリボン デザイナーからリボン XML にエクスポートする](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [方法: リボンのタブの位置を変更する](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [方法 : 組み込みタブをカスタマイズする](../vsto/how-to-customize-a-built-in-tab.md)   
 [方法: Backstage ビューにコントロールを追加する](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Outlook のリボンのカスタマイズ](../vsto/customizing-a-ribbon-for-outlook.md)   
 [方法 : リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [方法 : アドインのユーザー インターフェイス エラーを表示する](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [チュートリアル : リボン デザイナーを使用したカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル : 実行時のリボン コントロールの更新](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [チュートリアル : リボン XML によるカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  