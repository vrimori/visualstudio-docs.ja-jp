---
title: Office ソリューションの配置のトラブルシューティング |Microsoft ドキュメント
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
ms.openlocfilehash: 29c3cfdcf31609eb5b6aec0111fe2297ba8c01ef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-office-solution-deployment"></a>Office ソリューション配置のトラブルシューティング
  このトピックでは、Office ソリューションを配置するときに発生する可能性がある一般的な問題を解決する方法について説明します。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="troubleshooting-office-solutions-by-using-the-event-viewer"></a>イベント ビューアーを使用した Office ソリューションのトラブルシューティング  
 Windows のイベント ビューアーを使用すると、Office ソリューションのインストール時またはアンインストール時に [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] でキャプチャされるエラー メッセージを表示できます。 イベント ロガーからのこれらのメッセージを使用して、インストールと配置の問題を解決できます。 詳細については、「 [Event Logging for Office Solutions](../vsto/event-logging-for-office-solutions.md)」を参照してください。  
  
## <a name="changing-the-assembly-name-causes-conflicts"></a>アセンブリ名の変更は競合発生の原因となる  
 変更した場合、**アセンブリ名**値で、**アプリケーション**のページ、**プロジェクト デザイナー**発行ツールによって変更は、ソリューションを配置した後、セットアップ パッケージ 1 つの Setup.exe ファイルと 2 つの配置マニフェストが必要です。 2 つのマニフェスト ファイルを配置すると、次のような状況が発生する場合があります。  
  
-   エンド ユーザーが両方のバージョンをインストールすると、アプリケーションは両方の VSTO アドインを読み込みます。  
  
-   VSTO アドインがインストールされている状態でアセンブリの名前を変更すると、エンド ユーザーが更新を受け取ることはなくなります。  
  
 これらの条件を回避するのには、ソリューションの変更しない**アセンブリ名**ソリューションを配置した後の値します。  
  
## <a name="checking-for-updates-takes-a-long-time"></a>更新プログラムのチェックに長い時間がかかる  
 Visual Studio 2010 Tools for Office Runtime には、マニフェストやソリューションをダウンロードするときのタイムアウト値を設定するために管理者が使用できるように、レジストリ エントリが用意されています。  
  
#### <a name="to-set-the-time-out-value"></a>タイムアウト値を設定するには  
  
1.  レジストリで、次のキーに移動します。  
  
     HKEY_CURRENT_USER\Software\Microsoft\VSTA  
  
2.  **AddInTimeout** サブキーに、タイムアウト値をミリ秒単位で設定します。  
  
     **[AddInTimeout]** サブキーが存在しない場合は、DWORD として作成します。  
  
## <a name="cant-update-or-publish-to-a-network-file-share"></a>ネットワーク ファイル共有に対する更新または発行ができない  
 ネットワーク ファイル共有にある Office ソリューションは、更新の発行プロセスでソリューションの Setup.exe ファイルがロックされると、誤解を招くメッセージを表示することがあります。 たとえば、"'setup.exe' を Web サイトに追加できません。 ファイル 'setup.exe' はこの Web サイトに既に存在します。" というメッセージが表示されることがあります。  
  
 ファイルがロックされないようにするには、エンド ユーザーに対して共有を読み取り専用に設定します。 ただし、共有上にドキュメントがあると、このドキュメントもエンド ユーザーに対して読み取り専用になります。  
  
## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Microsoft Office の必須コンポーネントがインストールされていない  
 セットアップ パッケージには、Office ソリューションと共に配置される必須コンポーネントとして、.NET Framework、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]、および Office プライマリ相互運用機能アセンブリを追加できます。 プライマリ相互運用機能アセンブリをインストールする方法については、次を参照してください。 [Office ソリューションの開発コンピューターを構成する](../vsto/configuring-a-computer-to-develop-office-solutions.md)と[する方法: Office のプライマリ相互運用機能アセンブリをインストール](../vsto/how-to-install-office-primary-interop-assemblies.md)です。  
  
## <a name="publishing-using-localhost-can-cause-installation-problems"></a>"Localhost" を使用して発行するとインストール問題が生じることがある  
 使用すると"http://localhost"、発行場所またはインストール先のドキュメント レベルのソリューションとして、**発行ウィザード**実際のコンピューター名に文字列を変換されません。 この場合は、ソリューションを開発用コンピューター上にインストールする必要があります。 配置ソリューションに開発用コンピューター上の IIS を使用させるには、HTTP、HTTPS、FTP のすべての場所について、localhost ではなく完全修飾名を使用します。  
  
## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>更新済みのアセンブリではなくキャッシュしたアセンブリが読み込まれる  
 プロジェクトの出力パスがネットワーク ファイル共有上にあり、アセンブリが厳密な名前で署名されていて、カスタマイズ アセンブリのバージョンが変更されていない場合、.NET Framework アセンブリ ローダーである fusion は、キャッシュしたアセンブリのコピーを読み込みます。 アセンブリを更新しても、これらの条件が満たされるとキャッシュしたコピーが読み込まれるため、プロジェクトを次回実行するときに更新は表示されません。  
  
 Visual Studio を構成し、プロジェクトを実行するたびに fusion がアセンブリをダウンロードするように設定できます。  
  
#### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>キャッシュしたコピーではなくアセンブリをダウンロードするには  
  
1.  メニュー バーで、次のように選択します。**プロジェクト**、* ProjectName ***プロパティ**です。  
  
2.  **[アプリケーション]** ページで、 **[アセンブリ情報]** を選択します。  
  
3.  最初の**アセンブリ バージョン**ボックスで、アスタリスクを入力 (\*) を選択し、 **[ok]** ボタンをクリックします。  
  
 アセンブリのバージョンを変更したら、厳密な名前でアセンブリに署名します。fusion が最新バージョンのカスタマイズを読み込むようになります。  
  
## <a name="installation-fails-when-the-uri-has-characters-that-aret-us-ascii"></a>URI に US-ASCII 以外の文字が含まれているとインストールが失敗する  
 Office ソリューションを HTTP、HTTPS、または FTP のいずれかの場所に発行する場合、US-ASCII ではない Unicode 文字をパスに含めることはできません。 これらの文字を使用すると、セットアップ プログラムで一貫性のない動作が実行されることがあります。 インストール パスには、US-ASCII 文字を使用してください。  
  
## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>開発用コンピューターにソリューションを発行およびインストールすると手動でアンインストールするよう求めるプロンプトが表示される  
 Office ソリューションをビルドすると、そのビルド バージョンが自動的に登録されます。 開発用コンピューターに同じソリューションを以前に発行およびインストールしていた場合は、次のビルド後、リビルド後、または発行後に、発行されたバージョンとビルドされたバージョンのインストール パスが違うことが [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] によって検出されます。 "現在他のバージョンがインストールされており、この場所からアップグレードすることはできないため、このカスタマイズをインストールすることはできません。" というエラー メッセージが表示されます。 レジストリ キーは、ソリューションがビルドされるたびに更新されます。 したがって、新しいバージョンを発行、デバッグ、または実行する前に、以前のバージョンをアンインストールする必要があります。  
  
 このメッセージが表示されないようにするには、開発用コンピューターで別のユーザー アカウントを作成して配置をテストします。 または、次回のソリューションの発行、デバッグ、またはリビルドの前に、コンピューター上にインストールされているプログラムの一覧からそのバージョンをアンインストールできます。  
  
## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>ソリューションをインストールするときキャッチされない例外やメソッドが見つからないエラーが発生する  
 配置マニフェスト (.vsto ファイル)、Office アプリケーション、ドキュメント、またはブックを開いて Office ソリューションをインストールすると、次の状態に対するエラー メッセージが表示される場合があります。  
  
-   メソッドが見つからない  
  
-   MissingMethodException  
  
-   キャッチされない例外  
  
 これらのエラー メッセージが表示されないようにするには、セットアップ プログラムを実行することにより、ソリューションをインストールします。  
  
 セットアップ プログラムを実行せずにソリューションをインストールする場合、インストーラーでは、必須コンポーネントの有無のチェックや、それらのインストールは行われません。 セットアップ プログラムは、正しいバージョンの必須コンポーネントをチェックし、必要に応じて、これらをインストールします。  
  
## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>InstallShield Limited Edition プロジェクトをビルドした後にアドイン用マニフェスト レジストリ キーが変わる  
 VSTO アドイン セットアップ プログラムに含まれるマニフェスト レジストリ キーが、InstallShield Limited Edition プロジェクトのビルド時に .vsto から .dll.manifest に変わる場合があります。  
  
 この問題の発生を防ぐには、InstallShield Limited Edition プロジェクトを別のソリューションで作成するか、レジストリ キー値として VSTO アドイン名が含まれる CompanyName.AddinName を使用します。  
  
## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Office ソリューションの ClickOnce インストーラーがプライマリ相互運用機能アセンブリをインストールしない  
 Office ソリューション用に ClickOnce が作成するセットアップ プログラムを実行すると、Office プライマリ相互運用機能アセンブリ (PIA) がまだインストールされていない場合のみ、PIA のインストーラーが実行されます。  
  
 セットアップ プログラムで PIA が正しくインストールされない場合、インストール ディレクトリから o2007pia.msi というインストーラー ファイルを実行して PIA を手動でインストールします。  
  
## <a name="reinstalling-office-solutions-causes-an-argument-out-of-range-exception"></a>Office ソリューションを再インストールすると、引数が範囲外という例外が発生する  
 Office ソリューションを再インストールするときに、 <xref:System.ArgumentOutOfRangeException> 例外が発生し、"指定された引数は、有効な値の範囲内にありません" というエラー メッセージが表示される場合があります。  
  
 インストール場所の URL の大文字と小文字が違っていると、この状況が発生します。 Office ソリューションをインストールした場合このエラーが表示されるなど、 [ http://fabrikam.com/ExcelSolution.vsto ](http://fabrikam.com/ExcelSolution.vsto)初めてし、使用[ http://fabrikam.com/excelsolution.vsto ](http://fabrikam.com/excelsolution.vsto) 2 番目の時間。  
  
 このエラー メッセージが表示されないようにするには、Office ソリューションのインストール時に、同じ大文字と小文字の組み合わせを使用します。  
  
## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Web で配置マニフェストを開いても ClickOnce ソリューションをインストールできない  
 ユーザーは、Web で配置マニフェストを開くことにより、Office ソリューションをインストールできます。 ただし、一部のインターネット インフォメーション サービス (IIS) がインストールされていると、.vsto ファイル名拡張子はブロックされます。 IIS を使用して Office ソリューションを配置する前に、IIS で MIME の種類を定義する必要があります。  
  
 IIS 6 で MIME の種類を定義する方法については、「 [MIME の種類を構成する (IIS 6.0)](http://www.microsoft.com/technet/prodtechnol/WindowsServer2003/Library/IIS/cd72c0dc-c5b8-42e4-96c2-b3c656f99ead.mspx?mfr=true)」をご覧ください。  
  
 IIS 7 で MIME の種類を定義する方法については、「 [MIME の種類を追加する (IIS 7)](http://technet.microsoft.com/library/cc725608(WS.10).aspx)」をご覧ください。  
  
 拡張子を **.vsto** に、MIME の種類を " **application/x-ms-vsto**" に設定します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置のトラブルシューティング](/visualstudio/deployment/troubleshooting-clickonce-deployments)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)  
  
  