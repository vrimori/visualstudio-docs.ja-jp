---
title: "Extending the SharePoint Tools in Visual Studio | Microsoft Docs"
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
  - "Visual Studio, extending tools"
  - "extensibility [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extending tools"
ms.assetid: 084cf4bf-aaba-4277-8032-448f2cb2a124
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Tools in Visual Studio
  Visual Studio の SharePoint ツールは、さまざまなアプリケーション開発シナリオの要件を満たします。  しかし、開発に必要な機能が常に提供されるとは限りません。  そのような場合は、SharePoint のツールを拡張して、自分に必要な機能を作成することができます。  
  
## SharePoint ツールを拡張する方法  
 SharePoint プロジェクト システムおよび **\[サーバー エクスプローラー\]** ウィンドウの **\[SharePoint 接続\]** ノードは拡張できます。  
  
### SharePoint プロジェクト システムの拡張  
 Visual Studio では、 SharePoint ソリューションの作成に使用できる一連のプロジェクト テンプレートおよび項目テンプレートが含まれています。  たとえば、イベント レシーバー、リスト定義、ワークフロー、Web パーツなどに対応したテンプレートが存在します。  ただし、フィールドやカスタム動作などの SharePoint コンポーネントを作成するために独自の種類の SharePoint プロジェクト項目を定義することもできます。  また、既に Visual Studio にインストールされている SharePoint プロジェクト項目の種類の拡張を作成したり、SharePoint プロジェクトの拡張機能を作成したりすることもできます。  
  
 詳細については、「[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)」を参照してください。  
  
### サーバー エクスプローラーの \[SharePoint 接続\] ノードの拡張  
 Visual Studio で、**サーバー エクスプローラー** のペインで階層ツリー ビューの一つ以上の SharePoint ローカル サイトの多くのコンポーネントを表示するために**SharePoint 接続** ノードを使用できます。 また **SharePoint 接続** ノードを次のように拡張できます:  
  
-   独自のノードを追加する。  既定では表示されない SharePoint サイトのコンポーネントを表示する必要がある場合に適した方法です。  
  
-   既存のノードを拡張する。  たとえば、新しい子ノードを既存のノードに追加できます。またはショートカット メニュー項目をノードに追加し、開発者がメニュー項目をクリックしたときにタスクを実行できます。  
  
 詳細については、「[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)」を参照してください。  
  
## 開発コンピューターの要件  
 SharePoint ツールの拡張機能を作成するには、開発用コンピューターは、 Visual Studio で SharePoint ソリューションを作成する場合と同じ要件を満たしている必要があります。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
 また、[!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] もインストールすることをお勧めします。  SDK には、Visual Studio の拡張に使用できるプロジェクト テンプレートおよびツールが付属しています。  特に、SDK には、Visual Studio Extension \(VSIX\) パッケージを容易に作成できるプロジェクト テンプレートが用意されています。  VSIX パッケージは、 Visual Studio の Visual Studio 拡張機能を配置する推奨される方法です。  SharePoint ツールのすべての拡張機能は VSIX パッケージを使用して配置する必要があります。  このドキュメントのすべてのチュートリアルは、[!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] がインストールされていることを前提に作成されています。  
  
 SDK をダウンロードするには、[http:\/\/go.microsoft.com\/fwlink\/?LinkId\=164562](http://go.microsoft.com/fwlink/?LinkId=164562) を参照してください。  Visual Studio の拡張機能の詳細については、「[Visual Studio 拡張機能の開発](../Topic/Developing%20Visual%20Studio%20Extensions.md)」を参照してください。  
  
## 参照  
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Reference &#40;SharePoint Tools Extensibility&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  