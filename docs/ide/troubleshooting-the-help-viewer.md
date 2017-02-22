---
title: "ヘルプ ビューアーのトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ヘルプ ビューアー 2.0, トラブルシューティング"
  - "トラブルシューティング [ヘルプ ビューアー 2.0]"
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ヘルプ ビューアーのトラブルシューティング
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このトピックでは、ヘルプ ビューアーで発生する可能性のある問題について説明します。  
  
## オーディオが機能しない。  
 ヘルプ ビューアーにはオーディオ プレーヤーが含まれていません。  オーディオが含まれるコンテンツをダウンロードした場合に、**\[再生\]** をクリックしてもコンテンツは再生されません。オーディオ プレーヤーをインストールしてください。  
  
## 検索は、Windows Server 2008、Windows Server 2008 SP1、または Windows Server 2008 R2 では機能しません。  
 ヘルプ ビューアーの検索機能とフィルター機能を使用するには、Windows Search サービスがインストールされ、オンになっている必要があります。  このサービスは Windows Server 2008、Windows Server 2008 Service Pack 1 \(SP1\)、および Windows Server 2008 R2 では既定でオフになっています。  
  
#### Windows Search サービスをアクティブにするには  
  
1.  サーバー マネージャーを起動します。  
  
2.  左側のナビゲーション ペインで、**\[役割\]** を選択します。  
  
3.  \[役割の概要\] ペインで、**\[役割の追加\]** を選択します。  
  
4.  ファイル サービスの役割を選択し、**\[次へ\]** をクリックします。  
  
5.  Windows Search の役割サービスを選択します。  
  
## その他のリソース  
 次のリソースを使用して、ヘルプ ビューアーで詳細情報を取得し、フィードバックを提供することができます。  
  
-   フィードバックを提供するには、Microsoft の Web サイト、[Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) をご覧になるか、[hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com) まで電子メールを送信してください。  
  
-   詳細については、[Developer Documentation and Help System \(デベロッパー ドキュメントおよびヘルプ システム\)](http://go.microsoft.com/fwlink/?LinkId=232741) フォーラムおよび [The Help Guy \(ヘルプ ガイ\)](http://go.microsoft.com/fwlink/?LinkId=232743) ブログを参照してください。  
  
## 参照  
 [ヘルプ ビューアー 2.1 の管理者ガイド](http://go.microsoft.com/fwlink/?LinkId=243985)