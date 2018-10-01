---
title: '方法: ClickOnce のセキュリティ設定を有効にする |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 65cba913afdee2379e5f702dda460cea2a33598f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535612"
---
# <a name="how-to-enable-clickonce-security-settings"></a>方法 : ClickOnce のセキュリティ設定を有効にする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: ClickOnce のセキュリティ設定を有効にする](https://docs.microsoft.com/visualstudio/deployment/how-to-enable-clickonce-security-settings)します。  
  
アプリケーションを発行するためには、ClickOnce アプリケーションのコード アクセス セキュリティを有効にする必要があります。 これは自動的に発行ウィザードを使用してアプリケーションを発行するときです。  
  
 場合によっては、コード アクセス セキュリティを有効にするとパフォーマンスに影響するビルド時や、アプリケーションのデバッグこのような場合は、セキュリティ設定を一時的に無効にする可能性があります。  
  
 ClickOnce のセキュリティ設定を有効または無効にすることができます、**セキュリティ**のページ、**プロジェクト デザイナー**します。  
  
### <a name="to-enable-clickonce-security-settings"></a>ClickOnce のセキュリティ設定を有効にするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **[セキュリティ]** タブをクリックします。  
  
3.  **[ClickOnce セキュリティ設定を有効にする]** チェック ボックスをオンにします。  
  
     [セキュリティ] ページで、アプリケーションのセキュリティ設定をカスタマイズできます。  
  
    > [!NOTE]
    >  アプリケーションを発行するたびに、このチェック ボックスを自動的に選択、**発行**ウィザード。  
  
### <a name="to-disable-clickonce-security-settings"></a>ClickOnce のセキュリティ設定を無効にするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **[セキュリティ]** タブをクリックします。  
  
3.  クリア、 **ClickOnce セキュリティ設定を有効にする**チェック ボックスをオンします。  
  
     アプリケーションは完全な信頼のセキュリティ設定で実行します。すべての設定、**セキュリティ**ページは無視されます。  
  
    > [!NOTE]
    >  発行ウィザードで、アプリケーションを発行するたびに、このチェック ボックスがオンする;各発行に成功した後にもう一度オフにする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce アプリケーションのコード アクセス セキュリティ](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)



