---
title: '方法: ClickOnce アプリケーションのスタート メニューの名前を指定 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
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
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 17
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: f01bb5750f31101a6d8ec0cb5f33669e5fbf2b4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>方法 : ClickOnce アプリケーションのスタート メニューの名前を指定する
オンラインまたはオフラインで利用できる [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションがインストールされると、**スタート**メニューおよび**プログラムの追加と削除** の一覧にエントリが追加されます。 既定では、表示される名前はアプリケーション アセンブリの名前と同じですが、**発行オプション** のダイアログ ボックスで**製品名**を設定することで表示名を変更することがきます。  
  
 **製品名** は publish.htm のページに表示されます；インストールされたオフライン アプリケーションの場合、この名前が **スタート** メニューに表示されるエントリの名前になり、**プログラムの追加または削除** にも同じ名前が表示されます。  
  
 **パブリッシャー名** は publish.htm ページの**製品名**の上に表示され、インストールされたオフライン アプリケーションの場合、**スタート**メニューの中で、アプリケーションのアイコンが含まれているフォルダーの名前として表示されます。  
  
 **製品名**と**パブリッシャー名**のプロパティは、**プロジェクト デザイナー**の**発行**ページにある**発行オプション** ダイアログ ボックスで設定することができます。  
  
### <a name="to-specify-a-start-menu-name"></a>スタート メニューの名前を指定するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  **オプション**ボタンをクリックして、**発行オプション** ダイアログ ボックスを開きます。  
  
4.  **説明**をクリックします。  
  
5.  **発行オプション** ダイアログ ボックスで、**製品名**に表示する名前を入力します。  
  
6.  必要に応じて、**パブリッシャー名**にパブリッシャー名を入力します。  
  
## <a name="see-also"></a>参照  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)