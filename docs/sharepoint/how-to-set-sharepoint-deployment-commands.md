---
title: "方法: SharePoint の配置コマンドを設定する"
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
  - "Visual Studio での SharePoint 開発, 配置"
ms.assetid: 289c8c33-a603-434e-889f-a0d0a1736ecb
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 方法: SharePoint の配置コマンドを設定する
  配置プロセスは、配置前コマンドおよび配置後コマンドを設定することによってカスタマイズできます。  これらのコマンドは、Visual Studio から SharePoint ソリューションをデバッグするときに他の配置アクションの前および後に実行されます。  
  
### 配置前コマンドを追加するには  
  
1.  メニュー バーで、**\[プロジェクト\]**、**\[*\<ProjectName\>* のプロパティ\]** の順に選択します。  
  
2.  **\[SharePoint\]** タブをクリックします。  
  
3.  **\[配置前コマンド ライン\]** のテキスト ボックスに、このステップをカスタマイズするための MS\-DOS コマンドまたは MSBuild を入力します。  
  
     たとえば、配置の完了前にディレクトリの内容を一覧表示するには、**dir**を入力します。  
  
### 配置後コマンドを追加するには  
  
1.  メニュー バーで、**\[プロジェクト\]**、**\[*\<ProjectName\>* のプロパティ\]** の順に選択します。  
  
2.  **\[SharePoint\]** タブをクリックします。  
  
3.  **\[配置後コマンド ライン\]** のテキスト ボックスに、このステップをカスタマイズするための MS\-DOS コマンドまたは MSBuild を入力します。  
  
     たとえば、配置の完了後にディレクトリの内容を一覧表示するには、**dir**を入力します。  MSBuild 変数をビルド ディレクトリからアセンブリをコピーするには **copy $\(TargetPath\) c:\\DeploymentDirectory**を入力します。  
  
## 参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  