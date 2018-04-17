---
title: ClickOnce キャッシュの概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 847e6cc7e84dcda2efdbaac630ce8589ff959180
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="clickonce-cache-overview"></a>ClickOnce キャッシュの概要
すべて[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]、アプリケーションは、ローカルにインストールされたり、オンラインでホストされているかどうか、内のクライアント コンピューターに保存されて、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション*キャッシュ*です。 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]キャッシュは、現在のユーザーの Documents and Settings フォルダーのローカル設定ディレクトリの下の非表示のディレクトリのファミリです。 このキャッシュは、アセンブリ、構成ファイル、アプリケーションとユーザー設定、およびデータ ディレクトリを含む、アプリケーションのすべてのファイルを保持します。 アプリケーションのデータ ディレクトリを最新バージョンに移行するため、キャッシュもします。 データ移行の詳細については、次を参照してください。[ローカルへのアクセスと ClickOnce アプリケーションでのリモート データ](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)です。  
  
 アプリケーションの記憶域は、1 つの場所を提供することによって[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ユーザーから、アプリケーションの物理的なインストールを管理するための作業を引き継ぎます。 キャッシュでは、アセンブリとすべてのアプリケーションのデータ ファイルを保持することでアプリケーションを切り分けることができ、その個々 のバージョンが互いから分離します。 たとえば、アップグレード、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション、バージョンとそのデータ リソースがキャッシュ内の独自のディレクトリで提供されていること。  
  
## <a name="cache-storage-quota"></a>キャッシュの記憶域のクォータ  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] オンラインでホストされているアプリケーションは、占有できる領域の量のサイズを制限するクォータで制限された、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]キャッシュします。 すべてのユーザーのオンライン アプリケーションにキャッシュ サイズが適用されます。1 つの部分的に信頼された、オンライン アプリケーションは、クォータのスペースの半分を占有に制限されます。 インストールされているアプリケーションは、キャッシュのサイズによる制限はありませんし、キャッシュ制限としてはカウントされません。 すべての[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション、キャッシュは、現在のバージョンのみと、以前にインストールされたバージョンが保持されます。  
  
 既定では、クライアント コンピューターがある 250 MB の記憶域のオンライン[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。 データ ファイルは、この制限はカウントされません。 システム管理者を拡大または HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB、値は、DWORD レジストリ キーを変更することによって、特定のクライアント コンピューターにこのクォータを削減できます。キャッシュ サイズ (キロバイト単位) を表現するとします。 たとえば、50 mb のキャッシュ サイズを減らす、この値を 51200 を変更します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションにおけるローカル データおよびリモート データへのアクセス](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)