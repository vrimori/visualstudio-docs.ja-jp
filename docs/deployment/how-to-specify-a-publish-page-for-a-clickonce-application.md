---
title: '方法: ClickOnce アプリケーションの発行 ページの指定 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6397944a39a0424211c57ddfe1ad045fce730ec3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911664"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>方法: ClickOnce アプリケーションの発行ページを指定する
発行するときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションでは、既定の Web ページ (publish.htm) が生成され、アプリケーションと共に発行します。 このページは、アプリケーション、アプリケーションまたはすべての前提条件のインストールへのリンクおよび説明するヘルプ トピックへのリンクの名前を含む[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]します。 **発行ページ**、プロジェクトのプロパティを使用するための Web ページの名前を指定する、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション。  
  
 [発行] ページを指定すると、公開すると、次回そのはファイルにコピー発行場所です。できません、もう一度発行する場合は上書きされます。 ページの外観をカスタマイズする場合は、変更内容を失うことがなく実行できます。 詳細については、「[方法 :ClickOnce の既定の Web ページのカスタマイズ](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)」を参照してください。  
  
 **発行ページ**プロパティを設定することができます、**発行オプション**からアクセスできるダイアログ ボックス、**発行**のウィンドウ、**プロジェクト デザイナー**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>ClickOnce アプリケーションのカスタム Web ページを指定するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  選択、**発行**ウィンドウ。  
  
3.  をクリックして、**オプション**ボタンをクリックする、**発行オプション** ダイアログ ボックス。  
  
4.  クリックして**展開**します。  
  
5.  **発行オプション** ダイアログ ボックスに、必ず、**発行後に web ページを開いている配置** チェック ボックスをオン (既定でその選択する必要があります)。  
  
6.  **配置 web ページ**ボックス、Web ページの名前を入力し、クリックして**OK**します。  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>[発行] ページが発行するたびを起動するを防ぐために  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  選択、**発行**ウィンドウ。  
  
3.  をクリックして、**オプション**ボタンをクリックする、**発行オプション** ダイアログ ボックス。  
  
4.  クリックして**展開**します。  
  
5.  **発行オプション** ダイアログ ボックスで、クリア、**発行後に web ページを開いている配置**チェック ボックスをオンします。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [方法: ClickOnce の既定の Web ページのカスタマイズ](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)