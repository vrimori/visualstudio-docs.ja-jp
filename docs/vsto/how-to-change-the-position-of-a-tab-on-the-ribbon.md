---
title: "方法: リボンのタブの位置を変更する | Microsoft Docs"
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
  - "リボン [Visual Studio での Office 開発], タブ"
ms.assetid: 3f0906e3-9708-4136-ac49-986bc4c92ea4
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 方法: リボンのタブの位置を変更する
  **タブ コレクション エディター**を使用すると、リボンのカスタム タブの順序を変更できます。  リボン上の組み込みタブの前または後ろにカスタム タブを配置できます。  組み込みタブは、Microsoft Office アプリケーションのリボンに用意されているタブです。  たとえば、**\[データ\]** タブは、Excel の組み込みタブです。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### リボンのタブ オーダーを変更するには  
  
1.  **ソリューション エクスプローラー**でリボン コード ファイル \(.vb ファイルまたは .cs ファイル\) を選択します。  
  
2.  **\[表示\]** メニューの **\[デザイナー\]** をクリックします。  
  
3.  リボン デザイナーを右クリックし、**\[プロパティ\]** をクリックします。  
  
4.  **\[プロパティ\]** ウィンドウで、**\[Tabs\]** プロパティを選択し、省略記号ボタン \(![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.png "ASP.NET モバイル デザイナー楕円")\) ボタンをクリックします。  
  
     **タブ コレクション エディター**が表示されます。  
  
5.  **タブ コレクション エディター**の **\[メンバー\]** ボックスの一覧で、移動するタブを選択し、上向きまたは下向きの矢印をクリックして、タブ オーダーを変更します。  
  
### リボン上の組み込みタブの前または後ろにタブを配置するには  
  
1.  リボン デザイナーで、カスタム タブを選択します。  
  
2.  **\[プロパティ\]** のペインで、**\[ControlId\]** のプロパティを展開し、**\[ControlIdType\]** のプロパティの値が **\[カスタム\]**に設定されていることを確認します。  
  
3.  **\[プロパティ\]** ウィンドウで **\[Position\]** プロパティを展開します。  
  
4.  **\[PositionType\]** プロパティを適切な値に設定します。  
  
    -   **BeforeOfficeId** に設定すると、グループは指定の組み込みタブの前に配置されます。  
  
    -   **AfterOfficeId** に設定すると、グループは指定の組み込みタブの後ろに配置されます。  
  
5.  組み込みタブのコントロール ID に **OfficeId** プロパティを設定します。  
  
     コントロールIDの一覧については、[Office 2010ヘルプ ファイル: Office Fluentユーザー インターフェイスのコントロールID](http://go.microsoft.com/fwlink/?LinkID=181052)" "を参照してください。  
  
## 参照  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [チュートリアル : リボン デザイナーを使用したカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル : リボン XML によるカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  