---
title: 配置、発行、および SharePoint ソリューション パッケージのアップグレード |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 17578fbfb58d354f06e91c78f067d228b92860fe
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327204"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>配置、発行、および SharePoint ソリューション パッケージのアップグレード
  Visual Studio で SharePoint ソリューションを開発した後か、そのパッケージ (.wsp) ファイルをローカル SharePoint サーバーにデプロイしたりリモートまたはローカルの SharePoint サーバーにパブリッシュできます。 ファイルを展開する場合は、パッケージ ファイル (.wsp) を展開する方法をカスタマイズできます。  
  
> [!NOTE]  
>  現時点では、サンド ボックス ソリューションのみがリモートの SharePoint サーバーにパブリッシュできます。 詳細については、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)します。  
  
## <a name="deploy-publish-and-upgrade"></a>配置、発行、およびアップグレード
 *展開*ローカル ホストに、Visual Studio での SharePoint プロジェクトからビルドされた SharePoint ソリューション ファイルのコピーを参照します。 デプロイ済みのソリューションでは、展開後、ソリューションのアクティブ化など、インターネット インフォメーション サービス (IIS) プールのリサイクル、展開の手順を構成してなど。 展開するには、使用、**デプロイ**コマンドを**ビルド**メニュー。 詳細については、次を参照してください。[方法: SharePoint の配置構成を編集](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)と[方法: 展開と SharePoint ソリューションをローカル SharePoint サイトにパブリッシュ](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)します。  
  
 *発行*参照をリモートの sharepoint サンド ボックス化された SharePoint ソリューション ファイルをアップロードするサイト。 つまり、別のシステム上にあるサイトです。 ローカルの SharePoint サイトに SharePoint のサンド ボックス ソリューション ファイルを発行することもできますが、かどうかに発行されたサイトは、ローカルまたはリモートに関係なく、その展開の手順を構成することはできません。  
  
 *アップグレード*既存のリモートまたはローカルで発行済みの SharePoint ソリューションの更新を参照します。 Visual Studio で SharePoint ソリューションに変更を加えた後は、ソリューションを再パブリッシュ、およびが正常に再パブリッシュした後、ソリューションをアップグレードするソリューションのパッケージ ファイル名を変更します。 ローカルで発行済みのソリューションを再パブリッシュした場合は、既存のソリューション ファイルを上書きできます。  
  
## <a name="deploy-packages"></a>パッケージを配置します。
 テストとデバッグ用の開発用コンピューターで、SharePoint サーバーにパッケージ ファイルを配置できます。 パッケージ ファイルを選択して別のコンピューターにインストールできることを作成することも、**ファイル システムに公開**内のオプション ボタン、**発行** ダイアログ ボックス。 パッケージが作成され、指定したローカル ファイル パスにコピーします。 ローカル サーバーに SharePoint ソリューションを展開するには、使用、**デプロイ**コマンドを**ビルド**メニュー。 詳細については、次を参照してください。[方法: デプロイと、SharePoint ソリューションをローカル SharePoint サイトに発行](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)します。  
  
 リスト定義の展開、イベント レシーバーを追加して、フィーチャー デザイナーとパッケージ デザイナーを使用する方法については、次を参照してください。[チュートリアル: プロジェクト タスク リスト定義の展開](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)します。  
  
## <a name="customize-the-deployment-process"></a>展開プロセスをカスタマイズします。
 次の表では、デバッグ、および SharePoint ソリューションを展開するときに使用できる 2 つの展開構成を示します。  
  
|展開の構成|説明|  
|------------------------------|-----------------|  
|既定値|既定の配置構成。 次の展開手順が実行されます。<br /><br /> 1.配置前コマンドを実行します。<br />2.IIS アプリケーション プールをリサイクルします。<br />3.ソリューションを取り消します。<br />4.ソリューションを追加します。<br />5.機能を有効にします。<br />6.配置後コマンドを実行します。<br /><br /> パッケージがアンインストールされると、次の取り消し手順が実行されます。<br /><br /> 1.IIS アプリケーション プールをリサイクルします。<br />2.ソリューションを取り消します。|  
|アクティベーション不可|この配置構成は、既定の構成として同じ手順を実行しますが、アクティブ化の手順をスキップします。|  
  
 1 つの手順を完了したり、展開プロセスの手順の順序を変更、独自の展開構成を作成できます。 詳細については、次を参照してください。[方法: SharePoint の配置構成を編集](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)します。  

 デプロイの前後に実行するためのコマンドを追加することもできます。 詳細については、次を参照してください。[方法: SharePoint の設定の配置コマンド](../sharepoint/how-to-set-sharepoint-deployment-commands.md)します。  
  
## <a name="publish-packages-to-a-remote-or-local-server"></a>リモートまたはローカル サーバーにパッケージを公開します。
 メニュー バーでのリモート サーバーをセキュリティで保護された SharePoint ソリューションを発行する選択**ビルド**、**発行**、[、**発行**] ダイアログ ボックスで、選択、 **SharePoint サイトに発行**など、リモート サーバーの URL を提供する、オプション ボタン **https://someremoteserver.sharepoint.microsoftonline.com**します。  
  
 ローカル サーバーに SharePoint ソリューションの発行、**発行** ダイアログ ボックスで、選択、**ファイル システムに公開**オプション ボタン、ローカル システム パスを指定します。  
  
 ソリューションが SharePoint に正常に発行した後、ソリューションが表示されます、**ソリューション ギャラリー**がアクティブ化できます。 詳細については、次を参照してください。[方法: 配置、発行、およびリモート サーバー上で SharePoint ソリューションのアップグレード](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)します。  
  
### <a name="upgrade-published-packages"></a>公開済みのパッケージをアップグレードします。
 パブリッシュした後に、Visual Studio での SharePoint プロジェクトに変更を加えた場合、変更を含める公開されたパッケージをアップグレードする必要があります。 正常にアップグレードするには、一意の名前がパッケージに必要です。 同じ名前のパッケージは、エラー アラート - 既存のアプリケーションを更新するときに発生するのと、SharePoint サイトで見つかった場合、ファイル名を競合し、パッケージの名前を変更することができます。 、再発行後は、新しいパッケージは、SharePoint サイトに表示され、アップグレードすることができます。 アップグレードされたパッケージは、以前のパッケージからデータを使用して、ソリューションを更新し、し、SharePoint でソリューションがアクティブにします。 詳細については、次を参照してください。[方法: 配置、発行、およびリモート サーバー上で SharePoint ソリューションのアップグレード](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)します。  
  
## <a name="see-also"></a>関連項目
 [パッケージ化し、SharePoint ソリューションのデプロイ](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
