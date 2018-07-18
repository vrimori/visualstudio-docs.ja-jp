---
title: '方法: ClickOnce アプリケーションの既定の Web ページをカスタマイズする |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 743d7f259da4129eda578808d1ce04619104a3f1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31557672"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>方法 : ClickOnce アプリケーションの既定の Web ページをカスタマイズする
Web への ClickOnce アプリケーションを発行するときに、Web ページが自動的に生成され、アプリケーションと共に発行します。 既定のページには、アプリケーションと、アプリケーションのインストール、インストールの前提条件、または MSDN のヘルプにアクセスするリンクの名前が含まれています。  
  
> [!NOTE]
>  ページに表示される実際のリンクは、ページが表示されているコンピューターと新機能によって異なります。 前提条件が含まれています。  
  
 Web ページの既定の名前は Publish.htm です。内の名前を変更することができます、**プロジェクト デザイナー**です。 詳細については、次を参照してください。[する方法: ClickOnce アプリケーションの発行ページを指定](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)です。  
  
 Publish.htm Web ページを公開するは、新しいバージョンが検出された場合にのみです。  
  
> [!NOTE]
>  対して行った変更、**発行**設定は、Publish.htm ページで、1 つの例外: 追加の前提条件を最初に発行後に削除するか、前提条件の一覧が不要になった正確になります。 変更を反映するように前提条件のリンクのテキストを編集する必要があります。  
  
### <a name="to-customize-the-publish-web-page"></a>発行 Web ページをカスタマイズするには  
  
1.  Web 上の場所に、ClickOnce アプリケーションを発行します。 詳細については、次を参照してください。[する方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)です。  
  
2.  Web サーバー上には、ビジュアル Web デザイナーまたは他の HTML エディターで Publish.htm ファイルを開きます。  
  
3.  必要に応じて、ページをカスタマイズし、保存します。  
  
4.  任意。 Visual Studio のカスタマイズした発行 Web ページの上書きを防ぐためにオフにして**後に配置された web ページを自動的に生成すべて発行**発行オプション ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: ClickOnce アプリケーションと共に必須コンポーネントをインストールする](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [方法: ClickOnce アプリケーションの発行ページを指定する](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)