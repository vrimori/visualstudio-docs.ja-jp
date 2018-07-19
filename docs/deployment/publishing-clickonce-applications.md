---
title: ClickOnce アプリケーションの発行 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Options
- Microsoft.VisualStudio.Publish.ClickOnceProvider.PublishWizard.Help
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- ClickOnce applications, publishing
- applications [Visual Studio], ClickOnce deployment
- deploying applications [ClickOnce], publishing ClickOnce applications
ms.assetid: eb6dfe79-f54c-4331-8e36-073688e70973
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0c6f931af213ff7ce97ec77c2b742d6767cf733
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079252"
---
# <a name="publish-clickonce-applications"></a>ClickOnce アプリケーションを発行します。
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを最初に発行するときに、発行ウィザードを使用して発行プロパティを設定できます。 このウィザードで設定できるのはプロパティの一部のみです。その他のプロパティはすべて、既定値に設定されます。  
  
 プロパティを公開する後続の変更がに対する、**発行**ページで、**プロジェクト デザイナー**します。  
  
## <a name="publish-wizard"></a>発行ウィザード  
 発行ウィザードを使用して、アプリケーションを発行するときの基本的な設定を指定できます。 たとえば、次の発行プロパティが含まれます。  
  
-   発行フォルダーの場所 - Visual Studio がファイルをコピーする場所 (ローカル コンピューター、ネットワーク ファイル共有、FTP サーバー、または Web サイト)。  
  
-   インストール フォルダーの場所 - エンド ユーザーがインストールを開始する場所 (ネットワーク ファイル共有、FTP サーバー、Web サイト、CD/DVD)。  
  
-   オンラインまたはオフラインの可用性 - エンド ユーザーがネットワーク接続でアプリケーションにアクセスできるかどうか。  
  
-   更新間隔 - 新しい更新プログラムをアプリケーションがチェックする頻度。  
  
 詳細については、次を参照してください。[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)します。  
  
## <a name="publish-page"></a>ページの発行  
 **プロジェクト デザイナー** の **[発行]** ページは、ClickOnce 配置用のプロパティを構成する場合に使用します。 次の表では、トピックを示します。  
  
|Title|説明|  
|-----------|-----------------|  
|[方法: Visual Studio がファイルをコピーする場所を指定します。](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Visual Studio がアプリケーション ファイルとマニフェストを配置する場所を設定する方法について説明します。|  
|[方法: エンドユーザーがからインストールする場所を指定](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|ユーザーがアプリケーションをダウンロードし、インストールするためにアクセスする場所を設定する方法について説明します。|  
|[方法: ClickOnce のオフラインを指定するか、オンライン モードのインストール](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|アプリケーションをオフラインまたはオンラインで使用できるかどうかを設定する方法について説明します。|  
|[方法: ClickOnce の発行設定のバージョン](../deployment/how-to-set-the-clickonce-publish-version.md)|ClickOnce を設定する方法について説明します**発行バージョン**を公開するアプリケーションは更新プログラムとして扱うかどうかを決定するプロパティ。|  
|[方法: 発行のバージョンに自動的にインクリメント、ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|リビジョン番号を自動的にインクリメントする方法について説明します、 **PublishVersion**アプリケーションを発行するたびにします。|  
  
 詳細については、次を参照してください[プロジェクト デザイナーの [発行] ページ。](../ide/reference/publish-page-project-designer.md)  
  
### <a name="application-files-dialog-box"></a>アプリケーション ファイル ダイアログ ボックス  
 このダイアログ ボックスでは、発行、動的ダウンロード、および更新のために、プロジェクト内のファイルを分類する方法を指定できます。 このダイアログ ボックスには、既定では除外されないプロジェクト ファイル、またはダウンロード グループのあるプロジェクト ファイルを一覧にしたグリッドが含まれています。  
  
 ファイルを除外するファイルをデータ ファイルや必須コンポーネントとしてマークし、Visual Studio UI で条件付きでインストールするファイルのグループを作成を参照してください[方法: ClickOnce で発行されるファイルの指定](../deployment/how-to-specify-which-files-are-published-by-clickonce.md)します。 また、Mage.exe を使用してデータ ファイルにマークすることもできます。 詳細については、次を参照してください。[方法: ClickOnce アプリケーションにデータ ファイルを含める](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)します。  
  
### <a name="prerequisites-dialog-box"></a>[必須コンポーネント] ダイアログ ボックス  
 このダイアログ ボックスでは、必須コンポーネントとしてインストールするコンポーネントおよびそのインストール方法を指定します。 詳細については、次を参照してください。[方法: ClickOnce アプリケーションと共に必須コンポーネントをインストール](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)と[の前提条件 ダイアログ ボックス](../ide/reference/prerequisites-dialog-box.md)します。  
  
### <a name="application-updates-dialog-box"></a>アプリケーションの更新 ダイアログ ボックス  
 このダイアログ ボックスでは、アプリケーションのインストール時に更新プログラムをチェックする方法を指定します。 詳細については、次を参照してください。[方法: ClickOnce アプリケーションの更新プログラムの管理](../deployment/how-to-manage-updates-for-a-clickonce-application.md)します。  
  
### <a name="publish-options-dialog-box"></a>発行オプション ダイアログ ボックス  
 [発行オプション] ダイアログ ボックスでは、アプリケーションの配置オプションを指定します。  
  
|||  
|-|-|  
|[方法: ClickOnce アプリケーションの発行の言語を変更します。](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|言語およびカルチャを指定してローカライズ版と対応付ける方法について説明します。|  
|[方法: ClickOnce アプリケーションのスタート メニューの名前を指定します。](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|ClickOnce アプリケーションの表示名を変更する方法について説明します。|  
|[方法: テクニカル サポートのリンクを指定](../deployment/how-to-specify-a-link-for-technical-support.md)|設定する方法について説明します、**サポート URL**プロパティで、Web ページまたはアプリケーションに関する情報を取得するユーザーにアクセスできるファイル共有を識別します。|  
|[方法: ClickOnce 配置で個々 の必要条件のサポート URL を指定](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|各必要条件の個別のサポート URL が含まれるようにアプリケーション マニフェストを手動で変更する方法を説明します。|  
|[方法: ClickOnce アプリケーションの発行ページを指定](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|既定の Web ページ (publish.htm) とアプリケーションを生成および発行する方法について説明します。|  
|[方法: ClickOnce の既定の Web ページのカスタマイズ](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|アプリケーションと共に自動的に生成および発行された Web ページをカスタマイズする方法について説明します。|  
|[方法: CD インストールの自動開始を有効にします。](../deployment/how-to-enable-autostart-for-cd-installations.md)|メディアを挿入したときに ClickOnce アプリケーションが自動的に起動するように、自動開始を有効にする方法について説明します。|  
  
## <a name="related-tpics"></a>関連 tpics  
  
|Title|説明|  
|-----------|-----------------|  
|[方法: ファイルの関連付けを ClickOnce アプリケーションの作成](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|ClickOnce アプリケーションにファイル名の拡張子のサポートを追加する方法について説明します。|  
|[方法: オンライン ClickOnce アプリケーションでは、クエリ文字列の情報の取得](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|ClickOnce アプリケーションの実行用 URL に渡されるパラメーターを取得する方法を説明します。|  
|[方法: デザイナーを使用して ClickOnce アプリケーションの URL アクティべーションを無効にします。](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|アプリケーションを開始するユーザーに強制する方法について説明します、**開始**デザイナーを使用してメニュー。|  
|[方法: ClickOnce アプリケーションの URL アクティべーションを無効にします。](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|アプリケーションを開始するユーザーに強制する方法について説明します、**開始**メニュー。|  
|[チュートリアル: ClickOnce 配置デザイナーを使用して API で必要に応じてアセンブリをダウンロードします。](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|デザイナーを使用して、アプリケーションで初めて使用するときにのみアプリケーション アセンブリをダウンロードする方法を説明します。|  
|[チュートリアル: ClickOnce 配置 API で必要に応じてアセンブリをダウンロードします。](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|アプリケーションで初めて使用するときにのみアプリケーション アセンブリをダウンロードする方法を説明します。|  
|[チュートリアル: ClickOnce 配置 API で必要に応じてサテライト アセンブリをダウンロードします。](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|サテライト アセンブリをオプションとしてマークする方法、および現在のカルチャ設定にクライアント コンピューターが必要とするアセンブリのみをダウンロードする方法について説明します。|  
|[チュートリアル: ClickOnce アプリケーションを手動で展開します。](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|.NET Framework ユーティリティを使用して ClickOnce アプリケーションを配置する方法を説明します。|  
|[チュートリアル: 再署名不要ブランド情報を保持する ClickOnce アプリケーションを手動で展開します。](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)|.NET Framework ユーティリティを使用して、マニフェストに再署名せずに ClickOnce アプリケーションを配置する方法について説明します。|  
|[方法: プロジェクトをターゲット プラットフォームを構成します。](../ide/how-to-configure-projects-to-target-platforms.md)|変更することで、64 ビット プロセッサを発行する方法について説明します、**ターゲット CPU**または**プラットフォーム ターゲット**プロジェクトのプロパティ。|  
|[チュートリアル: ClickOnce アプリケーションの複数の .NET Framework のバージョンで実行を有効にします。](http://msdn.microsoft.com/en-us/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|複数バージョンの .NET Framework で ClickOnce アプリケーションのインストールと実行を行う方法について説明します。|  
|[チュートリアル: ClickOnce アプリケーションのカスタム インストーラーを作成します。](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|カスタム インストーラーを作成し、ClickOnce アプリケーションをインストールする方法について説明します。|  
|[方法: visual スタイルが有効になっている WPF アプリケーションの発行](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Visual スタイルが有効になっている WPF アプリケーションを発行しようとしたときに表示されるエラーを解決する手順について説明します。|  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce に関するリファレンス](../deployment/clickonce-reference.md)