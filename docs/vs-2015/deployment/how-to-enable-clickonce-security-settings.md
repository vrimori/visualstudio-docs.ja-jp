---
title: '方法: ClickOnce のセキュリティ設定を有効にする |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 73f4e16dc0d088ca617b49ee1250f51c4ae769e2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226028"
---
# <a name="how-to-enable-clickonce-security-settings"></a>方法 : ClickOnce のセキュリティ設定を有効にする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



