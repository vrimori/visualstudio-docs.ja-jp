---
title: ヘルプ ビューアーの管理者ガイド | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f470c55b08cc559e481ed75e962fda4f0e625a5c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871291"
---
# <a name="help-viewer-administrator-guide"></a>ヘルプ ビューアー の管理者ガイド
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ヘルプ ビューアーを使用すると、インターネット アクセスの有無に関係なく、ネットワーク環境のローカル ヘルプのインストールを管理できます。 ローカル ヘルプ コンテンツは、コンピューターごとに構成されます。 既定では、ユーザーがローカル ヘルプのインストールを更新するには、そのユーザーに管理者権限が必要です。  
  
 クライアントがインターネットにアクセスできるネットワーク環境では、ヘルプ ビューアーによって、コマンド ライン スクリプトを使用してインターネットからローカル ヘルプ コンテンツを配置できるようになります。  
  
 クライアントがインターネットにアクセスできないネットワーク環境では、ヘルプ ビューアーを使用して、イントラネットまたはネットワーク共有からローカル ヘルプ コンテンツを配置できます。 また、レジストリ キーのオーバーライドを使用して、オンライン/オフライン ヘルプの切り替えや IDE の最初の起動時のコンテンツのインストールなど、Visual Studio IDE のヘルプ オプションを無効にし、イントラネット コンテンツ サービスを指定し、コンテンツを管理することもできます。  
  
 基本構文は次のとおりです。  
  
 \<*パス*> \HlpCtntmgr.exe/operation \<*引数*>/catalogname \<*名前*>/locale \<*ロケール*>/sourceuri \< *.msha パスまたは URL*>  
  
 HlpCtntMgr.exe のコマンド ライン構文の詳細については、「[ヘルプ コンテンツ マネージャーのコマンド ライン引数](../ide/command-line-arguments-for-the-help-content-manager.md)」を参照してください。  
  
 コンテンツの作成、イントラネット サービスのエンドポイントの作成、および類似した種類のアクティビティの詳細については、ヘルプ ビューアー SDK を参照してください。  
  
## <a name="deploying-local-help-content-from-the-internet"></a>インターネットからのローカル ヘルプ コンテンツの配置  
 MSDN のコンテンツ パッケージ サービスを使用して、ローカル ヘルプ コンテンツをインターネットからクライアント コンピューターに配置できます。 このコマンドの構文は次のとおりです。  
  
 \\<*パス*> \v2.2\HlpCtntmgr.exe/operation \<*名前*>/catalogname \<*カタログ名*>/locale \< *ロケール*>  
  
 HlpCtntMgr.exe のコマンド ライン構文の詳細については、「[ヘルプ コンテンツ マネージャーのコマンド ライン引数](../ide/command-line-arguments-for-the-help-content-manager.md)」を参照してください。  
  
 要件:  
  
- クライアント コンピューターは、インターネットにアクセスできる必要があります。  
  
- インストール後にユーザーがローカル ヘルプ コンテンツを更新、追加、または削除するには、そのユーザーに管理者権限が必要です。  
  
  注意事項:  
  
- ヘルプの既定のソースはオンラインのままです。  
  
  > [!TIP]
  >  レジストリ キー HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\14.0\help\UseOnlineHelp を変更することで、ヘルプの既定のソースを変更できます。 詳細については、「[ヘルプ コンテンツ マネージャーのオーバーライド](../ide/help-content-manager-overrides.md)」を参照してください。  
  
- Visual Studio の最初の起動時には、基本ヘルプ コンテンツをインストールするよう求めるメッセージが表示されます。 レジストリ キー HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\14.0\Help\DisableFirstRunHelpSelection を変更することで、このメッセージを無効にできます。  
  
### <a name="example"></a>例  
 次の例では、クライアント コンピューターに Visual Studio の英語のコンテンツをインストールします。  
  
##### <a name="to-install-english-content-from-the-internet"></a>インターネットから英語のコンテンツをインストールするには  
  
1.  **[スタート]** を選択し、**[ファイル名を指定して実行]** を選択します。  
  
2.  次のように入力します。  
  
     C:\Program Files (x86)\Microsoft Help Viewer\v2.2\hlpctntmgr.exe /operation install /catalogname VisualStudio14 /locale en-us  
  
3.  ENTER キーを押します。  
  
## <a name="deploying-pre-installed-local-help-content-on-client-computers"></a>クライアント コンピューターに事前にインストールされたローカル ヘルプ コンテンツの配置  
 オンラインから 1 台のコンピューターに一連のコンテンツをインストールし、そのインストールされたコンテンツを他のコンピューターにコピーすることができます。  
  
 要件:  
  
- 最初にコンテンツをインストールするコンピューターでは、インターネットにアクセスできる必要があります。  
  
- インストール後にユーザーがローカル ヘルプ コンテンツを更新、追加、または削除するには、そのユーザーに管理者権限が必要です。  
  
  > [!TIP]
  >  ユーザーに管理者権限がない場合は、ヘルプ ビューアーで [コンテンツの管理] タブを無効にすることをお勧めします。 詳細については、「[ヘルプ コンテンツ マネージャーのオーバーライド](../ide/help-content-manager-overrides.md)」を参照してください。  
  
  注意事項:  
  
- ユーザーに管理者権限がない場合は、ヘルプ ビューアーで [コンテンツの管理] タブを無効にすることをお勧めします。 詳細については、「[ヘルプ コンテンツ マネージャーのオーバーライド](../ide/help-content-manager-overrides.md)」を参照してください。  
  
- ヘルプの既定のソースはオンラインのままです。  
  
- Visual Studio の最初の起動時には、基本ヘルプ コンテンツをインストールするよう求めるメッセージが表示されます。 詳細については、「[ヘルプ コンテンツ マネージャーのオーバーライド](../ide/help-content-manager-overrides.md)」を参照してください。  
  
### <a name="create-the-content-set"></a>コンテンツ セットを作成する  
 基本コンテンツ セットを作成する前に、ターゲット コンピューターで Visual Studio のすべてのローカル コンテンツをアンインストールする必要があります。  
  
##### <a name="to-uninstall-local-help"></a>ローカル ヘルプをアンインストールするには  
  
1. ヘルプ ビューアーで、**[コンテンツの管理]** タブを選択します。  
  
2. **利用可能なドキュメント**、Visual Studio のドキュメント セットに移動します。  
  
3. 各サブ項目の横の **[削除]** を選択します。  
  
4. 選択**開始**をアンインストールするには  
  
5. 参照する*n*: \ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12 フォルダーにファイル catalogType.xml にはのみが含まれていることを確認します。  
  
   前にインストールされた Visual Studio のローカル ヘルプ コンテンツをすべて削除したら、基本コンテンツ セットをダウンロードする準備が整いました。  
  
##### <a name="to-download-the-content"></a>コンテンツをダウンロードするには  
  
1. ヘルプ ビューアーで、**[コンテンツの管理]** タブを選択します。  
  
2. **利用可能なドキュメント**、クリックしてダウンロードするドキュメント セットに移動**追加**します。  
  
3. **[開始]** を選択します。  
  
   次に、クライアント コンピューターに配置できるように、コンテンツをパッケージ化する必要があります。  
  
##### <a name="to-package-the-content"></a>コンテンツをパッケージ化するには  
  
1.  後の配置でコンテンツをコピーするフォルダーを作成します。  
  
     たとえば、c:\VS12Help フォルダーを作成します。  
  
2.  管理者のアクセス許可で cmd.exe を開きます。  
  
3.  手順 1 で作成したフォルダーに移動します。  
  
4.  次のように入力します。  
  
     Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 \< *foldername*> \/y/e/k/o  
  
     例: `Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 c:\VS12Help\ /y /e /k /o`  
  
### <a name="deploying-the-content"></a>コンテンツの配置  
  
##### <a name="to-deploy-the-content"></a>コンテンツを配置するには  
  
1.  ネットワーク共有を作成し、その場所に theee ヘルプ コンテンツをコピーします。  
  
     たとえば、c:\VS12Help へのコンテンツをコピー \\\myserver\VS12Help します。  
  
2.  ヘルプ コンテンツの配置スクリプトを含める .bat ファイルを作成します。 クライアントがプッシュの一部として、削除されるファイルのいずれかに読み取りロックを設定している可能性があるため、更新をプッシュする前にクライアントをシャットダウンする必要があります。  
  
     次に例を示します。  
  
    ```  
    REM - copy pre-ripped content to ProgramData  
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o  
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to Programdata (%ERRORLEVEL%)  
  
    REM - get processor type and create/run registry update file  
    IF "%PROCESSOR_ARCHITECTURE%"=="AMD64" GOTO AMD64  
  
    @echo Architecture type is x86  
  
    ECHO Windows Registry Editor Version 5.00 > x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs] >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12] >> x86.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "FirstTimeRun"="False"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12\en-US]  >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help]  >> x86.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x86.reg  
  
    regedit.exe /s x86.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x86 reg (%ERRORLEVEL%)  
  
    GOTO CONTINUE  
  
    :AMD64  
    @echo Architecture type is AMD64  
  
    ECHO Windows Registry Editor Version 5.00 > x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs] >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14] >> x64.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio14\\"  >> x64.reg  
    ECHO "FirstTimeRun"="False"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14\en-US]  >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\en-US\\"  >> x64.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\VSWinExpress\14.0\help]  >> x64.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x64.reg  
  
    regedit.exe /s x64.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x64 reg (%ERRORLEVEL%)  
  
    :CONTINUE  
    ```  
  
3.  ヘルプ コンテンツをインストールするローカル コンピューターで、bat ファイルを実行します。  
  
## <a name="see-also"></a>関連項目  
 [ヘルプ コンテンツ マネージャーのコマンドライン引数](../ide/command-line-arguments-for-the-help-content-manager.md)   
 [ヘルプ コンテンツ マネージャーのオーバーライド](../ide/help-content-manager-overrides.md)



