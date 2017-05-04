---
title: "方法: リソース ファイルを追加する | Microsoft Docs"
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
  - "リソース ファイル [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, リソース ファイル"
ms.assetid: 2b4ac232-992e-4070-8e98-6f11eb88e1a8
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 方法: リソース ファイルを追加する
  リソース ファイルを追加するコマンドは、ソリューション エクスプローラーのソリューション ノードとフィーチャー ノードのショートカット メニューにあります。  詳細については、「[SharePoint ソリューションのローカライズ](../sharepoint/localizing-sharepoint-solutions.md)」を参照してください。  
  
### SharePoint ソリューションにグローバル リソース ファイルを追加するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]では、SharePoint ソリューションを開きます。  
  
2.  次に **\[ソリューション エクスプローラー\]** で、SharePoint プロジェクト ノードを選択し、メニュー バーで、**\[プロジェクト\]** をクリックします、**\[新しいアイテムの追加\]** を選択します。  
  
3.  **\[新しいアイテムの追加\]** ダイアログ ボックスで、**\[グローバル リソース ファイル\]** テンプレートを選択し、**\[追加\]** ボタンをクリックします。  
  
    > [!NOTE]  
    >  グローバル リソース ファイルのプロジェクト項目テンプレートは、SharePoint プロジェクト項目が選択された場合のみ表示されます。  
  
4.  **\[リソースの追加\]** ダイアログ ボックスで、英語 \(米国\) などのリソース ファイルのカルチャを選択します。  
  
     この手順では、形式、リソースの*x*\#\#\#.*culture*\#\#\#.の resx のグローバル リソース ファイルがソリューションになど、Resource1.en\-US.resx 追加します。  
  
5.  **\[リソース エディター\]** が [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で開くと、リソース ファイルにリソースを追加します。  
  
### SharePoint フィーチャーにフィーチャー リソース ファイルを追加するには  
  
1.  SharePoint ソリューションが既に [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で開いていない場合は、ソリューションを開きます。  
  
2.  **\[ソリューション エクスプローラー\]** では、機能の名前のショートカット メニューを **\[フィーチャー\]** ノードで開き、**\[フィーチャー リソースの追加\]** をクリックします。  
  
     この手順では、*ResourceFileName*形式 \#\#\#.*culture*\#\#\#.の resx の機能にリソース ファイルを、Feature1.en\-US.resx など\) を追加します。  
  
3.  **\[リソース エディター\]** が [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で開くと、リソース ファイルにリソースを追加します。  
  
## 参照  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  