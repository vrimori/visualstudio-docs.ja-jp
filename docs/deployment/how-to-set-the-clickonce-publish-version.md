---
title: "方法: ClickOnce の発行設定バージョン |Microsoft ドキュメント"
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
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: db6bfae35bbbd14190028fb0e32dfc8d35cb9bac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-clickonce-publish-version"></a>方法: ClickOnce の発行バージョンを設定する
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version`プロパティを公開するアプリケーションが更新プログラムとして扱われますかどうかを決定します。 各時間バージョンがインクリメントされる、アプリケーションは、更新プログラムとして発行されます。  
  
 `Publish Version`でプロパティを設定することができます、**発行**のページ、**プロジェクト デザイナー**です。  
  
> [!NOTE]
>  プロジェクトのオプションを自動的にインクリメントされる、`Publish Version`プロパティごとにアプリケーションを発行する以外の場合は既定では、このオプションが有効にします。 詳細については、次を参照してください。[する方法: ClickOnce の発行バージョンを自動的にインクリメント](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)です。  
  
### <a name="to-change-the-publish-version"></a>発行バージョンを変更するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  クリックして、**発行**タブです。  
  
3.  **発行するバージョン**フィールドに、インクリメント、**メジャー**、**マイナー**、**ビルド**、または**リビジョン**バージョン数値。  
  
    > [!NOTE]
    >  バージョン番号がデクリメントしないでください。そうする予期しない更新プログラムの動作と原因でした。  
  
## <a name="see-also"></a>参照  
 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)   
 [方法: ClickOnce の発行バージョンを自動的にインクリメントする](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)