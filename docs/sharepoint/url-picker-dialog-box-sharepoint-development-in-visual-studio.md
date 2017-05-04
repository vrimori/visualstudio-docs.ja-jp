---
title: "URL ピッカー ダイアログ ボックス (Visual Studio での SharePoint 開発) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.VWD.URLPicker"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での SharePoint 開発, デザイナー"
  - "Visual Studio での SharePoint 開発, URL ピッカー"
ms.assetid: 33f8f521-e1f8-4242-a580-8a4bd9cb5ddc
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# URL ピッカー ダイアログ ボックス (Visual Studio での SharePoint 開発)
  URL ピッカー ダイアログ ボックスで、プロジェクトにまたは SharePoint を実行しているローカル サーバー上に存在するマスター ページ ファイルまたはイメージ ファイルなどのファイルを選択できます。  
  
 このダイアログ ボックスは、プロパティを設定するファイルを選択できる場合に表示されます。  省略記号\(...\)ボタンをクリックして **\[プロパティ\]** ウィンドウのさまざまなプロパティの横にあるこのダイアログ ボックス \(![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.png "ASP.NET モバイル デザイナー楕円")\) を開くことができます。  省略記号ボタンは、デザイナーの**ソース** ビューで特定の属性に値を割り当てるときに、IntelliSense プロンプトとしても表示されます。  
  
## UIElement の一覧  
 **\[プロジェクト フォルダー\]**  
 プロジェクト内またはローカル SharePoint を実行しているサーバーで定義されたフォルダーの一覧を表示します。  サブフォルダーを表示するには、展開ボタンをクリックします。  
  
 プロジェクトのファイルを選択するに **\[プロジェクト\]** ノードを展開します。  プロジェクトのファイルがダイアログ ボックスで選択可能なファイルとして表示されるのは、次の条件を満たしている場合です。  
  
-   ファイルは、マップされたフォルダーに存在する必要があります。  
  
-   ファイルは、ソリューション パッケージに追加される必要があります。  
  
-   ファイルは、別のプロジェクトに存在することはできません。  
  
 これらの条件を満たさないファイルを参照する必要がある場合は、ファイルのパスを手動で入力する必要があります。  
  
 SharePoint を実行しているローカル サーバーに存在するファイルを選択するに **\[サーバー\]** ノードを展開します。  これらのファイルがダイアログ ボックスで選択可能なファイルとして表示されるのは、次の条件を満たしている場合です。  
  
-   ファイルは、マップされたフォルダー **Images**、**Layouts**、**ControlTemplates** のいずれかに存在する必要があります。  
  
-   ファイルは、SharePoint コンテンツ データベース内に存在することはできません。  
  
 これらの条件を満たさないファイルを参照する必要がある場合は、ファイルのパスを手動で入力する必要があります。  
  
 **\[フォルダーの内容\]**  
 選択したフォルダーに格納されているファイルの一覧を表示します。  ファイルを選択し、ダイアログ ボックスを閉じた後で元のプロセスに選択内容を送信するように **\[OK\]** ボタンをクリックします。  
  
 **\[ファイルの種類\]**  
 タスクに適したファイルの一覧から選択するか。  
  
## 参照  
 [SharePoint のアプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Visual Studio Web Development Content Map](http://msdn.microsoft.com/ja-jp/9c31f93b-c8fb-4599-9b14-6194ec8c7539)  
  
  