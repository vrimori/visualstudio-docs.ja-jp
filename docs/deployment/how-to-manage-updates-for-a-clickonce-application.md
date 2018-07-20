---
title: '方法: ClickOnce アプリケーションの更新プログラムの管理 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 30a02c4b438d6e7504056ce5cdcc06bfc129d218
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151589"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>方法: ClickOnce アプリケーションの更新プログラムの管理
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、プログラムによってまたは自動的に更新プログラムを確認できます。 開発者は、多くの更新チェックを実行するタイミングと方法、更新プログラムが必須かどうか、および更新プログラム、アプリケーションがどこで確認する必要がありますを指定するときに柔軟性があります。  
  
 アプリケーションの起動後に自動的に開始する前に、アプリケーション、または一定間隔で更新プログラムをチェックするアプリケーションを構成することができます。 さらに、最低限の必要なバージョンを指定できます。つまり、ユーザーのバージョンが必要なバージョンより低い場合、更新プログラムがインストールします。  
  
 ユーザーの要求などのイベントに基づいて、プログラムで更新プログラムを確認するアプリケーションを構成することができます。 プログラムで更新プログラムの確認"するには」の手順では、このトピックで使用するコードを記述する方法を示しています、<xref:System.Deployment.Application.ApplicationDeployment>イベントに基づいて更新をチェックするクラス。  
  
 1 つの場所からアプリケーションの展開を別の更新することができますも。 さまざまな更新プログラムの場所を指定します"するには」を参照してください。  
  
 詳細については、次を参照してください。 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)します。  
  
 管理する更新プログラムの動作、**アプリケーションの更新プログラム** ダイアログ ボックスから使用可能な**発行**のページ、**プロジェクト デザイナー。**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>アプリケーションを開始する前に更新プログラムを確認するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  をクリックして、**更新**ボタンをクリックする、**アプリケーションの更新プログラム** ダイアログ ボックス。  
  
4.  **アプリケーションの更新プログラム** ダイアログ ボックスで、ことを確認します、**アプリケーションの更新プログラムを確認する必要があります** チェック ボックスをオンします。  
  
5.  **アプリケーションの更新プログラムを確認する必要があります **セクションで、**アプリケーションを開始する前に**します。 これにより、常にネットワークに接続しているユーザーが最新の更新プログラムとアプリケーションを実行します。  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>アプリケーションの起動後に、バック グラウンドで更新をチェックするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  をクリックして、**更新**ボタンをクリックする、**アプリケーションの更新プログラム** ダイアログ ボックス。  
  
4.  **アプリケーションの更新プログラム** ダイアログ ボックスで、ことを確認します チェック ボックス**アプリケーションの更新プログラムを確認する必要があります**が選択されています。  
  
5.  **選択更新 セクションのアプリケーションを確認する必要があります**、**アプリケーションの起動後**します。 アプリケーションがこのようにしてより迅速に開始され、バック グラウンドで更新プログラムを確認し、更新プログラムが利用可能な場合にのみユーザーに通知することができます。 インストールされると、更新プログラムは反映されません、アプリケーションが再起動されるまでです。  
  
6.  **アプリケーションの更新プログラムを確認する頻度を指定**セクションで、いずれかを選択**アプリケーションを実行するたびに確認**(既定値) または**チェックすべて**数値と時間間隔を入力します。  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>アプリケーションの必要な最小のバージョンを指定するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  をクリックして、**更新**ボタンをクリックする、**アプリケーションの更新プログラム** ダイアログ ボックス。  
  
4.  **アプリケーションの更新プログラム** ダイアログ ボックスで、ことを確認します、**アプリケーションの更新プログラムを確認する必要があります** チェック ボックスをオンします。  
  
5.  選択、**このアプリケーションの最低限必要なバージョン指定**チェック ボックスをオンにし、入力**メジャー**、**マイナー**、**ビルド**、および**リビジョン**アプリケーションの番号。  
  
### <a name="to-specify-a-different-update-location"></a>さまざまな更新プログラムの場所を指定するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  をクリックして、**更新**ボタンをクリックする、**アプリケーションの更新プログラム** ダイアログ ボックス。  
  
4.  **アプリケーションの更新プログラム** ダイアログ ボックスで、ことを確認します、**アプリケーションの更新プログラムを確認する必要があります** チェック ボックスをオンします。  
  
5.  **の場所を更新**フィールドに、形式を使用して、完全修飾 URL で更新プログラムの場所を入力*http://Hostname/ApplicationName*、または UNC パス形式を使用して *\\\Server\ApplicationName*、 をクリックしてまたは、**参照**更新プログラムの場所を参照するボタンをクリックします。  
  
### <a name="to-check-for-updates-programmatically"></a>プログラムで更新プログラムを確認するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  をクリックして、**更新**ボタンをクリックする、**アプリケーションの更新プログラム** ダイアログ ボックス。  
  
4.  **アプリケーションの更新プログラム** ダイアログ ボックスに、必ず、**アプリケーションの更新プログラムを確認する必要があります**チェック ボックスをオフします。 (必要に応じて、更新プログラムと、ClickOnce ランタイムが自動的に更新プログラムの確認のチェックには、このチェック ボックスをオンできます)。  
  
5.  **の場所を更新**フィールドに、形式を使用して、完全修飾 URL で更新プログラムの場所を入力*http://Hostname/ApplicationName*、または UNC パス形式を使用して *\\\Server\ApplicationName*、 をクリックしてまたは、**参照**更新プログラムの場所を参照するボタンをクリックします。 更新プログラムの場所は、アプリケーションはそれ自体の更新バージョンを探します。  
  
6.  ユーザーが更新をチェックする選択が Windows フォームにボタン、メニュー項目、またはその他のユーザー インターフェイス項目を作成します。 その項目のイベント ハンドラーからの確認し、更新プログラムをインストールするメソッドを呼び出します。 このようなメソッドの Visual Basic および Visual c# のコードの例を見つけることができます[方法: ClickOnce 配置 API を使用してプログラムでアプリケーションの更新プログラムの確認](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)します。  
  
7.  アプリケーションをビルドします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [アプリケーションの更新 ダイアログ ボックス](http://msdn.microsoft.com/en-us/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [ClickOnce の更新方法を選択します。](../deployment/choosing-a-clickonce-update-strategy.md)   
 [学ぶことのできる ClickOnce を発行します。](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションの発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [方法: ClickOnce 配置 API を使用してプログラムでアプリケーションの更新プログラムの確認](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)