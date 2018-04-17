---
title: '方法: CD インストールの自動開始を有効にする |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 896d0f97df444ae24e81037e49d211084e5f577e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>方法 : CD インストールの自動開始を有効にする
展開するときに、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] CD-ROM または DVD-ROM などのリムーバブル メディアを使用してアプリケーションを有効にできます`AutoStart`できるように、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]メディアが挿入されると、アプリケーションが自動的に起動します。  
  
 `AutoStart` 有効にすることができます、**発行**のページ、**プロジェクト デザイナー**です。  
  
### <a name="to-enable-autostart"></a>自動開始を有効にするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  クリックして、**オプション**ボタンをクリックします。  
  
     **発行オプション** ダイアログ ボックスが表示されます。  
  
4.  をクリックして**展開**です。  
  
5.  選択、**の CD からインストール、自動的に開始セットアップ CD が挿入される**チェック ボックスをオンします。  
  
     Autorun.inf ファイルは、アプリケーションを発行するときに、発行場所にコピーされます。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)