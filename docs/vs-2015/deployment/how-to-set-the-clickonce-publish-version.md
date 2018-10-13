---
title: '方法: ClickOnce の発行設定のバージョン |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: b3965e9600fa3ef6a091ae8e32439e8e4f420668
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271714"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>方法: ClickOnce の発行バージョンを設定する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `Publish Version`プロパティが公開するアプリケーションは更新プログラムとして扱うかどうかを決定します。 各時点のバージョンがインクリメントされます、アプリケーションは、更新プログラムとして発行されます。  
  
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
 [方法: ClickOnce の発行バージョンを自動的にインクリメントする](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



