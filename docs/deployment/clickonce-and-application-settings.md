---
title: ClickOnce とアプリケーションの設定 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2904b4a8fbb6e4ec3fd831251b5675f2047b6368
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922705"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce とアプリケーション設定
Windows フォームのアプリケーション設定を簡単に作成、保存、およびカスタム アプリケーションとクライアント上のユーザー設定を管理します。 次のドキュメントでは、ClickOnce アプリケーションでのアプリケーション設定ファイルのしくみし、ユーザーが次のバージョンにアップグレードしたときに、ClickOnce が設定を移行する方法について説明します。  
  
 以下の情報は、既定のアプリケーション設定プロバイダーにのみ適用されます、 \<xref:System.Configuration.LocalFileSettingsProvider > クラス。 カスタム プロバイダーを指定すると、そのデータを格納する方法と、バージョン間で設定をアップグレードする方法、そのプロバイダーが判断されます。 アプリケーション設定プロバイダーの詳細については、次を参照してください。[アプリケーション設定アーキテクチャ](/dotnet/framework/winforms/advanced/application-settings-architecture)します。  
  
## <a name="application-settings-files"></a>アプリケーション設定ファイル  
 アプリケーションの設定は、2 つのファイルを使用: *\<アプリ >. exe.config*と*user.config*ここで、*アプリ*Windows フォーム アプリケーションの名前を指定します。 *user.config*アプリケーションには、ユーザー スコープの設定が格納されます。 クライアントの最初の時間に作成されます。 *\<アプリ >. exe.config*設定の既定値を定義する場合は展開する前にこれに対し、存在されます。 Visual Studio は、このファイルに自動的に使用すると、**発行**コマンド。 使用して ClickOnce アプリケーションを作成する場合*Mage.exe*または*MageUI.exe*、このファイルに含まれていることを確認しておく必要があります、アプリケーション マニフェストを設定するときに、アプリケーションの他のファイル。  
  
 ClickOnce を使用して、アプリケーションの展開されていない Windows フォーム アプリケーションで*\<アプリ >. exe.config*アプリケーション ディレクトリに保存されているときに、 *user.config*ファイルが格納されています。ユーザーの**Documents and Settings**フォルダー。 ClickOnce アプリケーションで*\<アプリ >. exe.config* 、ClickOnce アプリケーション キャッシュ内のアプリケーション ディレクトリ内に存在し、 *user.config* ClickOnce データ ディレクトリにそのアプリケーション。  
  
 アプリケーションをデプロイする方法に関係なくセーフの読み取りアクセス権をアプリケーション設定*\<アプリ >. exe.config*、およびセーフの読み取り/書き込みアクセスを*user.config*します。  
  
 ClickOnce アプリケーションでは、アプリケーションの設定で使用される構成ファイルのサイズは、ClickOnce キャッシュのサイズによって制限されます。 詳細については、次を参照してください。 [ClickOnce キャッシュの概要](../deployment/clickonce-cache-overview.md)します。  
  
## <a name="version-upgrades"></a>バージョンのアップグレード  
 ClickOnce アプリケーションの各バージョンが他のすべてのバージョンから分離されたのと同様、ClickOnce アプリケーションのアプリケーションの設定は、その他のバージョンも設定から分離されます。 ユーザーは、アプリケーションの以降のバージョンにアップグレードして、アプリケーションの設定は最も新しい (最も高い数字) バージョンの設定、更新されたバージョンとマージに新しい設定ファイルのセットの設定で指定した設定を比較します。  
  
 次の表では、アプリケーションの設定はコピーする設定を決定する方法について説明します。  
  
|変更の種類|アップグレード アクション|  
|--------------------|--------------------|  
|設定に追加*\<アプリ >. exe.config*|新しい設定が現在のバージョンにマージされる*\<アプリ >. exe.config*|  
|設定から削除*\<アプリ >. exe.config*|現在のバージョンから、以前の設定が削除された*\<アプリ >. exe.config*|  
|設定の既定値が変更されています。ローカル設定は、引き続き元の既定値に設定*user.config*|設定が現在のバージョンにマージされる*user.config*値として新しい既定値|  
|設定の既定値が変更されています。既定以外に設定されて*user.config*|設定が現在のバージョンにマージされる*user.config*で既定以外の値が保持されます|  
  
オーバーライドすることができます独自のアプリケーション設定ラッパー クラスを作成し、更新ロジックをカスタマイズする場合、 \<xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A > メソッドです。  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce とローミングの設定  
 ClickOnce 機能しません、ローミングの設定で、設定ファイルをネットワーク上のコンピューター間で利用できます。 ローミングの設定が必要な場合は、ネットワーク経由で設定を格納するアプリケーション設定プロバイダーを実装するか、リモート コンピューター上の設定を格納するため、独自のカスタム設定クラスを開発する必要があります。 設定プロバイダーの詳細については、次を参照してください。[アプリケーション設定アーキテクチャ](/dotnet/framework/winforms/advanced/application-settings-architecture)します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [アプリケーション設定の概要](/dotnet/framework/winforms/advanced/application-settings-overview)   
 [ClickOnce キャッシュの概要](../deployment/clickonce-cache-overview.md)   
 [ClickOnce アプリケーションにおけるローカル データおよびリモート データへのアクセス](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)