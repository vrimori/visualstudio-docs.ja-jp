---
title: "Office ソリューションのセキュリティのトラブルシューティング"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "セキュリティ [Visual Studio での Office 開発], トラブルシューティング"
ms.assetid: 6f85dd61-31f5-47da-8409-21ad827eb2dd
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Office ソリューションのセキュリティのトラブルシューティング
  ここでは、Office ソリューションをセキュリティで保護するときに発生する可能性がある一般的な問題を解決するためのヒントを示します。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 信頼されたソリューションを制限付きサイトからインストールできない  
 Userは、WebサイトをInternet Explorerの制限付きサイト ゾーンに示すネットワークの場所からソリューションをインストールできません。  これは、ソリューションが信頼されている証明書で署名されている場合にも該当します。  
  
 配置マニフェストの URL は、次の 5 つのゾーンのうちのいずれかに分類できます。  
  
-   マイ コンピューター  
  
-   インターネット  
  
-   ローカル イントラネット  
  
-   信頼済みサイト  
  
-   制限付きサイト  
  
 配置マニフェストの場所が制限付きサイト ゾーンに割り当てられていると、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ではソリューションのインストールは行われません。  その場所が既知のものであり、信頼できる場合は、その場所を制限付きサイト ゾーンから削除してソリューションをインストールできます。  ゾーンを管理する方法の詳細については、「[Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774)」を参照してください。  
  
## Internet Explorer セキュリティ強化の構成または Internet Explorer 7 がインストールされているとネットワーク ファイル共有または Web の場所からソリューションをインストールできない  
 Windows Server 2003、Internet Explorerセキュリティ強化の構成\(IEESC\)以上、およびInternet Explorer 7と非常に高く、userの機能をインターネットを参照する制限します。  userがネットワーク ファイル共有またはWeb上の場所からOfficeソリューションをインストールしようとすると、次のエラー メッセージが表示されることがあります。: 「このアプリケーションのカスタマイズされた機能は *\[ソリューション名\]* の配置マニフェストに署名に使用する証明書が信頼されていないため、動作しません。  管理者にお問い合わせください。" というエラー メッセージが表示されることがあります。  
  
 IEESCおよびInternet Explorer 7でマニフェストと配置マニフェストのURLがインターネット ゾーンに並べ替える場合よりも、マニフェストが信頼された発行元の証明書がないと、ソリューションはインストールできません。  IEESC を使用していない場合の既定の動作では、信頼するかどうかの確認がエンド ユーザーに求められます。  
  
 IEESCおよびInternet Explorer 7の影響を管理するには、より高い、信頼されるセキュリティ ゾーンの1にを信用追加し、名前付け規則の\(UNC\)の汎用パスとWebサイトを識別します \(ローカル イントラネットまたはサイトを信頼します\)。ゾーンを管理する方法の詳細については、" "を参照してください。[構成のClickOnce信頼された発行元](http://go.microsoft.com/fwlink/?LinkId=94774)  
  
## 参照  
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)  
  
  