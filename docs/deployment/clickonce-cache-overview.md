---
title: "ClickOnce キャッシュの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce アプリケーション, キャッシュ"
  - "ClickOnce 配置, キャッシュ"
  - "Windows アプリケーション, ClickOnce 配置"
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# ClickOnce キャッシュの概要
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ローカルにインストールされているか、またはオンラインでホストされているかに関係なく、すべての [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、クライアント コンピューターの [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション *キャッシュ*に格納されます。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] キャッシュは、現在のユーザーの \[Documents and Settings\] フォルダーの \[Local Settings\] ディレクトリの下の一連の隠しディレクトリです。  このキャッシュには、アプリケーションの全ファイル \(アセンブリ、構成ファイル、アプリケーションおよびユーザーの設定、データ ディレクトリ\) が格納されています。  このキャッシュは、アプリケーションのデータ ディレクトリを最新バージョンに移行する際にも使用されます。  データ移行の詳細については、「[ClickOnce アプリケーションにおけるローカル データおよびリモート データへのアクセス](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)」を参照してください。  
  
 アプリケーション ストレージの場所を 1 か所にすることで、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] はアプリケーションの物理インストールを管理するタスクをユーザーから引き受けます。  キャッシュによって、すべてのアプリケーションおよびその個々のバージョンのアセンブリとデータ ファイルを個別に維持することによってアプリケーションを隔離することもできます。  たとえば、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションをアップグレードする場合、そのバージョンおよびデータ リソースはキャッシュ内の個別のディレクトリに格納されます。  
  
## キャッシュ ストレージ クォータ  
 オンラインでホストされる [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] キャッシュのサイズを制約するクォータによって、占有できる領域の容量が制限されます。  キャッシュのサイズは、ユーザーのすべてのオンライン アプリケーションに適用されます。単一の部分信頼オンライン アプリケーションは、クォータの半分の容量まで占有できます。  インストールして使用するアプリケーションは、キャッシュ サイズによる制限を受けず、キャッシュ サイズの制限の影響を受けることもありません。  すべての [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションに対して、キャッシュには最新のバージョンおよびその前にインストールしたバージョンだけが保持されます。  
  
 オンライン [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーション用に、クライアント コンピューターに既定で割り当てられるストレージは 250 MB です。  この制限にデータ ファイルは含まれません。  システム管理者は、HKEY\_CURRENT\_USER\\Software\\Classes\\Software\\Microsoft\\Windows\\CurrentVersion\\Deployment\\OnlineAppQuotaInKB レジストリ キーの DWORD 値を変更することによって、特定のクライアント コンピューターのクォータを拡大または縮小できます。この値はキャッシュ サイズをキロバイト単位で表します。  たとえば、キャッシュ サイズを 50 MB に減らすには、この値を 51200 に変更します。  
  
## 参照  
 [ClickOnce アプリケーションにおけるローカル データおよびリモート データへのアクセス](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)