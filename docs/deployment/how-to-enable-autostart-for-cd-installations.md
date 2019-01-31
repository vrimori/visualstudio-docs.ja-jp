---
title: '方法: CD インストールの自動開始を有効にする |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e414a3d1bc512b15912eb73e3befb575d1437ca2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945737"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>方法: CD インストールの自動開始を有効にする
デプロイするときに、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] CD-ROM または DVD-ROM などのリムーバブル メディアを使用して、アプリケーションを有効にできます`AutoStart`ように、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]メディアが挿入されると、アプリケーションが自動的に起動します。  
  
 `AutoStart` 有効にすることができます、**発行**のページ、**プロジェクト デザイナー**します。  
  
### <a name="to-enable-autostart"></a>自動開始を有効にするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **[発行]** タブをクリックします。  
  
3.  **[オプション]** ボタンをクリックします。  
  
     **発行オプション** ダイアログ ボックスが表示されます。  
  
4.  クリックして**展開**します。  
  
5.  選択、**の CD のインストールは、CD が挿入されたときに自動的にセットアップを開始**チェック ボックスをオンします。  
  
     *Autorun.inf*アプリケーションを発行するときにファイルを発行場所にコピーされます。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)