---
title: ClickOnce 配置ストラテジの選択 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 54bf4f58a4cfe8622e12b3808ea9f36c8cf1ee49
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175631"
---
# <a name="choosing-a-clickonce-deployment-strategy"></a>ClickOnce 配置ストラテジの選択
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションを配置する際には 3 つのストラテジがあり、どれを選択するかは主として配置するアプリケーションの種類によって決まります。 この 3 つの配置ストラテジは次のとおりです。  
  
-   Web またはネットワーク共有からのインストール  
  
-   CD からのインストール  
  
-   Web またはネットワーク共有からのアプリケーションの起動  
  
    > [!NOTE]
    >  配置ストラテジを選択するだけでなく、アプリケーションの更新プログラムを提供するストラテジも選択する必要があります。 詳細については、次を参照してください。 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)します。  
  
## <a name="install-from-the-web-or-a-network-share"></a>Web またはネットワーク共有からのインストール  
 このストラテジを使用すると、アプリケーションが Web サーバーまたはネットワーク ファイル共有に配置されます。 エンド ユーザーがアプリケーションをインストールするときは、Web ページのアイコンをクリックするか、ファイル共有のアイコンをダブルクリックします。 これで、アプリケーションがユーザーのコンピューターにダウンロードされ、インストールされて起動します。 項目を追加、**開始**メニューと**プログラム追加と削除**で**コントロール パネルの**です。  
  
 このストラテジはネットワーク接続に依存するため、ローカル エリア ネットワークや高速インターネット接続にアクセスできるユーザーのコンピューターにアプリケーションを配置する場合に最適です。  
  
 アプリケーションを Web から配置する場合は、そのアプリケーションが URL を使用してアクティブ化されるときに、アプリケーションに引数を渡すことができます。 詳細については、次を参照してください。[方法: オンライン ClickOnce アプリケーションでのクエリ文字列情報の取得](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)します。 ここで説明されている他の方法でアクティブ化されるアプリケーションには、引数を渡すことができません。  
  
 この配置ストラテジを有効にする[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、 をクリックして**From the Web**または**UNC パスまたはファイル共有**上、**のインストール方法**発行ウィザードのページ。  
  
 これは既定の配置ストラテジです。  
  
## <a name="install-from-a-cd"></a>CD からのインストール  
 このストラテジを使用すると、CD-ROM や DVD などのリムーバブル メディアにアプリケーションが配置されます。 項目を追加するがインストールされ、開始、ユーザーがアプリケーションをインストールする前のオプションと同様、**開始**メニューと**プログラム追加と削除**で**コントロールパネル**します。  
  
 このストラテジは、永続的なネットワーク接続を利用していないユーザーや低帯域幅接続を利用しているユーザーに対してアプリケーションを配置する場合に最適です。 アプリケーションはリムーバブル メディアからインストールするため、インストールの際にネットワーク接続は不要ですが、アプリケーションの更新には、ネットワーク接続が必要です。  
  
 この配置ストラテジを有効にする[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、 をクリックして**から CD-ROM または DVD-ROM**上、**のインストール方法**発行ウィザードのページ。  
  
 この配置ストラテジを手動で有効にするには、変更、 **deploymentProvider**配置マニフェスト内のタグ。 (として Visual Studio で、このプロパティが公開されている**インストール URL**上、**発行**プロジェクト デザイナーのページ。 Mage.exe では**開始場所**)。  
  
## <a name="start-the-application-from-the-web-or-a-network-share"></a>Web またはネットワーク共有からのアプリケーションの起動  
 このストラテジは 1 番目のストラテジに似ていますが、アプリケーションが Web アプリケーションのように動作する点が異なります。 ユーザーが Web ページのリンクをクリック (またはファイル共有のアイコンをダブルクリック) すると、アプリケーションが起動します。 ローカルのコンピューターで使用できなくユーザー アプリケーションを閉じると、何も追加、**開始**メニューまたは**プログラム追加と削除**で**コントロール パネルの**です。  
  
> [!NOTE]
>  厳密には、アプリケーションは、Web アプリケーションが Web キャッシュにダウンロードされるのと同様に、ローカル コンピューターのアプリケーション キャッシュにダウンロードされ、インストールされます。 Web キャッシュの場合と同様に、ファイルは最終的にアプリケーション キャッシュから削除されます。 ただし、ユーザーの目には、アプリケーションが Web またはファイル共有から実行されるように映ります。  
  
 このストラテジは、使用頻度の低いアプリケーション (通常、年に 1 回しか実行されない従業員福利ツールなど) に最適です。  
  
 この配置ストラテジを有効にする[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、 をクリックして**アプリケーションをインストールしないでください**上、**インストールまたは実行から Web**発行ウィザードのページ。  
  
 この配置ストラテジを手動で有効にするには、変更、**インストール**配置マニフェスト内のタグ。 (その値を指定できます**true**または**false**します。 Mage.exe で、使用、**オンラインのみ**オプション、**アプリケーションの種類**一覧です)。  
  
## <a name="web-browser-support"></a>Web ブラウザー サポート  
 .NET Framework 3.5 を対象とするアプリケーションは、任意のブラウザーを使用してインストールできます。  
  
 .NET Framework 2.0 を対象とするアプリケーションは、Internet Explorer が必要です。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce の更新方法を選択します。](../deployment/choosing-a-clickonce-update-strategy.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)



