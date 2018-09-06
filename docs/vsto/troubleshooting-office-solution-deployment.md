---
title: Office ソリューションのデプロイをトラブルシューティングします。
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9bed7d523d91b43abe5455ea19567da5647f468c
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "43774662"
---
# <a name="troubleshoot-office-solution-deployment"></a>Office ソリューションのデプロイをトラブルシューティングします。
  このトピックでは、Office ソリューションを配置するときに発生する可能性がある一般的な問題を解決する方法について説明します。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>イベント ビューアーを使用して Office ソリューションをトラブルシューティングします。  
 Windows のイベント ビューアーを使用すると、Office ソリューションのインストール時またはアンインストール時に [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] でキャプチャされるエラー メッセージを表示できます。 イベント ロガーからのこれらのメッセージを使用して、インストールと配置の問題を解決できます。 詳細については、次を参照してください。 [Office ソリューションのイベント ログ](../vsto/event-logging-for-office-solutions.md)します。  
  
## <a name="change-the-assembly-name-causes-conflicts"></a>アセンブリの名前を変更して競合を原因します。  
 変更する場合、**アセンブリ名**値、**アプリケーション**のページ、**プロジェクト デザイナー**ソリューションを既にデプロイした後に、発行ツールを変更します1 つのセットアップ パッケージ*Setup.exe*ファイルと 2 つの配置マニフェスト。 2 つのマニフェスト ファイルを配置すると、次のような状況が発生する場合があります。  
  
-   エンド ユーザーが両方のバージョンをインストールすると、アプリケーションは両方の VSTO アドインを読み込みます。  
  
-   VSTO アドインがインストールされている状態でアセンブリの名前を変更すると、エンド ユーザーが更新を受け取ることはなくなります。  
  
 これらの条件を避けるためには、ソリューションを変更しない**アセンブリ名**ソリューションをデプロイした後の値します。  
  
## <a name="check-for-updates-takes-a-long-time"></a>更新時間がかかるを確認してください。  
 Visual Studio 2010 Tools for Office runtime では、管理者を使用して、マニフェストやソリューションをダウンロードするためのタイムアウト値を設定するレジストリ エントリを提供します。  
  
#### <a name="to-set-the-time-out-value"></a>タイムアウト値を設定するには  
  
1.  レジストリで、次のキーに移動します。  
  
     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**  
  
2.  **AddInTimeout** サブキーに、タイムアウト値をミリ秒単位で設定します。  
  
     **[AddInTimeout]** サブキーが存在しない場合は、DWORD として作成します。  
  
## <a name="cant-update-or-publish-to-a-network-file-share"></a>更新またはネットワーク ファイル共有に発行できません。  
 ネットワーク ファイル共有上にある office ソリューションとに、更新中の誤解を招くメッセージを表示可能性があります、ソリューションの*Setup.exe*更新プログラムが公開されているプロセスでファイルがロックされています。 たとえば、"'setup.exe' を Web サイトに追加できません。 ファイル 'setup.exe' はこの Web サイトに既に存在します。" というメッセージが表示されることがあります。  
  
 ファイルがロックされないようにするには、エンド ユーザーに対して共有を読み取り専用に設定します。 ただし、共有上にドキュメントがあると、このドキュメントもエンド ユーザーに対して読み取り専用になります。  
  
## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Microsoft Office の前提条件がインストールされていません。  
 セットアップ パッケージには、Office ソリューションと共に配置される必須コンポーネントとして、.NET Framework、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]、および Office プライマリ相互運用機能アセンブリを追加できます。 プライマリ相互運用機能アセンブリをインストールする方法については、次を参照してください。 [Office ソリューションを開発コンピューターを構成する](../vsto/configuring-a-computer-to-develop-office-solutions.md)と[方法: インストール Office プライマリ相互運用機能アセンブリ](../vsto/how-to-install-office-primary-interop-assemblies.md)します。  
  
## <a name="publish-using-localhost-can-cause-installation-problems"></a>使用して発行 'Localhost' のインストールに関する問題が発生することができます  
 使用すると"http://localhost"ドキュメント レベルのソリューションの発行またはインストールの場所として、**発行ウィザード**実際のコンピューター名を文字列に変換されません。 この場合は、ソリューションを開発用コンピューター上にインストールする必要があります。 配置ソリューションに開発用コンピューター上の IIS を使用させるには、HTTP、HTTPS、FTP のすべての場所について、localhost ではなく完全修飾名を使用します。  
  
## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>キャッシュされたアセンブリが更新されたアセンブリではなく読み込まれる  
 プロジェクトの出力パスがネットワーク ファイル共有上にあり、アセンブリが厳密な名前で署名されていて、カスタマイズ アセンブリのバージョンが変更されていない場合、.NET Framework アセンブリ ローダーである fusion は、キャッシュしたアセンブリのコピーを読み込みます。 アセンブリを更新しても、これらの条件が満たされるとキャッシュしたコピーが読み込まれるため、プロジェクトを次回実行するときに更新は表示されません。  
  
 Visual Studio を構成し、プロジェクトを実行するたびに fusion がアセンブリをダウンロードするように設定できます。  
  
### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>キャッシュしたコピーではなくアセンブリをダウンロードするには  
  
1.  メニュー バーで、**プロジェクト**、 _ProjectName_**プロパティ**します。  
  
2.  **[アプリケーション]** ページで、 **[アセンブリ情報]** を選択します。  
  
3.  最初の**アセンブリのバージョン**ボックスに、アスタリスクを入力 (\*) を選択し、 **[ok]** ボタン。  
  
 アセンブリのバージョンを変更したら、厳密な名前でアセンブリに署名します。fusion が最新バージョンのカスタマイズを読み込むようになります。  
  
## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>URI に US-ASCII ではない文字がある場合、インストールが失敗します。  
 Office ソリューションを HTTP、HTTPS、または FTP のいずれかの場所に発行する場合、US-ASCII ではない Unicode 文字をパスに含めることはできません。 これらの文字を使用すると、セットアップ プログラムで一貫性のない動作が実行されることがあります。 インストール パスには、US-ASCII 文字を使用してください。  
  
## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>発行および開発用コンピューターでソリューションをインストールするときに手動でアンインストールするプロンプトが表示されます。  
 Office ソリューションをビルドすると、そのビルド バージョンが自動的に登録されます。 開発用コンピューターに同じソリューションを以前に発行およびインストールしていた場合は、次のビルド後、リビルド後、または発行後に、発行されたバージョンとビルドされたバージョンのインストール パスが違うことが [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] によって検出されます。 "現在他のバージョンがインストールされており、この場所からアップグレードすることはできないため、このカスタマイズをインストールすることはできません。" というエラー メッセージが表示されます。 レジストリ キーは、ソリューションがビルドされるたびに更新されます。 したがって、新しいバージョンを発行、デバッグ、または実行する前に、以前のバージョンをアンインストールする必要があります。  
  
 このメッセージが表示されないようにするには、開発用コンピューターで別のユーザー アカウントを作成して配置をテストします。 または、次回のソリューションの発行、デバッグ、またはリビルドの前に、コンピューター上にインストールされているプログラムの一覧からそのバージョンをアンインストールできます。  
  
## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>キャッチされない例外やメソッドが見つからないというエラー ソリューションをインストールするときに  
 配置マニフェストを開くことで Office ソリューションをインストールすると (、 *.vsto*ファイル)、次の条件の Office アプリケーション、ドキュメント、またはブックでは、エラー メッセージが表示されます。  
  
-   メソッドが見つからない  
  
-   MissingMethodException  
  
-   キャッチされない例外  
  
 これらのエラー メッセージが表示されないようにするには、セットアップ プログラムを実行することにより、ソリューションをインストールします。  
  
 セットアップ プログラムを実行せずにソリューションをインストールする場合、インストーラーでは、必須コンポーネントの有無のチェックや、それらのインストールは行われません。 セットアップ プログラムは、正しいバージョンの必須コンポーネントをチェックし、必要に応じて、これらをインストールします。  
  
## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>マニフェストのアドインの変更のレジストリ キーが、InstallShield Limited Edition プロジェクトをビルドした後  
 VSTO アドインのセットアップに含まれるマニフェスト レジストリ キーをプログラムから変更こともあります *.vsto*に *..dll.manifest に*InstallShield Limited Edition プロジェクトをビルドする場合。  
  
 この問題の発生を防ぐには、InstallShield Limited Edition プロジェクトを別のソリューションで作成するか、レジストリ キー値として VSTO アドイン名が含まれる CompanyName.AddinName を使用します。  
  
## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Office ソリューションの ClickOnce インストーラーは、プライマリ相互運用機能アセンブリをインストールできません。  
 Office ソリューション用に ClickOnce が作成するセットアップ プログラムを実行すると、Office プライマリ相互運用機能アセンブリ (PIA) がまだインストールされていない場合のみ、PIA のインストーラーが実行されます。  
  
 セットアップ プログラムは、Pia を正しくインストールできない場合に手動で実行してインストールという名前のインストーラー ファイル*o2007pia.msi*インストール ディレクトリから。  
  
## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Office ソリューションの原因の引数が範囲外の例外を再インストールします。  
 Office ソリューションを再インストールするときに、 <xref:System.ArgumentOutOfRangeException> 例外が発生し、"指定された引数は、有効な値の範囲内にありません" というエラー メッセージが表示される場合があります。  
  
 インストール場所の URL の大文字と小文字が違っていると、この状況が発生します。 たとえば、このエラーはから Office ソリューションをインストールした場合に表示されます[ http://fabrikam.com/ExcelSolution.vsto ](http://fabrikam.com/ExcelSolution.vsto)初めてし、使用[ http://fabrikam.com/excelsolution.vsto ](http://fabrikam.com/excelsolution.vsto) 2 回目です。  
  
 このエラー メッセージが表示されないようにするには、Office ソリューションのインストール時に、同じ大文字と小文字の組み合わせを使用します。  
  
## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Web から配置マニフェストを開くことで、ClickOnce ソリューションをインストールすることはできません。  
 ユーザーは、Web で配置マニフェストを開くことにより、Office ソリューションをインストールできます。 ただし、インターネット インフォメーション サービス (IIS) のいくつかのインストールはブロック、 *.vsto*ファイル名拡張子。 Office ソリューションを配置するために使用する前に、IIS で MIME の種類を定義する必要があります。  
  
 IIS 7 で MIME の種類を定義する方法については、次を参照してください。 [MIME の種類 (IIS7) 追加](http://technet.microsoft.com/library/cc725608(WS.10).aspx)します。  
  
 拡張子を **.vsto** に、MIME の種類を " **application/x-ms-vsto**" に設定します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置をトラブルシューティングします。](/visualstudio/deployment/troubleshooting-clickonce-deployments)   
 [Office ソリューションをデプロイします。](../vsto/deploying-an-office-solution.md)  
  
  