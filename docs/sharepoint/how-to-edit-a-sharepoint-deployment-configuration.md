---
title: "方法: SharePoint の配置構成を編集する"
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
  - "VS.SharePointTools.Project.DeploymentConfig"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での SharePoint 開発, 配置"
ms.assetid: bff1895b-d3fe-4ec0-ba91-f8884dc35957
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 方法: SharePoint の配置構成を編集する
  配置構成は、新たに作成できるだけではなく、既存の配置構成に変更を加えることもできます。  たとえば、配置プロセスの 1 つの手順だけを実行したり、手順の順序を変更したりすることができます。  組み込みの構成やプログラムによって追加された構成は変更できないため、配置構成の作成または変更が必要になる場合があります。  
  
## SharePoint の配置構成の作成  
  
#### SharePoint の配置構成を作成するには  
  
1.  次に **\[ソリューション エクスプローラー\]** で、SharePoint プロジェクトを選択し、メニュー バーで、**\[プロジェクト\]** をクリックします、*ProjectName***\[プロパティ\]** を選択します。  
  
2.  **\[SharePoint\]** タブで、**\[新規作成\]** ボタンをクリックします。  
  
     **\[新しい配置構成の追加\]** ダイアログ ボックスが表示されます。  
  
3.  **\[名前\]** のテキスト ボックスに、配置構成の名前を入力します。  
  
4.  **\[使用可能な配置手順\]** のペインで、配置構成に追加する手順を選択し \(**\[\>\]**\) ボタンをクリックし、次へをクリックします **\[OK\]** ボタンをクリックします。  
  
    > [!NOTE]  
    >  配置前コマンドまたは配置後コマンドが構成されている場合、これらの手順は、カスタマイズした配置構成に追加した場合にのみ実行されます。  
  
## アクティブな配置構成の変更  
  
#### アクティブな配置構成を変更するには  
  
1.  次に **\[ソリューション エクスプローラー\]** で、SharePoint プロジェクトを選択し、メニュー バーで、**\[プロジェクト\]** をクリックします、*ProjectName***\[プロパティ\]** を選択します。  
  
2.  **\[SharePoint\]** タブをクリックします。  
  
3.  **\[アクティブな配置構成\]** ボックスの一覧で、使用する配置構成の名前をクリックします。  
  
## 参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  