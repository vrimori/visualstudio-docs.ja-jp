---
title: "Extending the SharePoint Project System"
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
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 654b2973-a5c9-44be-a3d2-8bc3d15f9624
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Project System
  Visual Studioで一連のプロジェクト テンプレートおよび項目テンプレートを使用してSharePointソリューションを作成できます。  これらのテンプレートは、さまざまなアプリケーション開発シナリオの要件を満たしていますが、必要な機能が常に提供されるとは限りません。されることがあります。  そのような場合は、SharePoint プロジェクト システムを拡張して対処することができます。  
  
## SharePoint プロジェクト システムの概要  
 SharePoint プロジェクト システムは、*SharePoint プロジェクト項目*の基本コンポーネントに基づいています。  SharePoint プロジェクト項目は、リスト定義、Web パーツ、コンテンツ タイプなど、単一の SharePoint カスタマイズを表しています。  
  
 SharePoint プロジェクトは、1 つまたは複数の SharePoint プロジェクト項目を含む Visual Studio プロジェクトです。  また、SharePoint プロジェクトには、配置のためにプロジェクト項目をフィーチャーとパッケージにグループ化する方法を定義したその他のコンポーネントも含まれます。  
  
 SharePoint プロジェクト項目と SharePoint プロジェクトの内容の詳細については、「[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)」を参照してください。  
  
## SharePoint プロジェクト システムの拡張方法  
 SharePoint プロジェクト システムは、次のような方法で拡張できます。  
  
-   独自の SharePoint プロジェクト項目の種類を定義し、Visual Studio で新しい項目テンプレートまたはプロジェクト テンプレートに関連付けます。  たとえば、カスタム動作またはフィールドを作成するための SharePoint プロジェクト項目の種類を定義できます。  詳細については、「[Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)」を参照してください。  
  
-   Visual Studio に既にインストールされている SharePoint プロジェクト項目の種類を拡張します。  たとえば、開発者がメニュー項目を選択すると、**\[ソリューション エクスプローラー\]** のプロジェクト項目に対するショートカット メニュー項目を追加し、プロジェクト項目をカスタマイズできます。  詳細については、「[Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)」を参照してください。  
  
-   SharePoint プロジェクトを拡張します。  たとえば、項目が SharePoint プロジェクトに追加されたり SharePoint プロジェクトから削除されたりした場合に特定のタスクを実行するイベント ハンドラーを追加します。  詳細については、「[Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)」を参照してください。  
  
-   SharePoint プロジェクト項目と SharePoint プロジェクトのパッケージ化と配置の動作を拡張します。  たとえば、プロジェクトの配置時や取り消し時に実行するカスタムの配置手順を作成します。また、Visual Studio によって特定の配置手順が実行されるタイミングで追加のカスタム タスクを実行することもできます。  詳細については、「[Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)」を参照してください。  
  
## 一般的な開発タスク  
 SharePoint プロジェクト システムの拡張機能では、次の一般的なタスクを実行できます。  
  
-   カスタム文字列データをプロジェクト項目と共に、数種類のプロジェクト ファイルに保存する。  詳細については、「[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)」を参照してください。  
  
-   SharePoint プロジェクト システムのオブジェクトを Visual Studio のオートメーション オブジェクト モデルまたは統合オブジェクト モデルの対応するオブジェクトに変換する。または、その逆。  詳細については、「[Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)」を参照してください。  
  
## 参照  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  