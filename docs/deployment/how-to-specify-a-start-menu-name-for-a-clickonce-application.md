---
title: '方法: ClickOnce アプリケーションのスタート メニューの名前を指定します |。Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7cf4f2b30079a76012acfe972ea0de0b9e0ea78
ms.sourcegitcommit: 34840a954ed3446c789e80ee87da6cbf1203cbb5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2018
ms.locfileid: "53592834"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>方法: ClickOnce アプリケーションのスタート メニューの名前を指定する
ときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]オンラインとオフラインの両方のアプリケーションがインストールされている、エントリを追加する、**開始**メニューおよび**プログラム追加と削除**一覧。 表示名では、既定では、アプリケーション アセンブリの名前と同じ、表示名を設定して変更することができますが、**製品名**で、**発行オプション** ダイアログ ボックス。  

 **製品名**に表示される、 *publish.htm*ページは、インストールされているオフライン アプリケーション内のエントリの名前をことが、**開始** メニューともなりますに表示される名前**を追加または削除プログラム**します。  

 **発行元名**に表示されます、 *publish.htm*ページ上部**製品名**、オフライン アプリケーションのインストールされている場合も可能になりますを含む、アプリケーションのフォルダーの名前とアイコン、**開始**メニュー。  

 スタート メニュー ショートカットまたはアプリ参照が作成される *%appdata%\Microsoft\Windows\Start menu \programs\\< 発行者名\>* します。 ショートカットまたはアプリの参照は、製品名と同じ名前を持ちます。
  
 設定することができます、**製品名**と**パブリッシャー名**プロパティで、**発行オプション**] ダイアログ ボックス、[、**発行**ページ**プロジェクト デザイナー**します。  

### <a name="to-specify-a-start-menu-name"></a>スタート メニューの名前を指定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **[発行]** タブをクリックします。  
  
3.  をクリックして、**オプション**ボタンをクリックする、**発行オプション** ダイアログ ボックス。  
  
4.  クリックして**説明**します。  
  
5.  **発行オプション** ダイアログ ボックスに表示する名前を入力**製品名**します。  
  
6.  パブリッシャー名を入力する必要に応じて、**パブリッシャー名**します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
