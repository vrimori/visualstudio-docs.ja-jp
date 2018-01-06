---
title: "方法: エンドユーザーがインストールを開始する場所を指定 |Microsoft ドキュメント"
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
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: a3a2770933f4a9f600b12a2d601deca855de3a94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>方法: エンド ユーザーがインストールを開始する場所を指定する
発行するときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションでは、ユーザーにアクセスする、アプリケーションをダウンロードしてインストール場所は必ずしもアプリケーションを最初に発行する場所です。 たとえば、組織によっては、開発者が、ステージング サーバーにアプリケーションを公開可能性があり、管理者は、アプリケーションを Web サーバーに移動し、します。  
  
 この場合、使用することができます、`Installation URL`プロパティをユーザーがアクセスするアプリケーションをダウンロードする Web サーバーを指定します。 これは、機能は、アプリケーション マニフェストが更新プログラムを検索する場所を認識できるように必要です。  
  
 `Installation URL`でプロパティを設定することができます、**発行**のページ、**プロジェクト デザイナー**です。  
  
 **注**、`Installation URL`を使用してプロパティを設定することも、 **PublishWizard**です。 詳細については、次を参照してください。[する方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)です。  
  
### <a name="to-specify-an-installation-url"></a>インストール URL を指定するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  クリックして、**発行**タブです。  
  
3.  インストールの URL フィールドに入力形式 http://www.microsoft.com/ApplicationName または形式を使用して UNC パスを使用して完全修飾 URL を使用して、インストール場所\\\Server\ApplicationName です。  
  
## <a name="see-also"></a>参照  
 [方法: Visual Studio がファイルをコピーする場所を指定する](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)