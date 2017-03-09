---
title: "アプリケーション、サービス、およびコンポーネントの配置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - ".NET アプリケーション, 配置"
  - "コンポーネント [.NET Framework], 配置"
  - "コンポーネント [Visual Studio], 配置"
  - "配置 (アプリケーションを) [Visual Studio]"
  - "配置 (アプリケーションを) [Visual Studio], 配置の概要 (アプリケーションの)"
  - "インストーラー"
  - "発行"
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# アプリケーション、サービス、およびコンポーネントの配置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

アプリケーション、サービス、またはコンポーネントを配置すると、他のコンピューターのデバイス、サーバー、またはクラウドに対してインストールするために、それらを配布することになります。  必要な配置の種類に合わせて、Visual Studio で適切な手法を選択します。  
  
 次の表に、さまざまな配置シナリオに関する説明と、それらのシナリオを正常に完了する詳細な方法へのリンクを示します。  
  
## このセクションの内容  
  
|配置シナリオ|関連する参照先|  
|------------|-------------|  
|**\[Publish to the cloud\] \(クラウドに発行\)** Visual Studio を使用して、アプリケーション、サービス、およびデータをあらゆる場所から Microsoft Azure に配置することができます。|[Visual Studio から Azure クラウド サービスへの発行](http://msdn.microsoft.com/library/windowsazure/ee460772.aspx)|  
|**\[Publish a Windows Store app\] \(Windows ストア アプリの発行\)**: アプリケーションを簡単にビルドおよび送信し、Windows ストアから世界中の顧客に販売することができます。|[Windows ストア アプリのパッケージ化、配置、およびクエリ](http://msdn.microsoft.com/library/hh446593\(v=vs.85\).aspx)|  
|**\[Publish a Windows Phone app\] \(Windows Phone アプリの発行\)**: 認定を受ける目的で、新しいアプリケーションまたは修正プログラムを Windows Phone デベロッパー センターに送信することができます。|[Windows Phone アプリの公開](http://dev.windowsphone.com/ja-jp/publish)|  
|**ASP.NET アプリケーションまたはサービスの配置:** ASP.NET アプリケーションおよびサービスは、多数の異なる方法で配置できます。|[ASP.NET Web アプリケーションおよびサービスを配置する](http://www.asp.net/aspnet/overview/deployment)|  
|**\[Deploy a LightSwitch application or service\] \(LightSwitch アプリケーションまたはサービスの配置\)**: LightSwitch を使用してアプリケーションと OData サービスを作成した後、Web サーバーまたは Microsoft Azure にそれらを配置できます。|[LightSwitch アプリケーションの配置](../Topic/Deploying%20LightSwitch%20Applications.md)|  
|**\[Publish an app for SharePoint\] \(SharePoint アプリケーションの発行\)**: Office ストアまたは組織内部向けのアプリケーション カタログに対して、SharePoint アプリケーションを発行できます。|[\[方法\]: Visual Studio を使用して SharePoint 用アプリを公開する](http://msdn.microsoft.com/JA-jp/library/office/jj220044\(v=office.15\).aspx)|  
|**\[Publish an app for Office\] \(Office アプリケーションの発行\)**: Office ストアまたは組織内部向けのアプリケーション カタログに対して、Office アプリケーションを発行できます。|[Office 用アプリの発行](http://msdn.microsoft.com/library/office/fp123515.aspx)|  
|**\[Deploy a WCF service\] \(WCF サービスの配置\)**: 他のアプリケーションは、Web サーバーに配置した WCF RIA サービスを使用できます。|[RIA サービス ソリューションの配置に関するガイド](http://msdn.microsoft.com/library/ff426912\(v=vs.91\).aspx)|  
|**\[Deploy an OData service\] \(OData サービスの配置\)**: 他のアプリケーションは、Web サーバーに配置した OData サービスを使用できます。|[方法: LightSwitch OData サービスを配置する](http://msdn.microsoft.com/library/hh973447.aspx)|  
|**\[Deploy a desktop application\] \(デスクトップ アプリケーションの配置\)** : ClickOnce 配置を使用し、Web サーバーまたはネットワーク ファイル共有に対してデスクトップ アプリケーションを発行することができます。  その後、ユーザーはシングル クリックでアプリケーションをインストールできます。|[ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)|  
|**\[Create a setup program\] \(セットアップ プログラムを作成します\)**: 無料の InstallShield Limited Edition を使用して、セットアップ プログラムを作成できます。|[InstallShield Limited Edition](../deployment/installshield-limited-edition.md)|  
|**\[Maintain an existing setup program\] \(既存のセットアップ プログラムの維持\)**: Visual Studio Installer Projects Extension をインストールして、以前のバージョンのVisual Studio で作成したセットアップ プログラムを使用し続けます。|[Visual Studio Installer Projects Extension](http://blogs.msdn.com/b/visualstudio/archive/2014/04/17/visual-studio-installer-projects-extension.aspx)<br /><br /> インストーラー プロジェクトについては、「[Visual Studio インストーラーの配置](http://msdn.microsoft.com/library/2kt85ked\(v=vs.100\).aspx)」を参照してください。|  
|**\[Deploy a Visual C\+\+ application\] \(Visual C\+\+ アプリケーションの配置\)**: 集中配置、ローカル配置、または静的リンクを使用して、アプリケーションと共に Visual C\+\+ ランタイムを配置できます。|[デスクトップ アプリケーションの配置 \(Visual C\+\+\)](http://msdn.microsoft.com/library/zebw5zk9.aspx)|  
|**\[Deploy an application for testing\] \(テスト用アプリケーションの配置\)**: 仮想環境にアプリケーションを配置すると、より高度な開発およびテストを有効にできます。|[ラボ環境でのテスト](/devops-test-docs/test/test-on-a-lab-environment)|  
|**\[必要コンポーネントのインストール\]**: ブートストラップと呼ばれる一般的なインストーラーを構成すると、デスクトップ アプリケーションの必須コンポーネントをインストールできます。|[アプリケーション配置の必要条件](../deployment/application-deployment-prerequisites.md)|