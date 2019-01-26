---
title: '方法: 配置、発行、およびリモート サーバー上で SharePoint ソリューションのアップグレード |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4aafc503ff2b8dffed5b70d17f4eb488baf72704
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865087"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>方法: 配置、発行、およびリモート サーバー上で SharePoint ソリューションのアップグレード
  SharePoint ソリューションをローカル システムを展開だけでなくリモート サイトまたはローカルの SharePoint サイトに SharePoint のサンド ボックス ソリューションを発行できます。 リモートの公開プロセスのコピー、 *.wsp* SharePoint サーバーにファイルが、ソリューションをインストールして、ソリューションをアクティブ化することができます。 変更された後は、リモート SharePoint ソリューションのインストールをアップグレードすることもできます。  
  
## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>リモート SharePoint サーバーをセキュリティで保護された SharePoint ソリューションを発行するには  
  
1.  **ソリューション エクスプ ローラー**、発行、および選択する、セキュリティで保護された SharePoint プロジェクトのショートカット メニューを開き**発行**します。  
  
2.  **発行** ダイアログ ボックスで、選択、 **SharePoint サイトに発行**オプション ボタン、およびなど、オンライン発行サイトの URL を入力:`https://mytestsite.sharepoint.microsoftonline.com`します。  
  
3.  選択、**発行した後、ブラウザーでソリューション ギャラリー ページを開く**のソリューションの一覧を表示するオプション ボタン、**ソリューション ギャラリー**発行後のページ。  
  
4.  選択、**発行**ボタンをクリックします。  
  
5.  ユーザー認証が必要な場合、リモート サーバーにログオンします。  
  
     Visual Studio で発行の進行状況が表示されます。**出力**ウィンドウ。 プロセスが終了すると、ソリューション (*.wsp*) ファイル、リモートの SharePoint サーバーにインストールされます。 ただし、その必要がありますもアクティブ化する前に、SharePoint で使用できます。  
  
6.  **ソリューション ギャラリー**ページで、SharePoint アプリケーションを選択し、リボンで、次のように選択します。、 **Activate**ボタンをクリックします。  
  
7.  **ソリューションのアクティブ化** ダイアログ ボックスで、リボンで、選択、**アクティブ化**もう一度ボタンをクリックします。  
  
     **状態**列に、**ソリューション ギャラリー**ページは、アプリケーションがアクティブであることを示します。  
  
## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>リモート SharePoint サーバー上のセキュリティで保護された SharePoint ソリューションをアップグレードするには  
 次のプロセスを使用すると、アプリケーションに変更を行った後にアップグレードする場合、SharePoint のサンド ボックス ソリューションは、リモート サーバーで既にパブリッシュされて、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。  
  
1.  SharePoint のパッケージの名前を変更[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 この場合に**ソリューション エクスプ ローラー**パッケージを開きます。 表示される、**パッケージ エクスプ ローラー**します。  
  
2.  **パッケージ エクスプ ローラー**の**名前**ボックスに、パッケージ名を一意の名前に変更します。  
  
3.  プロジェクトを保存します。  
  
4.  **ソリューション エクスプ ローラー**、プロジェクトのショートカット メニューを開き、選択し、**発行**します。  
  
5.  **発行** ダイアログ ボックスで、選択、 **SharePoint サイトに発行**オプション ボタンと、ソリューションが保存されているリモート サーバーの URL が不足している場合は、入力します。  
  
6.  選択、**発行した後、ブラウザーでソリューション ギャラリー ページを開く**のソリューションの一覧を表示するオプション ボタン、**ソリューション ギャラリー**発行後のページ。  
  
7.  選択、**発行**ボタンをクリックします。  
  
8.  ユーザー認証が必要な場合、リモート サーバーにログオンします。  
  
     ログインして場合、リモート サーバーに最近、認証は必要ありません。  
  
     SharePoint サーバーで同じ名前を持つアプリケーションの古いバージョンがまだ存在する場合は、SharePoint サーバーに同じ名前のパッケージが既に存在するエラーが発生します。 パブリッシュする前に一意の名前に、パッケージの名前を変更する必要があります。  
  
9. SharePoint では、新しいアプリケーションを選択し、その後、リボンで、次のように選択します。、**アップグレード**ボタンをクリックします。  
  
10. **ソリューションのアップグレード** ダイアログ ボックスで、リボンで、選択、**アップグレード**もう一度ボタンをクリックします。 **状態**列に、**ソリューション ギャラリー**ページは、アプリケーションがアクティブであるを示すようになりました。  
  
     ソリューションの古いバージョンが非アクティブ化、ソリューションの新しいバージョンが以前のソリューションから保持されているデータをアップグレードし、SharePoint で新しいソリューションを有効にします。  
  
## <a name="see-also"></a>関連項目
 [方法: 配置し、SharePoint ソリューションをローカル SharePoint サイトに発行します。](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [SharePoint ソリューション パッケージを作成します。](../sharepoint/creating-sharepoint-solution-packages.md)   
 [方法: SharePoint ソリューション パッケージをカスタマイズします。](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [方法: 追加して、パッケージ デザイナーを使用して機能と、パッケージにアイテムを削除](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
