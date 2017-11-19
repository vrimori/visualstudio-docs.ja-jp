---
title: "展開する、発行、および SharePoint ソリューション パッケージのアップグレード |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
ms.assetid: 5efc1d99-2bd2-4f1a-a7b0-86c3b8f533f0
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5ae973b0a1fc30f0592f6cb2702df645708ab43f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="deploying-publishing-and-upgrading-sharepoint-solution-packages"></a>SharePoint ソリューションのパッケージの配置、発行、アップグレード
  Visual Studio での SharePoint ソリューションを開発した後、いずれかローカル SharePoint サーバーにそのパッケージ (.wsp) ファイルを配置したり、リモートまたはローカルの SharePoint サーバーにパブリッシュできます。 ファイルを展開する場合は、パッケージ ファイル (.wsp) を展開する方法をカスタマイズできます。  
  
> [!NOTE]  
>  現時点では、サンド ボックス ソリューションのみがリモートの SharePoint サーバーにパブリッシュできます。 詳細については、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)です。  
  
## <a name="deploying-publishing-and-upgrading"></a>展開する、発行、およびアップグレード  
 *展開する*ローカル ホストに Visual Studio での SharePoint プロジェクトからビルドされた SharePoint ソリューション ファイルのコピーを指します。 展開されたソリューションでは、ソリューションの配置後、アクティブ化、展開手順については、インターネット インフォメーション サービス (IIS) プールのリサイクルなどを構成しなどできます。 展開するには、使用、**展開**コマンドを**ビルド**メニュー。 詳細については、次を参照してください。[する方法: SharePoint の配置構成を編集](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)と[する方法: 展開と SharePoint ソリューションをローカル SharePoint サイトにパブリッシュ](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)です。  
  
 *発行*参照サンド ボックス化された SharePoint ソリューション ファイルをリモートの SharePoint にアップロードするサイトです。 つまり、別のシステム上にあるサイトです。 ローカルの SharePoint サイトに、SharePoint サンド ボックス ソリューション ファイルを公開することもできますが、かどうか、サイトにパブリッシュされたでローカルまたはリモートに関係なく、その展開の手順を構成することはできません。  
  
 *アップグレード*は既存のリモートまたはローカルで発行済みの SharePoint ソリューションの更新を参照します。 Visual Studio で SharePoint ソリューションに変更を加えた後、ソリューションのパッケージ ファイル名を変更、ソリューションを再パブリッシュおよびが正常に再パブリッシュした後、ソリューションをアップグレードします。 ローカルで発行済みのソリューションを再発行する場合は、既存のソリューション ファイルを上書きできます。  
  
## <a name="deploying-packages"></a>パッケージの配置  
 テストおよびデバッグのため、開発用コンピューターで、SharePoint サーバーにパッケージ ファイルを配置できます。 選択して別のコンピューターにインストールできるパッケージ ファイルを作成することも、**ファイル システムに公開**内のオプション ボタン、**発行** ダイアログ ボックス。 パッケージが作成され、指定したローカル ファイル パスにコピーします。 SharePoint ソリューションをローカル サーバーを展開するには、**展開**コマンドを**ビルド**メニュー。 詳細については、次を参照してください。[する方法: 展開と SharePoint ソリューションをローカル SharePoint サイトにパブリッシュ](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)です。  
  
 リストの定義を展開、イベント レシーバーを追加して、フィーチャー デザイナーとパッケージ デザイナーを使用する方法については、次を参照してください。[チュートリアル: プロジェクト タスク リスト定義の配置](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)です。  
  
## <a name="customizing-the-deployment-process"></a>配置プロセスのカスタマイズ  
 次の表は、デバッグ、および SharePoint ソリューションを展開するときに使用できる 2 つの展開構成を示します。  
  
|展開の構成|説明|  
|------------------------------|-----------------|  
|既定|既定の配置構成。 次の展開手順が実行されます。<br /><br /> 1.配置前コマンドを実行します。<br />2.IIS アプリケーション プールをリサイクルします。<br />3.ソリューションを取り消します。<br />4.ソリューションを追加します。<br />5.機能を有効にします。<br />6.配置後コマンドを実行します。<br /><br /> パッケージがアンインストールされると、次の取り消し手順が実行されます。<br /><br /> 1.IIS アプリケーション プールをリサイクルします。<br />2.ソリューションを取り消します。|  
|アクティブ化しません。|この配置構成は、既定の構成として、同じ手順を実行が、アクティブ化の手順をスキップします。|  
  
 1 つの手順を完了するか、展開プロセスの手順の順序を変更する、独自の展開構成を作成できます。 詳細については、次を参照してください。[する方法: SharePoint の配置構成を編集](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)です。  
  
 展開の前後に実行するためのコマンドを追加することもできます。 詳細については、次を参照してください。[する方法: SharePoint の配置コマンドを設定](../sharepoint/how-to-set-sharepoint-deployment-commands.md)です。  
  
## <a name="publishing-packages-to-a-remote-or-local-server"></a>リモートまたはローカル サーバーにパッケージを発行します。  
 メニュー バーでのリモート サーバーにセキュリティで保護された SharePoint ソリューションを発行するには選択**ビルド**、**発行**、[、**発行**] ダイアログ ボックスで、選択、 **SharePoint サイトに発行**など、リモート サーバーの URL を提供する、オプション ボタン**https://someremoteserver.sharepoint.microsoftonline.com**です。  
  
 ローカル サーバーに SharePoint ソリューションを発行する、**発行** ダイアログ ボックスで、選択、**ファイル システムに公開**ローカル システム パスを提供する、オプション ボタンをクリックします。  
  
 正常に SharePoint に発行すると、ソリューション、ソリューションが表示されます、**ソリューション ギャラリー**がアクティブ化できます。 詳細については、次を参照してください。[する方法: 配置、発行、およびリモート サーバー上の SharePoint ソリューションのアップグレード](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)です。  
  
### <a name="upgrading-published-packages"></a>公開されたパッケージをアップグレードします。  
 パブリッシュした後に、Visual Studio での SharePoint プロジェクトに変更を加えた場合は、変更を含める発行済みのパッケージをアップグレードしてください。 正常にアップグレードするには、一意の名前がパッケージに必要です。 同じ名前のパッケージが見つかった場合 - これは、既存のアプリケーションを更新する場合に発生することが、SharePoint サイトでエラー アラート ファイル名を競合およびパッケージの名前を変更することができます。 再発行されない後は、新しいパッケージは、SharePoint サイトに表示され、アップグレードすることができます。 アップグレードされたパッケージは、古いパッケージからデータを使用してソリューションを更新し、し、SharePoint のソリューションがアクティブにします。 詳細については、次を参照してください。[する方法: 配置、発行、およびリモート サーバー上の SharePoint ソリューションのアップグレード](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)です。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  