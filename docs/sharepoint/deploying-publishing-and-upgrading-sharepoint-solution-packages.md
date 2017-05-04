---
title: "SharePoint ソリューションのパッケージの配置、発行、アップグレード | Microsoft Docs"
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
  - "VS.SharePointTools.Project.SharePointProjectPropertyTab"
  - "VS.SharePointTools.Project.Publishing"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "配置 [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, 配置"
ms.assetid: 5efc1d99-2bd2-4f1a-a7b0-86c3b8f533f0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# SharePoint ソリューションのパッケージの配置、発行、アップグレード
  Visual Studio で SharePoint ソリューションを開発した後、ローカル SharePoint サーバーにパッケージ \(.wsp\) ファイルを配置またはリモートまたはローカル SharePoint サーバーに発行できます。  ファイルを配置する場合は、パッケージ ファイル \(.wsp\) の配置方法をカスタマイズできます。  
  
> [!NOTE]  
>  現在、サンドボックス ソリューションのみリモートの SharePoint サーバーに発行できます。  詳細については、「[サンドボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)」を参照してください。  
  
## ビルド、配置、およびアップグレード発行します。  
 SharePoint プロジェクトの*配置が* Visual Studio でローカル ホストに組み込まれている SharePoint ソリューション ファイルをコピーすることを示します。  配置したソリューションには、さらに配置後にソリューションを操作する Internet Information Services \(IIS\) のプールのリサイクルなどの配置手順を構成できます。  配置するには、**\[ビルド\]** メニューの **\[配置\]** コマンドを使用します。  詳細については、「[方法: SharePoint の配置構成を編集する](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)」および「[方法: SharePoint ソリューションをローカルの SharePoint サイトに配置および発行する](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)」を参照してください。  
  
 *発行とは、* リモートの SharePoint サイトにサンドボックス SharePoint ソリューション ファイルのアップロードを示します; つまり、他のシステムにあるサイト。  また、ローカルの SharePoint サイトに SharePoint のサンドボックス ソリューション ファイルを発行してでも関係なくに発行されるサイトをローカルまたはリモートであっても、配置手順を設定できません。  
  
 *アップグレードは* リモートまたはローカルの SharePoint に発行したソリューションが存在することを更新することを示します。  Visual Studio で SharePoint ソリューションに変更が加えられると、再発行後のソリューション パッケージ ファイルの名前を変更し、ソリューションを再発行され、ソリューションをアップグレードします。  ローカルで発行されたソリューションを再発行する場合は、既存のソリューション ファイルを上書きできます。  
  
## パッケージの配置  
 テストおよびデバッグのために開発コンピューター上の SharePoint サーバーにパッケージ ファイルを配置できます。  また、別のコンピューターに **\[発行\]** ダイアログ ボックスに **\[ファイル システムに発行する\]** のオプション ボタンをクリックして、インストールできるパッケージ ファイルを作成できます。  パッケージは、指定されたローカル ファイル パスに作成されます。  ローカル サーバーに SharePoint ソリューションを配置するには、**\[ビルド\]** メニューの **\[配置\]** コマンドを使用します。  詳細については、「[方法: SharePoint ソリューションをローカルの SharePoint サイトに配置および発行する](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)」を参照してください。  
  
 リスト定義の配置方法、イベント レシーバーの追加方法、およびフィーチャー デザイナーとパッケージ デザイナーの使用方法については、「[チュートリアル: プロジェクト タスク リスト定義の配置](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)」を参照してください。  
  
## 配置プロセスのカスタマイズ  
 SharePoint ソリューションのデバッグ時と配置時に使用できる 2 つの配置構成を次の表に示します。  
  
|配置構成|説明|  
|----------|--------|  
|既定の|既定の配置構成です。  次の配置手順が実行:<br /><br /> 1.  配置前コマンドを実行します。<br />2.  IIS アプリケーション プールをリサイクルします。<br />3.  ソリューションを取り消しをクリックします。<br />4.  ソリューションを追加します。<br />5.  フィーチャーをアクティブ化します。<br />6.  配置後コマンドを実行します。<br /><br /> パッケージのアンインストール時には、次の取り消し手順が実行されます。<br /><br /> 1.  IIS アプリケーション プールをリサイクルします。<br />2.  ソリューションを取り消しをクリックします。|  
|アクティベーションなし|この配置構成では、既定の構成と同じ手順が実行されますが、アクティブ化の手順は省略されます。|  
  
 独自の配置構成を作成して、配置プロセスの中の 1 つの手順だけを実行したり、手順の順序を変更したりすることができます。  詳細については、「[方法: SharePoint の配置構成を編集する](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)」を参照してください。  
  
 配置の前後に実行されるコマンドを追加することもできます。  詳細については、「[方法: SharePoint の配置コマンドを設定する](../sharepoint/how-to-set-sharepoint-deployment-commands.md)」を参照してください。  
  
## リモートまたはローカル サーバーへの発行パッケージ  
 次に、リモート サーバーのサンドボックスで SharePoint ソリューションをメニュー バーで発行するには、**\[発行\]**、**\[発行\]** ダイアログ ボックスで選択して https:\/\/someremoteserver.sharepoint.microsoftonline.com などのリモート サーバーの URL を指定する **\[SharePoint サイトに発行\]** のオプション ボタンを **\[ビルド\]** をクリックします。  
  
 ローカル サーバーに SharePoint ソリューションを、**\[発行\]** ダイアログ ボックスで発行するには、ローカル システム パスを提供する **\[ファイル システムに発行する\]** のオプション ボタンを選択します。  
  
 ソリューションの後に SharePoint ソリューションに、表示、アクティブにできる **\[ソリューション ギャラリー\]** に発行します。  詳細については、「[方法: リモート サーバー上で SharePoint ソリューションを配置、発行、およびアップグレードする](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)」を参照してください。  
  
### 発行されたパッケージのアップグレード  
 発行後に Visual Studio の SharePoint に変更を加えるため変更が含まれるように、発行されたパッケージをアップグレードする必要があります。  正常にアップグレードするには、パッケージ名は一意である必要があります。  ファイル名の競合にエラー通知既存のアプリケーションを更新している–発生し、パッケージの名前を変更できるようにする場合は、同じ名前のパッケージが SharePoint サイト–にある場合。  再発行の後で、新しいパッケージが SharePoint サイトに表示され、アップグレードできます。  アップグレードされたパッケージによっては古いパッケージからのデータを使用して、ソリューションを更新し、SharePoint ソリューションがアクティブになります。  詳細については、「[方法: リモート サーバー上で SharePoint ソリューションを配置、発行、およびアップグレードする](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)」を参照してください。  
  
## 参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  