---
title: "方法: Backstage ビューにコントロールを追加する | Microsoft Docs"
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
  - "コントロール, リボン"
  - "カスタム リボン, メニュー"
  - "カスタマイズ (リボンを), メニュー"
  - "メニュー, カスタマイズ"
  - "Microsoft Office ボタン"
  - "Microsoft Office メニュー"
  - "Office ボタン"
  - "リボン, カスタマイズ"
  - "リボン, メニュー"
ms.assetid: 4fda1278-9aea-4d54-928a-269a81584494
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 方法: Backstage ビューにコントロールを追加する
  **\[ファイル\]** のタブをクリックしたときに表示されるメニューにコントロールを追加するには、リボン デザイナーを使用できます。  アプリケーションを実行するときは、**\[ファイル\]** のタブに追加したコントロールは **\[アドイン\]**という名前のグループ表示されます。  
  
 組み込みコントロールの前または後にVisual Studioのリボン デザイナーを使用してコントロールを配置することはできません。  組み込みコントロールは、Backstageビューで既に表示されるコントロールです。  組み込みコントロールの前または後ろにコントロールを配置するには、リボン XML を使用する必要があります。  **\[リボン \(XML\)\]**に関する詳細については、[リボン XML](../vsto/ribbon-xml.md)を参照してください。  Backstage ビューのカスタマイズ方法の詳細については、「[Introduction to the Office 2010 Backstage View for Developers \(開発者向け Office 2010 Backstage ビューの概要\)](http://go.microsoft.com/fwlink/?LinkId=182189)」および「[Customizing the Office 2010 Backstage View for Developers \(Office 2010 Backstage ビューをカスタマイズする \(開発者向け\)\)](http://go.microsoft.com/fwlink/?LinkId=182188)」を参照してください。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Backstageビューにコントロールを追加するには  
  
1.  デザイン ビューでリボン項目を開きます。  
  
     プロジェクトに **\[リボン \(ビジュアル デザイナー\)\]** 項目を追加する方法の詳細については、「[方法 : リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)」を参照してください。  
  
2.  リボン デザイナーで、**\[ファイル\]** のタブをクリックします。  
  
     メニュー デザイナーが表示されます。  このデザイン サーフェイスにコントロールは含まれていません。  
  
3.  **\[ツールボックス\]** の **\[Office リボン コントロール\]** タブから、次に挙げるコントロールの中から任意のものをメニュー デザイナーにドラッグします。  
  
    -   ボタン  
  
    -   CheckBox  
  
    -   Gallery  
  
    -   メニュー  
  
    -   \[Separator\]  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  コントロールをドラッグし、メニュー上の新しい位置に移動します。  
  
## 参照  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [方法 : リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [チュートリアル : リボン デザイナーを使用したカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  