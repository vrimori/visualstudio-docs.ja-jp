---
title: "方法 : 組み込みタブをカスタマイズする | Microsoft Docs"
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
  - "組み込みタブ [Visual Studio での Office 開発]"
  - "リボン [Visual Studio での Office 開発], タブ"
ms.assetid: 197a7aaa-a51d-496c-b904-b9421849fad9
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 方法 : 組み込みタブをカスタマイズする
  組み込みタブには、グループやコントロールを追加できます。  組み込みタブは、Microsoft Office アプリケーションのリボンに用意されているタブです。  たとえば、**\[データ\]** タブは、Excel の組み込みタブです。  カスタム グループを作成すると、そのグループはタブの最後に表示されますが、タブ上のどこにでも移動できます。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  組み込みタブにグループを追加することはできますが、組み込みタブから組み込みグループを削除することはできません。  
  
### 組み込みタブにグループを追加するには  
  
1.  **ソリューション エクスプローラー**で、リボンのコード ファイルを右クリックし、**\[デザイナーの表示\]** をクリックします。  
  
    > [!NOTE]  
    >  リボン コード ファイルが**ソリューション エクスプローラー**に表示されない場合は、**リボン項目**をプロジェクトに追加する必要があります。  「[方法 : リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)」を参照してください。  
  
2.  リボン デザイナーで、任意のタブを右クリックし、**\[プロパティ\]** をクリックします。  
  
3.  **\[プロパティ\]** ウィンドウで、**\[ControlId\]** プロパティを展開し、**\[ControlIdType\]** プロパティを **Office** に設定します。  
  
4.  **OfficeId** プロパティを、カスタマイズする組み込みタブの*コントロール ID* に設定します。  
  
     コントロール ID は、Microsoft Office アプリケーションに組み込まれているタブ、グループ、コントロールを一意に識別する名前です。  
  
     コントロール ID の一覧については、「[Office 2010 ヘルプ ファイル: Office Fluent ユーザー インターフェイスのコントロール ID](http://go.microsoft.com/fwlink/?LinkID=181052)」を参照してください。  
  
5.  **ツールボックス**の **\[Office リボン コントロール\]** タブから、グループをタブにドラッグします。  
  
    > [!NOTE]  
    >  組み込みグループは、デザイナーには表示されません。  したがって、操作しているのが組み込みタブであるかどうかを判断するには、タブの **ControlId** プロパティを調べる方法しかありません。  
  
### 組み込みタブ上でグループを配置するには  
  
1.  リボン デザイナーで、カスタム グループを選択します。  
  
2.  **\[プロパティ\]** ウィンドウで **\[Position\]** プロパティを展開します。  
  
3.  **\[PositionType\]** プロパティを適切な値に設定します。  
  
    -   **BeforeOfficeId** に設定すると、グループは指定の組み込みグループの前に配置されます。  
  
    -   **AfterOfficeId** に設定すると、グループは指定の組み込みグループの後ろに配置されます。  
  
4.  組み込みグループのコントロール ID に **OfficeId** プロパティを設定します。  
  
     コントロール ID の一覧については、「[Office 2010 ヘルプ ファイル: Office Fluent ユーザー インターフェイスのコントロール ID](http://go.microsoft.com/fwlink/?LinkID=181052)」を参照してください。  
  
## 参照  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [チュートリアル : リボン デザイナーを使用したカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル : リボン XML によるカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [方法 : リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [方法: リボンのタブの位置を変更する](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [方法: Backstage ビューにコントロールを追加する](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [方法 : アドインのユーザー インターフェイス エラーを表示する](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  