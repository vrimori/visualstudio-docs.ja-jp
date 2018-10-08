---
title: '方法: CD インストールの自動開始を有効にする |Microsoft Docs'
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
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 7a0f7228e4340763104f38dc56e5e8603ed85408
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535280"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>方法 : CD インストールの自動開始を有効にする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: CD インストールの自動開始を有効にする](https://docs.microsoft.com/visualstudio/deployment/how-to-enable-autostart-for-cd-installations)します。  
  
デプロイするときに、 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] CD-ROM または DVD-ROM などのリムーバブル メディアを使用して、アプリケーションを有効にできます`AutoStart`ように、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]メディアが挿入されると、アプリケーションが自動的に起動します。  
  
 `AutoStart` 有効にすることができます、**発行**のページ、**プロジェクト デザイナー**します。  
  
### <a name="to-enable-autostart"></a>自動開始を有効にするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  をクリックして、**オプション**ボタンをクリックします。  
  
     **発行オプション** ダイアログ ボックスが表示されます。  
  
4.  クリックして**展開**します。  
  
5.  選択、**の CD のインストールは、CD が挿入されたときに自動的にセットアップを開始**チェック ボックスをオンします。  
  
     Autorun.inf ファイルは、アプリケーションを発行するときに、発行場所にコピーされます。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



