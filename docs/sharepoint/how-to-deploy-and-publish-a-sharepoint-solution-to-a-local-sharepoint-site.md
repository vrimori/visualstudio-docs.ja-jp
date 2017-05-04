---
title: "方法: SharePoint ソリューションをローカルの SharePoint サイトに配置および発行する | Microsoft Docs"
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
  - "配置 [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, 配置"
ms.assetid: 73f8d6a9-4c64-4bba-ae0e-9474baf8df26
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 方法: SharePoint ソリューションをローカルの SharePoint サイトに配置および発行する
  開発コンピューター上のローカル SharePoint サーバーに SharePoint ソリューションを配置または発行できます。  配置プロセスでは、.wsp ファイルが SharePoint サーバーにコピーされ、ソリューションがインストールされて、フィーチャーがアクティブ化されます。  発行プロセスは SharePoint サーバーにのみ、.wsp ファイルをコピーし、インストールされます。  手動で SharePoint のトレースを有効にするように行う必要があります。  
  
## SharePoint ソリューションをローカルの SharePoint サーバーに配置するには  
  
1.  **\[ソリューション エクスプローラー\]** で、配置するプロジェクトを選択します。  
  
2.  メニュー バーで、**\[ソリューションの配置\]\[ビルド\]** をクリックします。  
  
     .wsp ファイルが作成され、ローカルの SharePoint サーバーにインストールされます。  また、フィーチャーがアクティブ化されます。  
  
## SharePoint ソリューションをローカルの SharePoint サーバーに発行するには  
  
1.  **\[ソリューション エクスプローラー\]** で **\[発行\]** をクリックします発行および対象の SharePoint のプロジェクトのショートカット メニューを開きます。  
  
2.  **\[発行\]** ダイアログ ボックスで、**\[ファイル システムに発行する\]** のオプション ボタンを選択します。  
  
3.  **\[ターゲットの場所\]** のテキスト ボックスで、ローカル パスを入力し、**\[発行\]** ボタンをクリックします。  
  
     発行の進行状況は Visual Studio の **\[出力\]** ウィンドウに表示されます。  プロセスが完了したら、ソリューション \(.wsp\) ファイルは、ローカル SharePoint サーバーにインストールされています。  ただし、SharePoint で使用されることを行う必要があります。  ソリューション ファイルが既に存在する場合、エラーが発生し、既存のファイルを上書きするかどうかを切り替えます。  パッケージのアップグレードの詳細については、[方法: リモート サーバー上で SharePoint ソリューションを配置、発行、およびアップグレードする](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)のリモート パッケージのアップグレードのセクションを参照してください。  
  
## 参照  
 [方法: リモート サーバー上で SharePoint ソリューションを配置、発行、およびアップグレードする](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [SharePoint ソリューション パッケージの作成](../sharepoint/creating-sharepoint-solution-packages.md)   
 [方法: SharePoint ソリューション パッケージをカスタマイズする](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [方法: パッケージ デザイナーを使用してパッケージのフィーチャーおよび項目を追加および削除する](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  