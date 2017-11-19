---
title: "方法: ClickOnce アプリケーションの発行ページを指定する |Microsoft ドキュメント"
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
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: "18"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: e05718d2a00df76d2c78e16c5b4473ab48d43a39
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>方法: ClickOnce アプリケーションの発行ページを指定する
発行するときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションで、既定の Web ページ (publish.htm) が生成され、アプリケーションと共に発行します。 このページは、アプリケーション、アプリケーションや、前提条件のインストールへのリンク、および説明するヘルプ トピックへのリンクの名前を含む[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]です。 **ページを公開**、プロジェクトのプロパティでは、Web ページの名前を指定することができます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。  
  
 [発行] ページを指定すると、次回発行するには場所にコピーする、発行;これは上書きされませんを再発行する場合。 ページの外観をカスタマイズする場合は、これを行う、変更内容を失うことがなくです。 詳細については、次を参照してください。[する方法: ClickOnce の既定の Web ページをカスタマイズ](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)です。  
  
 **ページを公開**プロパティを設定することができます、**発行オプション**ダイアログ ボックスからアクセスできる、**発行**のペイン、**プロジェクト デザイナー**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>ClickOnce アプリケーションのカスタム Web ページを指定するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  選択、**発行**ウィンドウです。  
  
3.  クリックして、**オプション**を開く ボタン、**発行オプション** ダイアログ ボックス。  
  
4.  をクリックして**展開**です。  
  
5.  **発行オプション** ダイアログ ボックスで、ことを確認して、**発行後に web ページを開いている配置** チェック ボックスをオン (既定では、選択する必要があります)。  
  
6.  **配置 web ページ:**ボックスで、Web ページの名前を入力し、をクリックして**OK**です。  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>[発行] ページを発行するたびを起動できないようにするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  選択、**発行**ウィンドウです。  
  
3.  クリックして、**オプション**を開く ボタン、**発行オプション** ダイアログ ボックス。  
  
4.  をクリックして**展開**です。  
  
5.  **発行オプション**ダイアログ ボックスで、クリア、**発行後に web ページを開いている配置**チェック ボックスをオンします。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションの発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [方法: ClickOnce の既定の Web ページをカスタマイズします。](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)