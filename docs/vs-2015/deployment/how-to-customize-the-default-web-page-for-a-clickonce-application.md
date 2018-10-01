---
title: '方法: ClickOnce アプリケーションの既定の Web ページをカスタマイズする |Microsoft Docs'
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
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: bae699d0425f622f81ca14427934271b8d45eefb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538351"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>方法 : ClickOnce アプリケーションの既定の Web ページをカスタマイズする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: ClickOnce アプリケーションの既定の Web ページをカスタマイズ](https://docs.microsoft.com/visualstudio/deployment/how-to-customize-the-default-web-page-for-a-clickonce-application)します。  
  
ClickOnce アプリケーションの Web を発行するときに、Web ページが自動的に生成され、アプリケーションと共に発行します。 既定のページには、アプリケーションとアプリケーションのインストール、インストールの前提条件、または MSDN のヘルプにアクセスするリンクの名前が含まれています。  
  
> [!NOTE]
>  ページに表示される実際のリンクは、ページが表示されているコンピューターとによって異なります。 前提条件が含まれています。  
  
 Web ページの既定の名前は Publish.htm;内の名前を変更することができます、**プロジェクト デザイナー**します。 詳細については、次を参照してください。[方法: ClickOnce アプリケーションの発行ページを指定](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)します。  
  
 新しいバージョンが検出された場合にのみ、Publish.htm Web ページが発行されます。  
  
> [!NOTE]
>  対して行った変更、**発行**設定は Publish.htm ページで、1 つの例外は影響しません。 追加の前提条件を最初に発行した後に削除するか、前提条件の一覧が正確なにされなくなります。 変更を反映する前提条件となるリンクのテキストを編集する必要があります。  
  
### <a name="to-customize-the-publish-web-page"></a>発行 Web ページをカスタマイズするには  
  
1.  Web 上の場所に、ClickOnce アプリケーションを発行します。 詳細については、次を参照してください。[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)します。  
  
2.  Web サーバーでは、Visual Web Designer または別の HTML エディターで Publish.htm ファイルを開きます。  
  
3.  必要に応じて、ページをカスタマイズし、保存します。  
  
4.  任意。 Visual Studio の発行のカスタマイズされた Web ページの上書きを防ぐためにオフにします。**後に配置 web ページを自動的に生成すべて発行**発行オプション ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: ClickOnce アプリケーションと共に必須コンポーネントをインストールする](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [方法: ClickOnce アプリケーションの発行ページを指定する](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)



