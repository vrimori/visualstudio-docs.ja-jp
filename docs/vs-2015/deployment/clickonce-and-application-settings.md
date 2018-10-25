---
title: ClickOnce とアプリケーションの設定 |Microsoft Docs
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
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 29f51960ad953318c8d9de749f28f684128e52ef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176987"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce とアプリケーション設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows フォームのアプリケーション設定を簡単に作成、保存、およびカスタム アプリケーションとクライアント上のユーザー設定を管理します。 次のドキュメントでは、ClickOnce アプリケーションでのアプリケーション設定ファイルのしくみし、ユーザーが次のバージョンにアップグレードしたときに、ClickOnce が設定を移行する方法について説明します。  
  
 以下の情報は、既定のアプリケーション設定プロバイダーにのみ適用されます、<xref:System.Configuration.LocalFileSettingsProvider>クラス。 カスタム プロバイダーを指定すると、そのデータを格納する方法と、バージョン間で設定をアップグレードする方法、そのプロバイダーが判断されます。 アプリケーション設定プロバイダーの詳細については、次を参照してください。[アプリケーション設定アーキテクチャ](http://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562)します。  
  
## <a name="application-settings-files"></a>アプリケーション設定ファイル  
 アプリケーションの設定は、2 つのファイルを使用:*アプリ*. exe.config と user.config、場所*アプリ*Windows フォーム アプリケーションの名前を指定します。 user.config がアプリケーションには、ユーザー スコープの設定が格納されます。 クライアントの最初の時間に作成されます。 *アプリ*.exe.config にこれに対し、存在展開する前に既定値の設定を定義する場合。 Visual Studio は、このファイルに自動的に使用すると、**発行**コマンド。 このファイルに含まれることを確認しておく必要があります Mage.exe または MageUI.exe を使用して ClickOnce アプリケーションを作成する場合、アプリケーション マニフェストを設定するときに、アプリケーションの他のファイル。  
  
 ClickOnce を使用して、アプリケーションの展開されていない Windows フォーム アプリケーションで*アプリ*. はユーザーの user.config ファイルが格納されているアプリケーション ディレクトリに exe.config ファイルが格納されている**Documents and Settings**フォルダー。 ClickOnce アプリケーションで*アプリ*。 exe.config が、ClickOnce アプリケーション キャッシュ内でアプリケーションのディレクトリに存在しており、そのアプリケーションの ClickOnce データ ディレクトリの user.config が存在します。  
  
 アプリケーションの設定により、セーフの読み取りアクセスをアプリケーションをデプロイする方法に関係なく*アプリ*.exe.config にと user.config への安全な読み取り/書き込みアクセス。  
  
 ClickOnce アプリケーションでは、アプリケーションの設定で使用される構成ファイルのサイズは、ClickOnce キャッシュのサイズによって制限されます。 詳細については、次を参照してください。 [ClickOnce キャッシュの概要](../deployment/clickonce-cache-overview.md)します。  
  
## <a name="version-upgrades"></a>バージョンのアップグレード  
 ClickOnce アプリケーションの各バージョンが他のすべてのバージョンから分離されたのと同様、ClickOnce アプリケーションのアプリケーションの設定は、その他のバージョンも設定から分離されます。 ユーザーは、アプリケーションの以降のバージョンにアップグレードして、アプリケーションの設定は最も新しい (最も高い数字) バージョンの設定、更新されたバージョンとマージに新しい設定ファイルのセットの設定で指定した設定を比較します。  
  
 次の表では、アプリケーションの設定はコピーする設定を決定する方法について説明します。  
  
|変更の種類|アップグレード アクション|  
|--------------------|--------------------|  
|設定に追加*アプリ*exe.config。|新しい設定が現在のバージョンにマージされる*アプリ*exe.config。|  
|設定から削除*アプリ*exe.config。|現在のバージョンから、以前の設定が削除された*アプリ*exe.config。|  
|設定の既定値が変更されています。ローカル設定は、まだ user.config で元の既定値に設定|設定は、値として、新しい既定値は、現在のバージョンの user.config にマージされます。|  
|設定の既定値が変更されています。設定は user.config で既定以外に設定|既定以外の値が保持されますが結合に、現在のバージョンの user.config 設定|  
  
 オーバーライドすることができます独自のアプリケーション設定ラッパー クラスを作成し、更新ロジックをカスタマイズする場合、<xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A>メソッド。  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce とローミングの設定  
 ClickOnce 機能しません、ローミングの設定で、設定ファイルをネットワーク上のコンピューター間で利用できます。 ローミングの設定が必要な場合は、ネットワーク経由で設定を格納するアプリケーション設定プロバイダーを実装するか、リモート コンピューター上の設定を格納するため、独自のカスタム設定クラスを開発する必要があります。 設定プロバイダーの詳細については、次を参照してください。[アプリケーション設定アーキテクチャ](http://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562)します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [アプリケーション設定の概要](http://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc)   
 [ClickOnce キャッシュの概要](../deployment/clickonce-cache-overview.md)   
 [ClickOnce アプリケーションにおけるローカル データおよびリモート データへのアクセス](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)



