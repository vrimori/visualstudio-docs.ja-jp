---
title: "ClickOnce とアプリケーションの設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 862f51aa7d124c3dbaa6514b666d74c26334e299
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="clickonce-and-application-settings"></a>ClickOnce とアプリケーション設定
Windows フォームのアプリケーション設定を簡単を作成、格納、およびカスタム アプリケーションと、クライアント上のユーザー設定を管理できます。 次のドキュメントでは、ClickOnce アプリケーションにおけるアプリケーション設定ファイルのしくみし、ユーザーは、次のバージョンにアップグレードしたときに、ClickOnce が設定を移行する方法について説明します。  
  
 以下の情報が既定のアプリケーションの設定プロバイダーにのみ適用されます、<xref:System.Configuration.LocalFileSettingsProvider>クラスです。 カスタム プロバイダーを提供する場合、そのプロバイダーは、そのデータを格納するしくみと、バージョン間で設定をアップグレードする方法に判断されます。 アプリケーション設定プロバイダーの詳細については、次を参照してください。[アプリケーション設定アーキテクチャ](/dotnet/framework/winforms/advanced/application-settings-architecture)です。  
  
## <a name="application-settings-files"></a>アプリケーション設定ファイル  
 アプリケーションの設定は、2 つのファイルを消費:*アプリ*.exe.config に変更し、user.config 場所*アプリ*Windows フォーム アプリケーションの名前を指定します。 user.config がアプリケーションには、ユーザー スコープ設定が格納されて、クライアント、最初の時間に作成されます。 *アプリ*.exe.config でこれに対し、が存在して展開する前に設定の既定値を定義する場合。 Visual Studio はこのファイルは自動的に追加するときにその**発行**コマンド。 このファイルに含まれることを確認する必要があります Mage.exe または MageUI.exe を使用して ClickOnce アプリケーションを作成する場合、アプリケーション マニフェストを作成するときに、アプリケーションの他のファイルです。  
  
 ClickOnce を使用して、アプリケーションの展開されていない Windows フォーム アプリケーションで*アプリ*. ユーザーの user.config ファイルが格納されているアプリケーション ディレクトリに *.exe.config ファイルが格納されている**Documents and Settings**フォルダーです。 ClickOnce アプリケーションに*アプリ*.exe.config に変更は、ClickOnce アプリケーションのキャッシュ内でアプリケーションのディレクトリに存在しており、user.config がそのアプリケーションの ClickOnce データ ディレクトリ内に存在します。  
  
 アプリケーションの設定により、セーフの読み取りアクセスをアプリケーションの展開方法に関係なく*アプリ*.exe.config に変更、および user.config にセーフの読み取り/書き込みアクセス。  
  
 ClickOnce アプリケーションには、アプリケーションの設定で使用される構成ファイルのサイズは、ClickOnce キャッシュのサイズによって制限されます。 詳細については、次を参照してください。 [ClickOnce キャッシュの概要](../deployment/clickonce-cache-overview.md)です。  
  
## <a name="version-upgrades"></a>バージョンのアップグレード  
 ClickOnce アプリケーションの各バージョンは、その他のすべてのバージョンから分離されているのと同様、ClickOnce アプリケーションのアプリケーションの設定は、他のバージョンでも同様の設定から分離されます。 アプリケーションの新しいバージョンにアップグレードする、ユーザー、アプリケーションの設定は新しい設定ファイルのセットに設定をマージ、更新されたバージョンに付属している設定に対して最新 (番号が最大) のバージョンの設定を比較します。  
  
 次の表では、アプリケーションの設定はコピーする設定を決定する方法について説明します。  
  
|変更の種類|アップグレード アクション|  
|--------------------|--------------------|  
|追加設定*アプリ*.exe.config に変更。|新しい設定が、現在のバージョンにマージ*アプリ*.exe.config に変更。|  
|設定から削除*アプリ*.exe.config に変更。|現在のバージョンから、以前の設定が削除された*アプリ*.exe.config に変更。|  
|設定の既定値が変更されています。ローカルの設定がまだ user.config で元の既定値に設定|設定が、値として新しい既定値は、現在のバージョンの user.config にマージします。|  
|設定の既定値が変更されています。user.config で既定以外に設定|設定が保持される既定以外の値と現在のバージョンの user.config にマージします。|  
  
 ラッパー クラス アプリケーションの設定を作成して更新ロジックをカスタマイズする場合は、上書き、<xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A>メソッドです。  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce と設定のローミング  
 ClickOnce では機能しませんローミング設定は、これにより、ネットワーク上のコンピューター間で後に、設定ファイルです。 設定をローミングする場合は、ネットワーク経由での設定を格納するアプリケーションの設定プロバイダーを実装するか、リモート コンピューター上の設定を格納するためには、独自のカスタム設定クラスを開発する必要があります。 設定プロバイダーの詳細については、次を参照してください。[アプリケーション設定アーキテクチャ](/dotnet/framework/winforms/advanced/application-settings-architecture)です。  
  
## <a name="see-also"></a>参照  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [アプリケーション設定の概要](/dotnet/framework/winforms/advanced/application-settings-overview)   
 [ClickOnce キャッシュの概要](../deployment/clickonce-cache-overview.md)   
 [ClickOnce アプリケーションにおけるローカル データおよびリモート データへのアクセス](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)