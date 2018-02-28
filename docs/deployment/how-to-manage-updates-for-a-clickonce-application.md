---
title: "方法: ClickOnce アプリケーションの更新プログラムの管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: f239f13a7dcefe0ce6f2bf8c12c641e97a48ce26
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>方法 : ClickOnce アプリケーションの更新プログラムを管理する
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションは、プログラムによってまたは自動的に更新プログラムを確認できます。 開発者は、多数の更新チェックを実行する時期と方法、更新プログラムを必須かどうか、および更新プログラム、アプリケーションをどこで確認する必要がありますを指定することで柔軟性があります。  
  
 アプリケーションの起動後に自動的に開始する前に、アプリケーション、または、設定された間隔で更新プログラムをチェックするアプリケーションを構成することができます。 さらに、最低限の必要なバージョンを指定できます。つまり、ユーザーのバージョンが必要なバージョンより低い場合、更新プログラムがインストールされます。  
  
 ユーザーの要求などのイベントに基づいて、プログラムで更新プログラムを確認するアプリケーションを構成できます。 "プログラムで更新プログラムの確認"する手順をこのトピックの内容を使用するコードを記述する方法を示しています、<xref:System.Deployment.Application.ApplicationDeployment>イベントに基づいて、更新プログラムを確認するクラス。  
  
 また、1 つの場所からアプリケーションを展開し、別の更新できます。 別の更新の場所を指定します。"には」を参照してください。  
  
 詳細については、次を参照してください。 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)です。  
  
 更新動作を管理する、**アプリケーションの更新プログラム** ダイアログ ボックスから、**発行**のページ、**プロジェクト デザイナー。**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>アプリケーションを開始する前に更新プログラムを確認するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  クリックして、**発行**タブです。  
  
3.  をクリックして、**更新**を開く ボタン、**アプリケーションの更新プログラム** ダイアログ ボックス。  
  
4.  **アプリケーションの更新プログラム** ダイアログ ボックスで、ことを確認して、**アプリケーションの更新プログラムを確認する必要があります** チェック ボックスをオンします。  
  
5.  **アプリケーションの更新プログラムを確認する必要があります** セクションで、**アプリケーションを開始する前に**です。 これにより、常にネットワークに接続しているユーザーが最新の更新プログラム、アプリケーションを実行します。  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>アプリケーションの起動後に、バック グラウンドで更新をチェックするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  クリックして、**発行**タブです。  
  
3.  をクリックして、**更新**を開く ボタン、**アプリケーションの更新プログラム** ダイアログ ボックス。  
  
4.  **アプリケーションの更新プログラム** ダイアログ ボックスで、ことを確認して、チェック ボックス**アプリケーションの更新プログラムを確認する必要があります**が選択されています。  
  
5.  **選択更新] セクションのアプリケーションを確認する**[**アプリケーションの起動後**です。 アプリケーションがこのようにしてより迅速を起動し、バック グラウンドで更新プログラムを確認し、更新プログラムがある場合にのみユーザーに通知するには。 インストールされると、更新プログラムは反映されません、アプリケーションが再起動されるまでです。  
  
6.  **アプリケーションが更新プログラムを確認する頻度を指定する**セクションで、いずれかを選択**アプリケーションを実行するたびに確認**(既定) または**チェックすべて**数値と時間間隔を入力してください。  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>アプリケーションに最低限必要なバージョンを指定するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  クリックして、**発行**タブです。  
  
3.  をクリックして、**更新**を開く ボタン、**アプリケーションの更新プログラム** ダイアログ ボックス。  
  
4.  **アプリケーションの更新プログラム** ダイアログ ボックスで、ことを確認して、**アプリケーションの更新プログラムを確認する必要があります** チェック ボックスをオンします。  
  
5.  選択、**このアプリケーションに最低限必要なバージョンを指定**チェック ボックスをオンにし、入力**メジャー**、**マイナー**、**ビルド**、および**リビジョン**アプリケーションの番号。  
  
### <a name="to-specify-a-different-update-location"></a>別の更新の場所を指定  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  クリックして、**発行**タブです。  
  
3.  をクリックして、**更新**を開く ボタン、**アプリケーションの更新プログラム** ダイアログ ボックス。  
  
4.  **アプリケーションの更新プログラム** ダイアログ ボックスで、ことを確認して、**アプリケーションの更新プログラムを確認する必要があります** チェック ボックスをオンします。  
  
5.  **の場所を更新**フィールドに「書式 http://Hostname/ApplicationName または形式を使用して UNC パスを使用して、完全修飾 URL を使用して更新プログラムの場所\\\Server\ApplicationName、クリックして、または**参照**更新プログラムの場所を参照するボタンをクリックします。  
  
### <a name="to-check-for-updates-programmatically"></a>プログラムで更新プログラムを確認するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  クリックして、**発行**タブです。  
  
3.  をクリックして、**更新**を開く ボタン、**アプリケーションの更新プログラム** ダイアログ ボックス。  
  
4.  **アプリケーションの更新プログラム** ダイアログ ボックスで、ことを確認して、**アプリケーションの更新プログラムを確認する必要があります** チェック ボックスをオフします。 (必要に応じて、更新プログラムでと、更新プログラムを自動的にチェック ClickOnce ランタイムのチェックには、このチェック ボックスをオンことができます)。  
  
5.  **の場所を更新**フィールドに「書式 http://Hostname/ApplicationName または形式を使用して UNC パスを使用して、完全修飾 URL を使用して更新プログラムの場所\\\Server\ApplicationName、クリックして、または**参照**更新プログラムの場所を参照するボタンをクリックします。 更新プログラムの場所は、アプリケーション自体の更新バージョンを検索する場所です。  
  
6.  ユーザーが更新プログラムを確認するには、次のように選択する Windows フォーム上のボタン、メニュー項目、またはその他のユーザー インターフェイス項目を作成します。 その項目のイベント ハンドラーからメソッドを呼び出しての確認し、更新プログラムをインストールします。 このようなメソッド用の Visual Basic および Visual c# のコードの例があります[する方法: ClickOnce 配置 API をアプリケーションの更新プログラムを使用したプログラムの確認](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)です。  
  
7.  アプリケーションをビルドします。  
  
## <a name="see-also"></a>参照  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [アプリケーションの更新 ダイアログ ボックス](http://msdn.microsoft.com/en-us/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [方法 : ClickOnce 配置 API を使用してアプリケーションの更新プログラムをプログラムで確認する](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)