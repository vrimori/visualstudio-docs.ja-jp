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
ときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]オンラインとオフラインの両方のアプリケーションがインストールされている、エントリを追加する、**開始**メニューおよび**プログラム追加と削除** ボックスの一覧です。 表示名では、既定では、アプリケーション アセンブリの名前と同じ、設定して表示名を変更することが**製品名**で、**発行オプション** ダイアログ ボックス。  
  
 **製品名**が表示されます publish.htm ページ; にインストールされているオフライン アプリケーション内のエントリの名前になります、**開始** メニューともなりますに表示される名前**を追加または削除プログラム**です。  
  
 **パブリッシャー名** は publish.htm ページの**製品名**の上に表示され、インストールされたオフライン アプリケーションの場合、**スタート**メニューの中で、アプリケーションのアイコンが含まれているフォルダーの名前として表示されます。  
  
 設定することができます、**製品名**と**パブリッシャー名**でプロパティ、**発行オプション** ダイアログ ボックスで、**発行**ページ**プロジェクト デザイナー**です。  
  
### <a name="to-specify-a-start-menu-name"></a>スタート メニューの名前を指定するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  クリックして、**発行**タブです。  
  
3.  クリックして、**オプション**を開く ボタン、**発行オプション** ダイアログ ボックス。  
  
4.  をクリックして**説明**です。  
  
5.  **発行オプション** ダイアログ ボックスで、**製品名**に表示する名前を入力します。  
  
6.  必要に応じて、**パブリッシャー名**にパブリッシャー名を入力します。  
  
## <a name="see-also"></a>参照  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)