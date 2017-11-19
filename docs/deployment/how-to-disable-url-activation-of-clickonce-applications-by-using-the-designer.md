---
title: "方法: デザイナーを使用して ClickOnce アプリケーションの URL アクティベーションを無効にする |Microsoft ドキュメント"
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
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: f694b7bf80d15fa3674d64bb7d062cdf0953c14b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>方法 : デザイナーを使用して ClickOnce アプリケーションの URL アクティベーションを無効にする
通常、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Web サーバーからインストールした後すぐにアプリケーションが自動的に開始します。 セキュリティ上の理由から、することができます、この動作を無効にしてからアプリケーションを起動するユーザーに通知する、**開始** メニューの代わりにします。 次の手順では、URL アクティベーションを無効にする方法を説明します。  
  
 この手法は、Web サーバーからユーザーのコンピューターにインストールされた [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションにのみ使用できます。 これは、オンライン専用アプリケーションで、その URL を使用してのみ開始することがあるため使用できません。 オンライン専用であり、インストールされているアプリケーションの違いの詳細については、次を参照してください。 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)です。  
  
 この手順では[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 使用してこのタスクを実行することもできます、[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]です。 詳細については、次を参照してください。[する方法: ClickOnce アプリケーションの URL アクティベーションを無効にする](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)です。  
  
## <a name="procedure"></a>プロシージャ  
  
#### <a name="to-disable-url-activation-for-your-application"></a>アプリケーションの URL アクティベーションを無効にするには  
  
1.  プロジェクト名を右クリックして**ソリューション エクスプ ローラー**、 をクリック**プロパティ**です。  
  
2.  **プロパティ** ページで、をクリックして、**発行**タブです。  
  
3.  **[オプション]**をクリックします。  
  
4.  をクリックして**マニフェスト**です。  
  
5.  チェック ボックスをオン**からアクティブ化して、URL を使用してアプリケーションをブロック**です。  
  
6.  アプリケーションを配置します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)