---
title: "方法: ClickOnce のセキュリティ設定を有効にする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: "8"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 7fc7df79f798596901d74d089baf1b84f1dcd152
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-enable-clickonce-security-settings"></a>方法 : ClickOnce のセキュリティ設定を有効にする
アプリケーションを発行するのには、ClickOnce アプリケーション用のコード アクセス セキュリティを有効にする必要があります。 これは自動的に発行ウィザードを使用してアプリケーションを発行するときにします。  
  
 場合によっては、コード アクセス セキュリティを有効にするとパフォーマンスに影響するビルド時や、アプリケーションのデバッグこのような場合は、セキュリティ設定を一時的に無効にすることです。  
  
 ClickOnce のセキュリティ設定を有効または無効にすることができます、**セキュリティ**のページ、**プロジェクト デザイナー**です。  
  
### <a name="to-enable-clickonce-security-settings"></a>ClickOnce のセキュリティ設定を有効にするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  **[セキュリティ]** タブをクリックします。  
  
3.  **[ClickOnce セキュリティ設定を有効にする]** チェック ボックスをオンにします。  
  
     これで、[セキュリティ] ページで、アプリケーションのセキュリティ設定をカスタマイズできます。  
  
    > [!NOTE]
    >  このチェック ボックスでアプリケーションを発行するたびに自動的に選択は、**発行**ウィザード。  
  
### <a name="to-disable-clickonce-security-settings"></a>ClickOnce のセキュリティ設定を無効にするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  **[セキュリティ]** タブをクリックします。  
  
3.  クリア、 **ClickOnce セキュリティ設定を有効にする**チェック ボックスをオンします。  
  
     完全な信頼のセキュリティ設定で、アプリケーションが実行されます。すべての設定、**セキュリティ**ページは無視されます。  
  
    > [!NOTE]
    >  発行ウィザードを使用してアプリケーションを発行するたびにこのチェック ボックスがオンされます。各正常に発行した後、オフにする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce アプリケーションのコード アクセス セキュリティ](../deployment/code-access-security-for-clickonce-applications.md)   
 
