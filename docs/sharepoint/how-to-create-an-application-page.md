---
title: "方法: アプリケーション ページを作成する"
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
  - "アプリケーション ページ [Visual Studio での SharePoint 開発], 追加"
  - "アプリケーション ページ [Visual Studio での SharePoint 開発], 作成"
ms.assetid: 9ad7044a-2fa7-4bba-8f25-b9f2cc1b7c6b
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 方法: アプリケーション ページを作成する
  一つまたは複数の SharePoint サイトの ASP.NET Web ページを作成できます。  SharePoint では、このようなページのことをアプリケーション ページと呼びます。  サイト ページとは異なり、アプリケーション ページには、ページとは分離して実行されるコードが含まれます。  詳細については、「[SharePoint のアプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)」を参照してください。  
  
### アプリケーション ページを作成するには  
  
1.  Visual Studio で、SharePoint プロジェクトを開くか作成します。  
  
     詳細については、「[SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)」を参照してください。  
  
2.  **ソリューション エクスプローラー**で、プロジェクト ノードを選択します。  
  
3.  メニュー バーで **\[プロジェクト\]**、**\[新しい項目の追加\]** の順に選択します。  
  
4.  **\[新しいアイテムの追加\]** ダイアログ ボックスで、**\[SharePoint\]** ノードを展開し、**2010** 項目を選択します。  
  
5.  SharePoint テンプレートの一覧で、**\[アプリケーション ページ\]** をクリックします。  
  
6.  **\[名前\]** ボックスに名前をアプリケーション ページに指定し、**\[追加\]** ボタンをクリックします。  
  
     複数のフォルダーとファイルがプロジェクトに追加されます。  これらのファイルの詳細については、「[SharePoint のアプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)」を参照してください。  
  
     Visual Web Developer デザイナーの **\[ソース\]** のビューでは、ASP.NET ページ ファイルが表示されます。  コントロールを **\[ツールボックス\]** から追加し、コンテンツ プレースホルダーに配置することにより、ページをデザインできます。  詳細については、「[ソース ビュー \(Web ページ デザイナー\)](http://msdn.microsoft.com/ja-jp/5911396b-fe51-4150-9ff1-b085f812862f)」を参照してください。  
  
7.  コントロール イベントを処理したい場合は、アプリケーション ページのコード ファイルにコードを追加します。  
  
     コード ファイルが ASP.NET ページ ファイルのノードを展開し、.cs または .vb 拡張子がある場合は、プロジェクトの言語によって表示されます。  アプリケーション ページを作成する方法の詳細については、「[チュートリアル: SharePoint アプリケーション ページの作成](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)」を参照してください。  
  
## 参照  
 [Visual Studio Web Development Content Map](http://msdn.microsoft.com/ja-jp/9c31f93b-c8fb-4599-9b14-6194ec8c7539)   
 [SharePoint のアプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [チュートリアル: SharePoint アプリケーション ページの作成](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
  