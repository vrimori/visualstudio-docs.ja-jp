---
title: "方法: モジュールを使用してファイルを含める | Microsoft Docs"
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
  - "モジュール [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, モジュール"
ms.assetid: 16ac3c3b-8219-466c-8550-6109357f2f9a
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 方法: モジュールを使用してファイルを含める
  *モジュール* \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] のモジュールとは異なる\) は、SharePoint にファイル \(ASPX マスター ページ、テキスト ファイル、イメージなど\) を配置するために使用できるコンテナーです。  
  
 ファイルは、ドキュメント ライブラリに配置することも、ドキュメント ライブラリに含まれない通常のファイル \(default.aspx など\) として配置することもできます。  ファイルをドキュメント ライブラリに追加するには、**File** 要素の属性として `Type="GhostableInLibrary"` を指定します。  これにより、ファイルがライブラリに追加されるときにそのファイルのリスト項目が作成されるようになります。  ファイルをドキュメント ライブラリの外部に配置するには、`Type="Ghostable"` を指定するか、**Type** 属性を省略します。  
  
## SharePoint ソリューションへのモジュールの追加  
  
#### モジュールを追加するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で、SharePoint プロジェクトを開くか、または作成します。  
  
     詳細については、「[SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)」を参照してください。  
  
2.  次に **\[ソリューション エクスプローラー\]** で、プロジェクト ノードを選択し、メニュー バーで、**\[プロジェクト\]** をクリックします、**\[新しいアイテムの追加\]** を選択します。  
  
     **\[新しい項目の追加\]** ダイアログ ボックスが表示されます。  
  
3.  SharePoint テンプレートの一覧で、**\[モジュール\]** テンプレートを選択し、**\[追加\]** ボタンをクリックします。  
  
     この手順では、Module1 というプロジェクトにノードを作成します。  
  
4.  Module1 の下に、Sample.txt ファイルを削除します。  
  
     Sample.txt は、すべての新しいモジュールに例として含まれるもので、必要ありません \(このファイルを削除すると、モジュールの Elements.xml ファイルのこのファイルのエントリも削除されます\)。  
  
5.  次にファイルが SharePoint 内の特定のフォルダー構造に配置されるよう **\[プロジェクト\]** をクリックしますメニュー バー **\[新しいフォルダー\]** で Module1 ノード、選択して [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で Module1 の下に、フォルダーを作成します。  
  
6.  次に、ファイルを追加し、メニュー バーで選択し、**\[既存のアイテムを追加\]\[プロジェクト\]** をクリックしますフォルダーです。  
  
7.  SharePoint に配置するを選択し、**\[追加\]** をクリックすると、一つ以上のファイルを表します。  
  
     ファイルをプロジェクトに追加すると、モジュールの Elements.xml ファイルにそのファイルのエントリが自動的に追加されます。  プロジェクトを配置すると、それらのファイルが SharePoint サーバーにコピーされます。コピーされる場所は、**File** 要素の **Url** 属性に指定されている、プロジェクトのルート ディレクトリを基準とする相対パスです \(`Url="Module1/New Folder/SomeFile.doc` など\)。  ファイルの配置場所を変更するには、**ソリューション エクスプローラー**で別のフォルダーに移動するか、**Url** の設定を変更します。  
  
8.  ファイルがドキュメント ライブラリに表示されるようにするには、Elements.xml のそのファイルのエントリに `Type="GhostableInLibrary"` 属性を追加します。  次に例を示します。  
  
    ```  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. プロジェクトを配置します。  
  
     SharePoint 内の指定した場所にファイルがコピーされます。  
  
## 参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  