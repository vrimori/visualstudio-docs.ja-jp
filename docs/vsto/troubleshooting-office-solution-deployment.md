---
title: Office ソリューションの配置をトラブルシューティングします。
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
ms.openlocfilehash: 854264da676ec52d93030371213fa3d8d57eb69f
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693209"
---
# <a name="troubleshoot-office-solution-deployment"></a>Office ソリューションの配置をトラブルシューティングします。
  このトピックでは、Office ソリューションを配置するときに発生する可能性がある一般的な問題を解決する方法について説明します。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>イベント ビューアーを使用して Office ソリューションをトラブルシューティングします。  
 Windows のイベント ビューアーを使用すると、Office ソリューションのインストール時またはアンインストール時に [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] でキャプチャされるエラー メッセージを表示できます。 イベント ロガーからのこれらのメッセージを使用して、インストールと配置の問題を解決できます。 詳細については、次を参照してください。 [Office ソリューションのイベント ログ](../vsto/event-logging-for-office-solutions.md)です。  
  
## <a name="change-the-assembly-name-causes-conflicts"></a>アセンブリ名の変更には、競合が発生します。  
 変更した場合、**アセンブリ名**値で、**アプリケーション**のページ、**プロジェクト デザイナー**発行ツールによって変更は、ソリューションを配置した後、セットアップ パッケージを 1 つ*Setup.exe*ファイルと 2 つの配置マニフェスト。 2 つのマニフェスト ファイルを配置すると、次のような状況が発生する場合があります。  
  
-   エンド ユーザーが両方のバージョンをインストールすると、アプリケーションは両方の VSTO アドインを読み込みます。  
  
-   VSTO アドインがインストールされている状態でアセンブリの名前を変更すると、エンド ユーザーが更新を受け取ることはなくなります。  
  
 これらの条件を回避するのには、ソリューションの変更しない**アセンブリ名**ソリューションを配置した後の値します。  
  
## <a name="check-for-updates-takes-a-long-time"></a>時間がかかる更新プログラムを確認します。  
 Visual Studio 2010 Tools for Office runtime は、管理者が、マニフェストやソリューションをダウンロードするためのタイムアウト値の設定に使用できるレジストリ エントリを提供します。  
  
#### <a name="to-set-the-time-out-value"></a>タイムアウト値を設定するには  
  
1.  レジストリで、次のキーに移動します。  
  
     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**  
  
2.  **AddInTimeout** サブキーに、タイムアウト値をミリ秒単位で設定します。  
  
     **[AddInTimeout]** サブキーが存在しない場合は、DWORD として作成します。  
  
## <a name="cant-update-or-publish-to-a-network-file-share"></a>更新またはネットワーク ファイル共有に公開できません。  
 Office ソリューションは、ネットワーク ファイル共有上にある可能性があります表示誤解を招くメッセージの更新中に、ソリューションの*Setup.exe*更新プログラムが公開されているプロセスでファイルがロックされています。 たとえば、"'setup.exe' を Web サイトに追加できません。 ファイル 'setup.exe' はこの Web サイトに既に存在します。" というメッセージが表示されることがあります。  
  
 ファイルがロックされないようにするには、エンド ユーザーに対して共有を読み取り専用に設定します。 ただし、共有上にドキュメントがあると、このドキュメントもエンド ユーザーに対して読み取り専用になります。  
  
## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Microsoft Office の前提条件がインストールされていません。  
 セットアップ パッケージには、Office ソリューションと共に配置される必須コンポーネントとして、.NET Framework、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]、および Office プライマリ相互運用機能アセンブリを追加できます。 プライマリ相互運用機能アセンブリをインストールする方法については、次を参照してください。 [Office ソリューションを開発コンピューターを構成する](../vsto/configuring-a-computer-to-develop-office-solutions.md)と[する方法: Office のインストールのプライマリ相互運用機能アセンブリ](../vsto/how-to-install-office-primary-interop-assemblies.md)です。  
  
## <a name="publish-using-localhost-can-cause-installation-problems"></a>使用してパブリッシュ 'Localhost' インストール問題が発生することができます  
 使用すると"http://localhost"、発行場所またはインストール先のドキュメント レベルのソリューションとして、**発行ウィザード**実際のコンピューター名に文字列を変換されません。 この場合は、ソリューションを開発用コンピューター上にインストールする必要があります。 配置ソリューションに開発用コンピューター上の IIS を使用させるには、HTTP、HTTPS、FTP のすべての場所について、localhost ではなく完全修飾名を使用します。  
  
## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>キャッシュしたアセンブリが更新されたアセンブリではなく読み込まれています。  
 プロジェクトの出力パスがネットワーク ファイル共有上にあり、アセンブリが厳密な名前で署名されていて、カスタマイズ アセンブリのバージョンが変更されていない場合、.NET Framework アセンブリ ローダーである fusion は、キャッシュしたアセンブリのコピーを読み込みます。 アセンブリを更新しても、これらの条件が満たされるとキャッシュしたコピーが読み込まれるため、プロジェクトを次回実行するときに更新は表示されません。  
  
 Visual Studio を構成し、プロジェクトを実行するたびに fusion がアセンブリをダウンロードするように設定できます。  
  
### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>キャッシュしたコピーではなくアセンブリをダウンロードするには  
  
1.  メニュー バーで、次のように選択します。**プロジェクト**、* ProjectName ***プロパティ**です。  
  
2.  **[アプリケーション]** ページで、 **[アセンブリ情報]** を選択します。  
  
3.  最初の**アセンブリ バージョン**ボックスで、アスタリスクを入力 (\*) を選択し、 **[ok]** ボタンをクリックします。  
  
 アセンブリのバージョンを変更したら、厳密な名前でアセンブリに署名します。fusion が最新バージョンのカスタマイズを読み込むようになります。  
  
## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>URI がない、US-ASCII 文字をインストールが失敗します。  
 Office ソリューションを HTTP、HTTPS、または FTP のいずれかの場所に発行する場合、US-ASCII ではない Unicode 文字をパスに含めることはできません。 これらの文字を使用すると、セットアップ プログラムで一貫性のない動作が実行されることがあります。 インストール パスには、US-ASCII 文字を使用してください。  
  
## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>発行およびソリューションを開発用コンピューターにインストールするときに手動でアンインストールするプロンプトが表示されます。  
 Office ソリューションをビルドすると、そのビルド バージョンが自動的に登録されます。 開発用コンピューターに同じソリューションを以前に発行およびインストールしていた場合は、次のビルド後、リビルド後、または発行後に、発行されたバージョンとビルドされたバージョンのインストール パスが違うことが [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] によって検出されます。 "現在他のバージョンがインストールされており、この場所からアップグレードすることはできないため、このカスタマイズをインストールすることはできません。" というエラー メッセージが表示されます。 レジストリ キーは、ソリューションがビルドされるたびに更新されます。 したがって、新しいバージョンを発行、デバッグ、または実行する前に、以前のバージョンをアンインストールする必要があります。  
  
 このメッセージが表示されないようにするには、開発用コンピューターで別のユーザー アカウントを作成して配置をテストします。 または、次回のソリューションの発行、デバッグ、またはリビルドの前に、コンピューター上にインストールされているプログラムの一覧からそのバージョンをアンインストールできます。  
  
## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>キャッチされない例外やメソッドが見つからないというエラー ソリューションをインストールするときに  
 配置マニフェストを開いて Office ソリューションをインストールすると (、 *.vsto*ファイル)、次の条件の Office アプリケーション、ドキュメント、またはブック、エラーのメッセージが表示される可能性があります。  
  
-   メソッドが見つからない  
  
-   MissingMethodException  
  
-   キャッチされない例外  
  
 これらのエラー メッセージが表示されないようにするには、セットアップ プログラムを実行することにより、ソリューションをインストールします。  
  
 セットアップ プログラムを実行せずにソリューションをインストールする場合、インストーラーでは、必須コンポーネントの有無のチェックや、それらのインストールは行われません。 セットアップ プログラムは、正しいバージョンの必須コンポーネントをチェックし、必要に応じて、これらをインストールします。  
  
## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>マニフェストのアドインでの変更のレジストリ キーが、InstallShield Limited Edition プロジェクトをビルドした後  
 マニフェスト レジストリ キーは、VSTO アドインのセットアップの一部であるプログラムからの変更の場合もあります *.vsto*に *..dll.manifest に*InstallShield Limited Edition プロジェクトを作成する場合。  
  
 この問題の発生を防ぐには、InstallShield Limited Edition プロジェクトを別のソリューションで作成するか、レジストリ キー値として VSTO アドイン名が含まれる CompanyName.AddinName を使用します。  
  
## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Office ソリューションの ClickOnce インストーラーがプライマリ相互運用機能アセンブリをインストールしません。  
 Office ソリューション用に ClickOnce が作成するセットアップ プログラムを実行すると、Office プライマリ相互運用機能アセンブリ (PIA) がまだインストールされていない場合のみ、PIA のインストーラーが実行されます。  
  
 セットアップ プログラムは、Pia を正しくインストールできない場合に手動で実行してインストールという名前のインストーラー ファイル*o2007pia.msi*インストール ディレクトリからです。  
  
## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Office ソリューションの原因が範囲外の例外の引数を再インストールします。  
 Office ソリューションを再インストールするときに、 <xref:System.ArgumentOutOfRangeException> 例外が発生し、"指定された引数は、有効な値の範囲内にありません" というエラー メッセージが表示される場合があります。  
  
 インストール場所の URL の大文字と小文字が違っていると、この状況が発生します。 Office ソリューションをインストールした場合このエラーが表示されるなど、 [ http://fabrikam.com/ExcelSolution.vsto ](http://fabrikam.com/ExcelSolution.vsto)初めてし、使用[ http://fabrikam.com/excelsolution.vsto ](http://fabrikam.com/excelsolution.vsto) 2 番目の時間。  
  
 このエラー メッセージが表示されないようにするには、Office ソリューションのインストール時に、同じ大文字と小文字の組み合わせを使用します。  
  
## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Web から配置マニフェストを開くことにより、ClickOnce ソリューションをインストールすることはできません。  
 ユーザーは、Web で配置マニフェストを開くことにより、Office ソリューションをインストールできます。 ただし、インターネット インフォメーション サービス (IIS) のブロックの一部のインストール、 *.vsto*ファイル名拡張子。 Office ソリューションを配置に使用する前に、IIS で MIME の種類を定義する必要があります。  
  
 IIS 6 で MIME の種類を定義する方法については、「 [MIME の種類を構成する (IIS 6.0)](http://www.microsoft.com/technet/prodtechnol/WindowsServer2003/Library/IIS/cd72c0dc-c5b8-42e4-96c2-b3c656f99ead.mspx?mfr=true)」をご覧ください。  
  
 IIS 7 で MIME の種類を定義する方法については、次を参照してください。 [MIME の種類 (iis 7) を追加](http://technet.microsoft.com/library/cc725608(WS.10).aspx)です。  
  
 拡張子を **.vsto** に、MIME の種類を " **application/x-ms-vsto**" に設定します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置をトラブルシューティングします。](/visualstudio/deployment/troubleshooting-clickonce-deployments)   
 [Office ソリューションを配置します。](../vsto/deploying-an-office-solution.md)  
  
  