---
title: アプリケーション、サービス、およびコンポーネントの配置 |Microsoft Docs
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
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: acc3383b2d76361c8e6994641770513c4e552b8d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276765"
---
# <a name="deploying-applications-services-and-components"></a>アプリケーション、サービス、およびコンポーネントの配置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

アプリケーション、サービス、またはコンポーネントを配置すると、他のコンピューターのデバイス、サーバー、またはクラウドに対してインストールするために、それらを配布することになります。 必要な配置の種類に合わせて、Visual Studio で適切な手法を選択します。  
  
 次の表に、さまざまな配置シナリオに関する説明と、それらのシナリオを正常に完了する詳細な方法へのリンクを示します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|配置シナリオ|関連する参照先|  
|-------------------------|------------------------|  
|**クラウドへの公開:** 行うことができますアプリケーション、サービス、およびデータから使用可能な Microsoft Azure に配置する Visual Studio を使用して任意の場所。|[Microsoft Azure にアプリケーションの発行](http://msdn.microsoft.com/library/windowsazure/ee460772.aspx)|  
|**Windows ストア アプリの発行:** 簡単に作成を送信して、世界各地のお客様に、Windows ストアからアプリを販売します。|[パッケージ化、展開、および Windows ストア アプリのクエリ](http://msdn.microsoft.com/library/hh446593\(v=vs.85\).aspx)|  
|**Windows Phone アプリの発行:** 新しいアプリまたは既存のアプリ、Windows Phone デベロッパー センターの証明書の更新を送信することができます。|[Windows Phone のアプリを発行します。](http://dev.windowsphone.com/publish)|  
|**ASP.NET アプリケーションまたはサービスのデプロイ:** 多数の異なる方法で ASP.NET アプリケーションおよびサービスをデプロイすることができます。|[ASP.NET web アプリケーションとサービスの展開](http://www.asp.net/aspnet/overview/deployment)|  
|**LightSwitch アプリケーションまたはサービスのデプロイ:** LightSwitch を使用して、アプリケーションと OData サービスを作成した後は展開する web サーバーまたは Microsoft Azure です。|[LightSwitch アプリケーションの配置](http://msdn.microsoft.com/library/4818d933-295c-4ecc-9148-7ad9ca28dcdb)|  
|**SharePoint 用アプリの発行:** for SharePoint を Office ストアまたは組織内部のアプリ カタログ アプリケーションを発行できます。|[Visual Studio を使用して SharePoint アプリケーションを発行します。](http://msdn.microsoft.com/library/office/jj220044\(v=office.15\).aspx)|  
|**Office 用アプリの発行:** Office Office ストアまたは組織内部のアプリケーション カタログのアプリケーションを発行できます。|[Office 用アプリの発行](http://msdn.microsoft.com/library/office/fp123515.aspx)|  
|**WCF サービスのデプロイ:** 他のアプリケーションが web サーバーに配置した WCF RIA サービスを使用できます。|[展開の WCF RIA サービス ソリューション](http://msdn.microsoft.com/library/ff426912\(v=vs.91\).aspx)|  
|**OData サービスのデプロイ:** 他のアプリケーションが web サーバーに配置した OData サービスを使用できます。|[OData サービスをデプロイします。](http://msdn.microsoft.com/library/hh973447.aspx)|  
|**デスクトップ アプリケーションのデプロイ:** ClickOnce 配置を使用すると、web サーバーまたはネットワーク ファイル共有をデスクトップ アプリケーションを発行することができます。 その後、ユーザーはシングル クリックでアプリケーションをインストールできます。|[ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)|  
|**セットアップ プログラムを作成します。** 無料の InstallShield Limited Edition では、を使用して、セットアップ プログラムを作成することができます。|[InstallShield Limited Edition](../deployment/installshield-limited-edition.md)|  
|**既存のセットアップ プログラムの管理:** Visual Studio Installer Projects Extension をインストールすることで Visual Studio の以前のバージョンで作成されたセットアップ プログラムを使用して続行します。|[Visual Studio Installer Projects Extension](http://blogs.msdn.com/b/visualstudio/archive/2014/04/17/visual-studio-installer-projects-extension.aspx)<br /><br /> インストーラー プロジェクトについては、ここで使用可能な: [Visual Studio インストーラーの配置](http://msdn.microsoft.com/library/2kt85ked\(v=vs.100\).aspx)|  
|**Visual C アプリケーションのデプロイ:** 集中配置、ローカル配置、または静的リンクを使用して、アプリケーションと共に Visual C ランタイムを配置することができます。|[ネイティブ デスクトップ アプリケーションの配置 (Visual C++)](http://msdn.microsoft.com/library/zebw5zk9.aspx)|  
|**テスト対象のアプリケーションのデプロイ:** より高度な開発と仮想環境にアプリケーションを配置してテストを有効にすることができます。|[ラボ環境でのテスト](http://msdn.microsoft.com/library/14ba54c8-a158-4a6e-b00a-b00ae960feb8)|  
|**インストールの前提条件:** ブートス トラップと呼ばれる一般的なインストーラーを構成することでデスクトップ アプリケーションに必要なコンポーネントをインストールすることができます。|[アプリケーション配置の必要条件](../deployment/application-deployment-prerequisites.md)|





