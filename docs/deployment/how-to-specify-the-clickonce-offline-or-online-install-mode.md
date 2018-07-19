---
title: '方法: ClickOnce のオフラインを指定するか、オンライン モードのインストール |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1515d9b9b12d92f7189c1dda59659d6ea1c03d5
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080174"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>方法: ClickOnce のオフラインを指定するか、オンライン モードのインストール
`Install Mode`の[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションがオフラインまたはオンライン、アプリケーションが利用できるかどうかを判断します。 選択すると**アプリケーションはオンラインでのみ使用可能な**に、ユーザーがアクセスする必要があります、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]発行場所 (Web ページまたはファイル共有のいずれか)、アプリケーションを実行するためにします。 選択すると**アプリケーションはオフラインでも利用可能な**、アプリケーションへのエントリを追加します、**開始**メニューと**プログラム追加と削除** ダイアログ ボックスは、ユーザーは、接続されていないときに、アプリケーションを実行することができます。  
  
 `Install Mode`に設定することができます、**発行**のページ、**プロジェクト デザイナー**します。  
  
 **注**、`Install Mode`発行ウィザードを使用して設定できます。 詳細については、次を参照してください。[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)します。  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>ClickOnce アプリケーションを使用できるようにするオンラインのみ  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  **モードのインストールと設定**領域で、をクリックして、**アプリケーションはオンラインでのみ使用可能な**オプション ボタンをクリックします。  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>オンラインまたはオフラインのために、ClickOnce アプリケーションを使用できるようにするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  **モードのインストールと設定**領域で、をクリックして、**アプリケーションはオフラインでも利用可能な**オプション ボタンをクリックします。  
  
     アプリケーションにエントリを追加インストールすると、**開始**メニューと**プログラム追加と削除**コントロール パネルの します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションを発行します。](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションの発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [ClickOnce 配置ストラテジを選択します。](../deployment/choosing-a-clickonce-deployment-strategy.md)