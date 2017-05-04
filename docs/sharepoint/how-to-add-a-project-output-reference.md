---
title: "方法: プロジェクト出力参照を追加する | Microsoft Docs"
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
  - "プロジェクト出力参照 [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, 高度なパッケージ化ツール"
  - "Visual Studio での SharePoint 開発, プロジェクト出力参照"
ms.assetid: 9d6bc25e-bf0d-4483-a691-2ad7a796fa80
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 方法: プロジェクト出力参照を追加する
  SharePoint 以外のプロジェクトのアセンブリ \(Silverlight プロジェクトの場合は .xap ファイル\) を SharePoint に配置するには、それらをプロジェクト出力参照として追加します。  
  
 プロジェクト出力参照を追加すると、その 2 つのプロジェクトの間にソリューションのビルドの依存関係が作成されます。  プロジェクト出力参照で関連付けられたプロジェクトは、SharePoint プロジェクトがビルドされて配置される前にビルドされます。  
  
### プロジェクト出力参照を追加するには  
  
1.  SharePoint プロジェクトと SharePoint 以外のプロジェクトを少なくとも 1 つずつ含むソリューションを読み込みます。  
  
2.  **\[ソリューション エクスプローラー\]** では、SharePoint プロジェクト項目のノードを選択します。  
  
3.  **\[プロパティ\]** ウィンドウで、**\[プロジェクト出力参照\]** のプロパティをクリックし、その横にある省略記号 \(![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.png "ASP.NET モバイル デザイナー楕円")\) ボタンをクリックします。  
  
4.  **\[プロジェクト出力参照\]** ダイアログ ボックスで、**\[追加\]** ボタンをクリックします。  
  
5.  プロパティ ペインで、下向きの矢印を **\[配置タイプ\]** のプロパティの横に選択し、表示する **\[ElementFile\]** など、SharePoint アイテムの適切な値を選択します。  
  
6.  **\[プロジェクト名\]** の横の矢印をクリックし、非 SharePoint プロジェクト項目の名前を選択し、**\[OK\]** ボタンをクリックします。  
  
## 参照  
 [プロジェクト項目でのパッケージ化と配置の情報の提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [方法: コントロールを安全なコントロールとしてマークする](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  