---
title: '方法: 指定の ClickOnce のオフラインまたはオンライン モードのインストール |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef19b966bb9d934975eebd00399b401e768922d1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011677"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>方法: ClickOnce のオフラインまたはオンラインのインストール モードを指定する
`Install Mode`の[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションがオフラインまたはオンライン、アプリケーションが利用できるかどうかを判断します。 選択すると**アプリケーションはオンラインでのみ使用可能な**に、ユーザーがアクセスする必要があります、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]発行場所 (Web ページまたはファイル共有のいずれか)、アプリケーションを実行するためにします。 選択すると**アプリケーションはオフラインでも利用可能な**、アプリケーションへのエントリを追加します、**開始**メニューと**プログラム追加と削除** ダイアログ ボックスは、ユーザーは、接続されていないときに、アプリケーションを実行することができます。  
  
 `Install Mode`に設定することができます、**発行**のページ、**プロジェクト デザイナー**します。  
  
 **注**、`Install Mode`発行ウィザードを使用して設定できます。 詳細については、「[方法 :発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)」を参照してください。  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>ClickOnce アプリケーションを使用できるようにするオンラインのみ  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **[発行]** タブをクリックします。  
  
3.  **モードのインストールと設定**領域で、をクリックして、**アプリケーションはオンラインでのみ使用可能な**オプション ボタンをクリックします。  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>オンラインまたはオフラインのために、ClickOnce アプリケーションを使用できるようにするには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **[発行]** タブをクリックします。  
  
3.  **モードのインストールと設定**領域で、をクリックして、**アプリケーションはオフラインでも利用可能な**オプション ボタンをクリックします。  
  
     アプリケーションにエントリを追加インストールすると、**開始**メニューと**プログラム追加と削除**コントロール パネルの します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)