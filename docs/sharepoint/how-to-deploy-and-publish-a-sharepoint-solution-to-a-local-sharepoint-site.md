---
title: '方法: 展開し、SharePoint ソリューションをローカル SharePoint サイトにパブリッシュ |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
ms.openlocfilehash: 5c4f7e347f9cea3a73ab5326b42720a1b2c33529
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>方法: SharePoint ソリューションをローカルの SharePoint サイトに配置および発行する
  展開したり、開発用コンピューター上のローカル SharePoint サーバーに SharePoint ソリューションを発行することができます。 展開プロセスは、SharePoint サーバーに .wsp ファイルをコピー、ソリューションをインストールし、機能をアクティブにし、します。 発行プロセスは、SharePoint サーバーに .wsp ファイルをコピーおよびインストールのみです。 SharePoint で有効にすることがアクティブ化する必要があります手動でします。  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>ローカルの SharePoint サーバーに SharePoint ソリューションを展開するには  
  
1.  **ソリューション エクスプ ローラー**、配置するプロジェクトを選択します。  
  
2.  メニュー バーで、次のように選択します。**ビルド**、**ソリューションの配置**です。  
  
     .Wsp ファイルが作成され、ローカルの SharePoint サーバーにインストールします。 また、機能がアクティブにします。  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>SharePoint ソリューションをローカル SharePoint サーバーに発行するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、SharePoint プロジェクトを発行し、選択するを**発行**です。  
  
2.  **発行** ダイアログ ボックスで、選択、**ファイル システムに公開**オプション ボタンをクリックします。  
  
3.  **ターゲットの場所**テキスト ボックスは、ローカル パスを入力し、、**発行**ボタンをクリックします。  
  
     Visual Studio で発行の進行状況が表示される**出力**ウィンドウです。 プロセスが完了したら、ソリューション (.wsp) ファイルはローカル SharePoint サーバーにインストールされます。 ただし、その必要がありますまだアクティブに SharePoint で使用します。 ソリューション ファイルが既に存在する場合、エラーが発生し、既存のファイルを上書きするかどうかを確認します。 パッケージをアップグレードする方法についてでリモート パッケージのアップグレードに関するセクションを参照して[する方法: 配置、発行、およびリモート サーバー上の SharePoint ソリューションのアップグレード](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: 配置、発行、およびリモート サーバー上で SharePoint ソリューションのアップグレード](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [SharePoint ソリューション パッケージの作成](../sharepoint/creating-sharepoint-solution-packages.md)   
 [方法: SharePoint ソリューション パッケージをカスタマイズします。](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [方法: パッケージ デザイナーを使用してパッケージのフィーチャーおよび項目を追加および削除する](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  