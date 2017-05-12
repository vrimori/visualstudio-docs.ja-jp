---
title: "方法: リモート サーバー上で SharePoint ソリューションを配置、発行、およびアップグレードする"
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
  - "配置 [Visual Studio での SharePoint 開発]"
  - "リモート配置 [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, 配置"
  - "Visual Studio での SharePoint 開発, リモート配置"
ms.assetid: d9c67fae-d097-4e26-a2b9-0f72ff800987
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 方法: リモート サーバー上で SharePoint ソリューションを配置、発行、およびアップグレードする
  ローカル システムへの SharePoint ソリューションを配置するだけでなく、リモート サイトまたはローカルの SharePoint サイトにサンドボックス SharePoint ソリューションを発行できます。  リモート発行プロセス、.wsp ファイルが SharePoint サーバーにコピーされ、有効をソリューションをアクティブにするには、ソリューションをインストールします。  これに変更が加えられた後、Remote SharePoint ソリューションのインストールをアップグレードできます。  
  
## サンドボックス SharePoint ソリューションをリモートの SharePoint サーバーに発行するには  
  
1.  **\[ソリューション エクスプローラー\]** で、発行するプロジェクトを右クリックし、**\[発行\]** をクリックしますサンドボックス SharePoint のプロジェクトのショートカット メニューを。  
  
2.  **\[発行\]** ダイアログ ボックスで、**\[SharePoint サイトに発行\]** のオプション ボタンをクリックし、以下の例のようなオンライン発行サイトの URL を入力します。: https:\/\/mytestsite.sharepoint.microsoftonline.com。  
  
3.  発行した後で **\[ソリューション ギャラリー\]** ページのソリューションの一覧を表示するに **\[発行後にブラウザーでソリューション ギャラリーのページを開く\]** のオプション ボタンを選択します。  
  
4.  **\[発行\]** ボタンをクリックします。  
  
5.  ユーザー認証が必要な場合は、そのリモート サーバーにログオンします。  
  
     発行の進行状況は Visual Studio の **\[出力\]** ウィンドウに表示されます。  プロセスが完了したら、ソリューション \(.wsp\) ファイルは、リモートの SharePoint サーバーにインストールされます。  ただし、その場合も、SharePoint で使用する前に行う必要があります。  
  
6.  次に **\[ソリューション ギャラリー\]** ページで、リボンの SharePoint アプリケーションを選択します **\[ライセンス認証\]** をクリックします。  
  
7.  **\[ソリューションのアクティブ化\]** ダイアログ ボックスのリボンで、**\[ライセンス認証\]** ボタンをもう一度クリックします。  
  
     **\[ソリューション ギャラリー\]** ページの **\[状態\]** の列は、アプリケーションがアクティブであることを示します。  
  
## リモートの SharePoint サーバーのサンドボックス SharePoint ソリューションをアップグレードするには  
 サンドボックス SharePoint ソリューションのリモート サーバーに既に発行すると、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]アプリケーションに変更を加えた後、次の手順を使用してアップグレードする。  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]の SharePoint パッケージの名前を変更します。  **\[ソリューション エクスプローラー\]** でこれを行うと、パッケージを開きます。  これは **\[パッケージ エクスプローラー\]** に表示されます。  
  
2.  **\[パッケージ エクスプローラー\]** で、**\[名前\]** ボックスに、一意の名前の変更、パッケージ名。  
  
3.  プロジェクトを保存します。  
  
4.  **\[ソリューション エクスプローラー\]** で、プロジェクトのショートカット メニューを開き、**\[発行\]** をクリックします。  
  
5.  **\[発行\]** ダイアログ ボックスで、ソリューションを保存するリモート サーバーの URL がない場合、**\[SharePoint サイトに発行\]** のオプション ボタンをクリックし、ファイル名を入力します。  
  
6.  発行した後で **\[ソリューション ギャラリー\]** ページのソリューションの一覧を表示するに **\[発行後にブラウザーでソリューション ギャラリーのページを開く\]** のオプション ボタンを選択します。  
  
7.  **\[発行\]** ボタンをクリックします。  
  
8.  ユーザー認証が必要な場合は、そのリモート サーバーにログオンします。  
  
     リモート サーバーにログインしている場合に、認証が不要な場合があります。  
  
     同じ名前が存在しているアプリケーションの古いバージョンが SharePoint サーバー上にある場合は、同じ名前のパッケージが SharePoint サーバーに既に存在するとエラーが発生します。  一意の名前に発行する前にパッケージの名前を変更する必要があります。  
  
9. 次に、新しい SharePoint アプリケーションで、リボンをクリックし、**\[アップグレード\]** ボタンをクリックします。  
  
10. **\[ソリューションのアップグレード\]** ダイアログ ボックスのリボンで、**\[アップグレード\]** ボタンをもう一度クリックします。  **\[ソリューション ギャラリー\]** ページの **\[状態\]** の列に、アプリケーションがアクティブであることを示す必要があります。  
  
     ソリューションの古いバージョンが非アクティブ化された、ソリューションの新しいバージョンが古いソリューションで保持されるデータをアップグレードし、新しいソリューションが SharePoint でアクティブ化されます。  
  
## 参照  
 [方法: SharePoint ソリューションをローカルの SharePoint サイトに配置および発行する](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [SharePoint ソリューション パッケージの作成](../sharepoint/creating-sharepoint-solution-packages.md)   
 [方法: SharePoint ソリューション パッケージをカスタマイズする](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [方法: パッケージ デザイナーを使用してパッケージのフィーチャーおよび項目を追加および削除する](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  