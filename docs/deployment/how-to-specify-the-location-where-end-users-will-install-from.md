---
title: '方法: エンドユーザーがインストールを開始する場所を指定 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0152cf6b03f2e089ee8633ef4abae9043e41bc24
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>方法: エンド ユーザーがインストールを開始する場所を指定する
発行するときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションでは、ユーザーにアクセスする、アプリケーションをダウンロードしてインストール場所は必ずしもアプリケーションを最初に発行する場所です。 たとえば、組織によっては、開発者が、ステージング サーバーにアプリケーションを公開可能性があり、管理者は、アプリケーションを Web サーバーに移動し、します。  
  
 この場合、使用することができます、`Installation URL`プロパティをユーザーがアクセスするアプリケーションをダウンロードする Web サーバーを指定します。 これは、機能は、アプリケーション マニフェストが更新プログラムを検索する場所を認識できるように必要です。  
  
 `Installation URL`でプロパティを設定することができます、**発行**のページ、**プロジェクト デザイナー**です。  
  
 **注**、`Installation URL`を使用してプロパティを設定することも、 **PublishWizard**です。 詳細については、次を参照してください。[する方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)です。  
  
### <a name="to-specify-an-installation-url"></a>インストール URL を指定するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  インストールの URL フィールドに、形式を使用して完全修飾 URL を使用して、インストール場所を入力してください。 http://www.microsoft.com/ApplicationName、または UNC パスを、形式を使用して\\\Server\ApplicationName です。  
  
## <a name="see-also"></a>関連項目  
 [方法: Visual Studio がファイルをコピーする場所を指定する](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)