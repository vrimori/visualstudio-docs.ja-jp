---
title: "方法: ClickOnce のオフラインを指定するか、オンライン モードのインストール |Microsoft ドキュメント"
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
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: "8"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 5376ef32ce768100af8bc1c9f18267f7ac39895a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>方法: ClickOnce のオフラインまたはオンラインのインストール モードを指定する
`Install Mode`の[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションでは、オフラインまたはオンライン、アプリケーションが使用できるかどうかを決定します。 選択すると**アプリケーションはオンラインでのみ使用可能な**へのアクセスが必要、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]発行場所 (Web ページまたはファイル共有のいずれか)、アプリケーションを実行するためにします。 選択すると**アプリケーションはオフラインでも利用可能な**、アプリケーションを追加するエントリ、**開始**メニューおよび**プログラム追加と削除** ダイアログ ボックスですユーザーは。接続されていないときに、アプリケーションを実行できません。  
  
 `Install Mode`に対して設定できる、**発行**のページ、**プロジェクト デザイナー**です。  
  
 **注**、`Install Mode`発行ウィザードを使用して設定することもできます。 詳細については、次を参照してください。[する方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)です。  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>ClickOnce アプリケーションを使用可能にオンラインのみ  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  クリックして、**発行**タブです。  
  
3.  **モードのインストールと設定**領域で、をクリックして、**アプリケーションはオンラインでのみ使用可能な**オプション ボタンをクリックします。  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>ClickOnce アプリケーションをオンラインでもオフラインでも使用できるようにするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  クリックして、**発行**タブです。  
  
3.  **モードのインストールと設定**領域で、をクリックして、**アプリケーションはオフラインでも利用可能な**オプション ボタンをクリックします。  
  
     アプリケーションにエントリを追加インストールすると、**開始**メニューおよび**プログラム追加と削除**コントロール パネルの します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションの発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)