---
title: Office ソリューションのセキュリティをトラブルシューティングします。
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
ms.openlocfilehash: 002759a1a5fd8a16ee3e7842df7439d6e6b9755f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862932"
---
# <a name="troubleshoot-office-solution-security"></a>Office ソリューションのセキュリティをトラブルシューティングします。
  このトピックでには、Office ソリューションのセキュリティを使用する場合に発生する可能性がある一般的な問題を解決するためのヒントが含まれています。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>信頼できるソリューションは、制限付きサイトからインストールすることはできません。  
 ユーザーは、web サイトが Internet Explorer の制限付きサイト ゾーンで表示されている場合、web からソリューションをインストールできません。 これは、ソリューションが信頼された証明書で署名された場合でも当てはまります。  
  
 配置マニフェストの URL は、5 つのゾーンのいずれかに分類できます。  
  
- マイ コンピューター  
  
- インターネット  
  
- ローカル イントラネット  
  
- 信頼済みサイト  
  
- 制限付きサイト  
  
  配置マニフェストの場所は、制限付きサイト ゾーンに割り当てられている場合[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]ソリューションではインストールされません。 場所を選択して言いますできる場合、信頼されたユーザーの場所を制限付きサイト ゾーンから削除してインストールできますソリューション。 ゾーンを管理する方法については、次を参照してください。 [ClickOnce 信頼された発行元の構成](http://go.microsoft.com/fwlink/?LinkId=94774)します。  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Internet Explorer セキュリティ強化の構成または Internet Explorer 7 がインストールされている場合、ネットワーク ファイル共有または web の場所からソリューションをインストールすることはできません。  
 Internet Explorer 拡張セキュリティ構成 (IEESC) Windows Server 2003 以降では、および Internet Explorer 7 以降、インターネットを閲覧するユーザーの機能を大幅に制限します。 ユーザーがネットワーク ファイル共有または web の場所から Office ソリューションをインストールしようとすると、次のエラー メッセージが訪れた可能性があります:"の配置マニフェストに署名する証明書が使用されるため、このアプリケーションのカスタマイズされた機能は機能しません*SolutionName*は信頼されていません。 管理者に問い合わせてください。"  
  
 場合は、配置マニフェストの URL はインターネット ゾーンに分類されています IEESC と Internet Explorer 7 以降、マニフェストが信頼された発行元からの証明書を必要またはソリューションをインストールすることはできません。 Ieesc については、既定の動作は、信頼の決定にエンド ユーザー入力を求めるは。  
  
 以降では、特定の web サイトや汎用規則 (UNC) パスを名前付けの IEESC と Internet Explorer 7 の効果を管理するのには、信頼し、のいずれか (イントラネットまたは信頼済みサイト) の信頼できるセキュリティ ゾーンに追加します。ゾーンを管理する方法については、次を参照してください。[構成 ClickOnce 信頼された発行者](http://go.microsoft.com/fwlink/?LinkId=94774)します。  
  
## <a name="see-also"></a>関連項目  
 [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)  
  
  