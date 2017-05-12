---
title: "方法: SharePoint アプリケーション ページまたは Web パーツのユーザー コントロールを作成する"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ユーザー コントロール [Visual Studio での SharePoint 開発], 追加"
  - "ユーザー コントロール [Visual Studio での SharePoint 開発], 作成"
ms.assetid: 492ea376-7188-4b5a-a2eb-adc0e3f51484
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 方法: SharePoint アプリケーション ページまたは Web パーツのユーザー コントロールを作成する
  SharePoint ソリューション向けの独自の機能を備えたカスタム ユーザー コントロールを作成し、その機能をプロジェクト内で再利用することができます。  ユーザー コントロールは、Web パーツまたはアプリケーション ページに含めることができます。他の ASP.NET コントロールや SharePoint コントロールを追加し、コントロールのプロパティとメソッドを定義することもできます。  ユーザー コントロールの詳細については、「[Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)」および「[User Controls and Server Controls in SharePoint \(SharePoint のユーザー コントロールとサーバー コントロール\)](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx)」を参照してください。  
  
### SharePoint のユーザー コントロールを作成するには  
  
1.  Visual Studio で、SharePoint プロジェクトを開くか作成します。  
  
     「[SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)」を参照してください。  
  
2.  **ソリューション エクスプローラー**で、プロジェクト ノードを選択します。  
  
3.  メニュー バーで **\[プロジェクト\]**、**\[新しい項目の追加\]** の順に選択します。  
  
     **\[新しい項目の追加\]** ダイアログ ボックスが表示されます。  
  
4.  **\[インストール済み\]** ペインで、**\[Office\/SharePoint\]** ノードを選択します。  
  
5.  SharePoint テンプレートの一覧で、**\[ユーザー コントロール \(ファーム ソリューションのみ\)\]** を選択します。  
  
    > [!NOTE]  
    >  ユーザー コントロールはファーム ソリューションでのみ機能します。  
  
6.  **\[名前\]** ボックスにユーザー コントロールの名前を入力し、**\[追加\]** をクリックします。  
  
     複数のフォルダーとファイルがプロジェクトに追加されます。  これらのファイルの詳細については、「[Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)」を参照してください。  
  
     既定で、Visual Web Developer デザイナーの**ソース** ビューにユーザー コントロール ファイルが表示されます。  このビューで、コントロールの XML マークアップを編集できます。  **ツールボックス**からコントロールをドラッグしてコントロールを視覚的にデザインする場合は、**デザイン** ビューに切り替えます。  「[NIB: Design View, Web Page Designer](http://msdn.microsoft.com/ja-jp/d8f2270a-357d-40a4-9b39-1a3f2366216d)」を参照してください。  
  
7.  コントロールで発生するイベントを処理する場合は、ユーザー コントロールのコード ファイルにコードを追加します。  
  
     このファイルは、**ソリューション エクスプローラー**のユーザー コントロール ファイルの下に表示されます。コード ファイルの拡張子は .cs または .vs です \(プロジェクトの言語によって異なります\)。  
  
## 参照  
 [Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [SharePoint のアプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
  