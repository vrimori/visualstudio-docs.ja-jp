---
title: '方法: 展開し、SharePoint ソリューションをローカル SharePoint サイトにパブリッシュ |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
ms.openlocfilehash: 8dd0dd78ca8f6b6f9791a657546cabc0d098b563
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835326"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>方法: 配置し、SharePoint ソリューションをローカル SharePoint サイトに発行します。
  展開するか、開発用コンピューターにローカル SharePoint サーバーに SharePoint ソリューションを発行します。 展開プロセスのコピー、 *.wsp* SharePoint サーバーにファイルが、ソリューションをインストールして、機能をアクティブにします。 コピーのみを処理する、発行、 *.wsp*ファイルを SharePoint サーバーにし、そのインストールします。 SharePoint で有効にすることがアクティブ化する必要があります手動でします。  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>ローカルの SharePoint サーバーに SharePoint ソリューションをデプロイするには  
  
1.  **ソリューション エクスプ ローラー**、デプロイするプロジェクトを選択します。  
  
2.  メニュー バーで、**ビルド**、**ソリューションの配置**します。  
  
     *.Wsp*ファイルが作成され、ローカルの SharePoint サーバーにインストールします。 また、機能がアクティブ化されます。  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>SharePoint ソリューションをローカル SharePoint サーバーに発行するには  
  
1.  **ソリューション エクスプ ローラー**、クリックして発行する SharePoint プロジェクトのショートカット メニューを開き**発行**します。  
  
2.  **発行** ダイアログ ボックスで、選択、**ファイル システムに公開**オプション ボタンをクリックします。  
  
3.  **ターゲットの場所**テキスト ボックスに、ローカル パスを入力し、、**発行**ボタンをクリックします。  
  
     Visual Studio で発行の進行状況が表示されます。**出力**ウィンドウ。 プロセスが終了すると、ソリューション (*.wsp*) ファイルがローカルの SharePoint サーバーにインストールされています。 ただし、まだがアクティブ化があります SharePoint で使用します。 ソリューション ファイルが既に存在する場合、エラーが発生し、既存のファイルを上書きするかどうかを確認します。 パッケージのアップグレード方法の詳細についてでリモート パッケージのアップグレードに関するセクションをご覧ください。[方法。配置、発行、およびリモート サーバー上で SharePoint ソリューションのアップグレード](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)します。  
  
## <a name="see-also"></a>関連項目
 [方法: 配置、発行、およびリモート サーバー上で SharePoint ソリューションのアップグレード](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [SharePoint ソリューション パッケージを作成します。](../sharepoint/creating-sharepoint-solution-packages.md)   
 [方法: SharePoint ソリューション パッケージをカスタマイズします。](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [方法: 追加して、パッケージ デザイナーを使用して機能と、パッケージにアイテムを削除](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
