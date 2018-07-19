---
title: '方法: ClickOnce の発行設定のバージョン |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c991975a369387fea248816f4465670f1062a927
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080227"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>方法: ClickOnce の発行設定のバージョン
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version`プロパティが公開するアプリケーションは更新プログラムとして扱うかどうかを決定します。 各時点のバージョンがインクリメントされます、アプリケーションは、更新プログラムとして発行されます。  
  
 `Publish Version`でプロパティを設定することができます、**発行**のページ、**プロジェクト デザイナー**します。  
  
> [!NOTE]
>  自動的にインクリメントするプロジェクトのオプションがある、`Publish Version`プロパティごとにアプリケーションを発行する。 このオプションは既定で有効にします。 詳細については、次を参照してください。[方法: ClickOnce の発行バージョンを自動的にインクリメントする](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)します。  
  
### <a name="to-change-the-publish-version"></a>発行バージョンを変更するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  **発行バージョン**フィールドに、インクリメント、**メジャー**、**マイナー**、**ビルド**、または**リビジョン**バージョン数値。  
  
    > [!NOTE]
    >  バージョン番号がデクリメントしないでください。そうする予期しない更新プログラムの動作と原因でした。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce の更新方法を選択します。](../deployment/choosing-a-clickonce-update-strategy.md)   
 [方法: 発行のバージョンに自動的にインクリメント、ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [ClickOnce アプリケーションを発行します。](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションの発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)