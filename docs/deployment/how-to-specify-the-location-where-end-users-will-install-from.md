---
title: '方法: エンドユーザーがからインストールする場所を指定 |Microsoft Docs'
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
ms.openlocfilehash: 6b0731a5e218b6fcd6a13ac00fe19daad86f6b3d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078086"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>方法: エンドユーザーがからインストールする場所を指定
発行するときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションをダウンロードしてインストール、アプリケーションにアクセスするユーザーの場所は必ずしも、アプリケーションを最初に発行する場所。 たとえば、一部の組織で、開発者は、ステージング サーバーにアプリケーションを公開可能性があり、管理者は、アプリケーションを Web サーバーを移動し。  
  
 この場合、使用することができます、`Installation URL`プロパティをユーザーは、アプリケーションのダウンロードにアクセスする Web サーバーを指定します。 これは、機能は、アプリケーション マニフェストが更新プログラムを検索する場所を認識できるように必要です。  
  
 `Installation URL`でプロパティを設定することができます、**発行**のページ、**プロジェクト デザイナー**します。  
  
 **注**、`Installation URL`を使用してプロパティを設定することも、**発行ウィザード**します。 詳細については、次を参照してください。[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)します。  
  
### <a name="to-specify-an-installation-url"></a>インストール URL を指定するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  インストール URL フィールドに、形式を使用して完全修飾 URL を使用して、インストール場所を入力します*http://www.microsoft.com/ApplicationName*、または UNC パス形式を使用して *\\\Server\ApplicationName*.  
  
## <a name="see-also"></a>関連項目  
 [方法: Visual Studio がファイルをコピーする場所を指定します。](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションの発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)