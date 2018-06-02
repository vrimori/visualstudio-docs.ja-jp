---
title: Office ソリューションのセキュリティのトラブルシューティング |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 547ba6d1e58376c50d0e01ab8fd3d55f62d5a935
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693319"
---
# <a name="troubleshooting-office-solution-security"></a>Office ソリューションのセキュリティのトラブルシューティング
  このトピックには、Office ソリューションのセキュリティ保護を使用する場合に発生する可能性がある一般的な問題を解決するためのヒントが含まれています。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>信頼された制限付きサイトからソリューションをインストールすることはできません。  
 ユーザーは、web サイトが Internet Explorer の制限付きサイト ゾーンに表示されている場合、web 上の場所から、ソリューションをインストールできません。 これは、ソリューションが信頼された証明書で署名されている場合でも当てはまります。  
  
 配置マニフェストの URL は、5 つのゾーンのいずれかに分類できます。  
  
-   マイ コンピューター  
  
-   インターネット  
  
-   ローカル イントラネット  
  
-   信頼済みサイト  
  
-   制限付きサイト  
  
 配置マニフェストの場所を制限付きサイト ゾーンに割り当てられている場合[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]ソリューションではインストールされません。 場合、場所がわかっていることができます、信頼されたユーザー場所を制限付きサイト ゾーンから削除でき、ソリューションをインストールできます。 ゾーンを管理する方法については、次を参照してください。 [ClickOnce 信頼された発行元の構成](http://go.microsoft.com/fwlink/?LinkId=94774)です。  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Internet Explorer セキュリティ強化の構成または Internet Explorer 7 がインストールされているときに、ネットワーク ファイル共有または Web の場所からソリューションをインストールすることはできません。  
 Internet Explorer 強化されたセキュリティ構成 (IEESC) Windows Server 2003 以降では、および Internet Explorer 7 以降が大幅にはインターネットを閲覧するユーザーの機能を制限します。 ユーザーがネットワーク ファイル共有または web 上の場所から Office ソリューションをインストールしようとすると、次のエラー メッセージを取得した可能性があります:"の配置マニフェストに署名する証明書が使用されるため、このアプリケーションのカスタマイズされた機能は動作しません*SolutionName*は信頼されていません。 管理者に問い合わせてさらに支援します。"  
  
 IEESC と Internet Explorer 7 以降では、配置マニフェストの URL は、インターネット ゾーンの分類は、マニフェストが信頼された発行元からの証明書を持つ必要がありますかソリューションをインストールすることはできません。 Ieesc については、既定の動作は、信頼の決定にエンド ユーザー入力を求めるはします。  
  
 IEESC と Internet Explorer 7 の効果を管理し、以降では、web サイトおよび汎用名前付けの規則 (UNC) パスを信頼して信頼されたセキュリティ ゾーン (イントラネットまたは信頼済みサイト) のいずれかに追加します。ゾーンを管理する方法については、次を参照してください。 [ClickOnce 信頼された発行元の構成](http://go.microsoft.com/fwlink/?LinkId=94774)です。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)  
  
  