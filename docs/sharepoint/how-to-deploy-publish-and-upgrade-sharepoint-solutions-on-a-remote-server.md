---
title: '方法: 配置、発行、およびリモート サーバー上で SharePoint ソリューションのアップグレード |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 108474e725c95f495bf6eec0f9a2224ca971b3d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>方法: リモート サーバー上で SharePoint ソリューションを配置、発行、およびアップグレードする
  に加えて、SharePoint ソリューションの配置、ローカル システムに、リモート サイトまたはローカルの SharePoint サイトにセキュリティで保護された SharePoint ソリューションを発行できます。 リモート発行プロセスは、SharePoint サーバーに .wsp ファイルをコピー、ソリューションをインストールし、ソリューションをアクティブ化することができます。 変更を行った後は、リモート SharePoint ソリューションのインストールをアップグレードすることもできます。  
  
## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>リモート SharePoint サーバーをセキュリティで保護された SharePoint ソリューションを発行するには  
  
1.  **ソリューション エクスプ ローラー**、発行、および順に選択する、セキュリティで保護された SharePoint プロジェクトのショートカット メニューを開いて**発行**です。  
  
2.  **発行** ダイアログ ボックスで、選択、 **SharePoint サイトに発行**オプションをクリックし、次の例など、オンライン発行のサイトの URL を入力: **https://mytestsite.sharepoint.microsoftonline.com**.  
  
3.  選択、**発行後にブラウザーでソリューション ギャラリー ページを開く**のソリューションの一覧を表示するオプション ボタン、**ソリューション ギャラリー**発行後のページです。  
  
4.  選択、**発行**ボタンをクリックします。  
  
5.  ユーザー認証が必要な場合、リモート サーバーにログオンします。  
  
     Visual Studio で発行の進行状況が表示される**出力**ウィンドウです。 プロセスが完了したら、ソリューション (.wsp) ファイルは、リモートの SharePoint サーバーにインストールされます。 ただし、その必要がありますまだアクティブ化を SharePoint で使用します。  
  
6.  **ソリューション ギャラリー**ページ、SharePoint アプリケーションを選択し、リボンで、次のように選択します。、 **Activate**ボタンをクリックします。  
  
7.  **アクティブ ソリューション**ダイアログ ボックスで、リボンで、選択、**アクティブ化**を再度クリックします。  
  
     **ステータス** 列、**ソリューション ギャラリー**ページは、アプリケーションがアクティブであることを示します。  
  
## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>リモート SharePoint サーバー上のセキュリティで保護された SharePoint ソリューションをアップグレードするには  
 サンド ボックス化された SharePoint ソリューションがリモート サーバーで既にパブリッシュされている場合、次のプロセスを使用すると、アプリケーションに変更を行った後にアップグレードする[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
1.  SharePoint パッケージの名前を変更[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 これを行うで**ソリューション エクスプ ローラー**パッケージを開きます。 表示される、**パッケージ エクスプ ローラー**です。  
  
2.  **パッケージ エクスプ ローラー**で、**名前**ボックスで、一意の名前に、パッケージ名を変更します。  
  
3.  プロジェクトを保存します。  
  
4.  **ソリューション エクスプ ローラー**、プロジェクトのショートカット メニューを開きを選択し、**発行**です。  
  
5.  **発行** ダイアログ ボックスで、選択、 **SharePoint サイトに発行**オプションをクリックし、ソリューションが保存されているリモート サーバーの URL がない場合に入力してください。  
  
6.  選択、**発行後にブラウザーでソリューション ギャラリー ページを開く**のソリューションの一覧を表示するオプション ボタン、**ソリューション ギャラリー**発行後のページです。  
  
7.  選択、**発行**ボタンをクリックします。  
  
8.  ユーザー認証が必要な場合、リモート サーバーにログオンします。  
  
     ログインした場合、リモート サーバーに最近、認証は必要なできません。  
  
     SharePoint サーバー上を同じ名前を持つアプリケーションの旧バージョンがまだ存在する場合は、同じ名前のパッケージは、SharePoint サーバーに既に存在するエラーが表示されます。 パブリッシュする前に一意の名前に、パッケージの名前を変更する必要があります。  
  
9. SharePoint では、新しいアプリケーションを選択し、リボンで、次のように選択します。、**アップグレード**ボタンをクリックします。  
  
10. **ソリューションのアップグレード**ダイアログ ボックスで、リボンで、選択、**アップグレード**を再度クリックします。 **ステータス** 列、**ソリューション ギャラリー**ページは、アプリケーションがアクティブであるようになりました示す必要があります。  
  
     ソリューションの古いバージョンが非アクティブ化、ソリューションの新しいバージョンが、以前のソリューションから保持されているデータによってアップグレードおよび SharePoint の新しいソリューションを有効にします。  
  
## <a name="see-also"></a>関連項目  
 [方法: 配置し、SharePoint ソリューションをローカルの SharePoint サイトに発行](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [SharePoint ソリューション パッケージの作成](../sharepoint/creating-sharepoint-solution-packages.md)   
 [方法: SharePoint ソリューション パッケージをカスタマイズします。](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [方法: パッケージ デザイナーを使用してパッケージのフィーチャーおよび項目を追加および削除する](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  