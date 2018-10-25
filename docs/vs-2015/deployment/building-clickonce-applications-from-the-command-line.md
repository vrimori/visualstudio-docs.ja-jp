---
title: コマンドラインから ClickOnce アプリケーションの構築 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: dac26a7846f4a6b611c53e9cd537d112a8205d2f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836789"
---
# <a name="building-clickonce-applications-from-the-command-line"></a>ClickOnce アプリケーションのコマンド ラインからのビルド
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]、統合開発環境 (IDE) で作成される場合でも、コマンドラインからプロジェクトをビルドできます。 実際で作成されたプロジェクトを再構築する[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]のみを持つ別のコンピューターで、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]をインストールします。 自動化されたプロセスを使用してビルドを再現することができます、たとえば、中央のビルド ラボまたはを使用して高度なスクリプティング プロジェクト自体のビルドの範囲外の手法です。  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>ClickOnce アプリケーションの展開を再現するために MSBuild の使用  
 プロジェクトをビルドし、作成するには、MSBuild システムに指示がコマンドラインで msbuild/target:publish を呼び出すと、 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] publish フォルダーにアプリケーション。 選択するのと同じ、**発行**IDE でコマンド。  
  
 このコマンドは、Visual Studio コマンド プロンプト環境のパスでは、msbuild.exe を実行します。  
  
 「ターゲット」は、コマンドを処理する方法には、MSBuild にインジケーターです。 キーのターゲットとは、ターゲットの「ビルド」と「発行」のターゲットです。 ビルド ターゲットがビルドを選択するのと同じ IDE でのコマンド (または f5 キーを押す) します。 プロジェクトをビルドする場合は、ことを実現する」と入力して`msbuild`します。 このコマンドは、ビルド ターゲットがによって生成されたすべてのプロジェクトの既定のターゲットであるため[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]します。 つまり、明示的にビルド ターゲットを指定する必要はありません。 したがって、`msbuild`入力と同じ操作は、`msbuild /target:build`します。  
  
 `/target:publish`コマンドは、発行ターゲットを呼び出すための MSBuild に指示します。 発行先は、ビルド ターゲットに依存します。 これは、発行操作は、ビルド操作のスーパー セットであることを意味します。 たとえば、Visual Basic または c# ソース ファイルのいずれかに変更を加えた場合、対応するアセンブリは自動的にして再構築、発行操作。  
  
 完全なを生成する方法について[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Mage.exe コマンド ライン ツールを使用して作成する展開、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]マニフェストを参照してください[チュートリアル: ClickOnce アプリケーションを手動で配置](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)します。  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>作成して、MSBuild を使用して基本的な ClickOnce アプリケーションの構築  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>作成して、ClickOnce プロジェクトを発行するには  
  
1. クリックして**新しいプロジェクト**から、**ファイル**メニュー。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2. 選択**Windows アプリケーション**名前を付けます`CmdLineDemo`します。  
  
3. **ビルド** メニューのをクリックして、**発行**コマンド。  
  
    この手順により、プロジェクトが生成するために正しく構成されている、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーションの展開。  
  
    発行ウィザードが表示されます。  
  
4. 発行ウィザードで、**完了**します。  
  
    Visual Studio では、生成し、Publish.htm と呼ばれる既定の Web ページを表示します。  
  
5. プロジェクトを保存しが格納されているフォルダーの場所をメモしておきます。  
  
   上記の手順では、作成、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]プロジェクトは、最初に公開されています。 IDE の外部でビルドを再現できます。  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>コマンドラインからビルドを再現するには  
  
1. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] を終了します。  
  
2. Windows から**開始** メニューのをクリックして**すべてのプログラム**、し**Microsoft Visual Studio**、し**Visual Studio Tools**、し**Visual Studio コマンド プロンプト**します。 コマンド プロンプトを開き、現在のユーザーのルート フォルダーでこの必要があります。  
  
3. **Visual Studio コマンド プロンプト**、先ほどビルドしたプロジェクトの場所を現在のディレクトリを変更します。 たとえば、「 `chdir My Documents\Visual Studio\Projects\CmdLineDemo`」と入力します。  
  
4. 生成された既存のファイルを削除する"を作成および公開を[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]プロジェクト"型`rmdir /s publish`します。  
  
    この手順は省略可能では、新しいファイルすべてによって生成されたコマンド ライン ビルドになります。  
  
5. 「`msbuild /target:publish`」と入力します。  
  
   上記の手順は、完全な[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]P を同じ名前のプロジェクトのサブフォルダーに、アプリケーションの展開**ublish**します。 CmdLineDemo.application は、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]配置マニフェスト。 フォルダー CmdLineDemo_1.0.0.0 CmdLineDemo.exe および CmdLineDemo.exe.manifest、ファイルが含まれています、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション マニフェスト。 Setup.exe が既定でインストールするように構成するブートス トラップ、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]します。 DotNetFX フォルダーには再頒布可能パッケージが含まれています、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]します。 これは、Web 上または UNC パスまたは CD または DVD を使用して、アプリケーションをデプロイする必要があるファイルのセット全体です。  
  
## <a name="publishing-properties"></a>発行プロパティ  
 上記の手順で、アプリケーションを発行するとき、次のプロパティは、発行ウィザードによって、プロジェクト ファイルに挿入されます。 これらのプロパティに直接影響を与える方法、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーションが生成されます。  
  
 CmdLineDemo.vbproj で/CmdLineDemo.csproj:  
  
```  
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>  
<GenerateManifests>true</GenerateManifests>  
<TargetZone>LocalIntranet</TargetZone>  
<PublisherName>Microsoft</PublisherName>  
<ProductName>CmdLineDemo</ProductName>  
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>  
<Install>true</Install>  
<ApplicationVersion>1.0.0.*</ApplicationVersion>  
<ApplicationRevision>1</ApplicationRevision>  
<UpdateEnabled>true</UpdateEnabled>  
<UpdateRequired>false</UpdateRequired>  
<UpdateMode>Foreground</UpdateMode>  
<UpdateInterval>7</UpdateInterval>  
<UpdateIntervalUnits>Days</UpdateIntervalUnits>  
<UpdateUrlEnabled>false</UpdateUrlEnabled>  
<IsWebBootstrapper>true</IsWebBootstrapper>  
<BootstrapperEnabled>true</BootstrapperEnabled>  
```  
  
 プロジェクト ファイル自体を変更せずには、コマンドラインでこれらのプロパティのいずれかをオーバーライドします。 たとえば、次がビルドされます、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]せず、ブートス トラップ アプリケーションの展開。  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 発行プロパティを制御[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]から、**発行**、**セキュリティ**、および**署名**のプロパティ ページ、**プロジェクト デザイナー**. アプリケーション デザイナーのさまざまなプロパティ ページで設定する各方法を示す値と共に、発行のプロパティの説明を次に示します。  
  
- `AssemblyOriginatorKeyFile` 署名に使用されるキー ファイルを指定します、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション マニフェスト。 これと同じキーをアセンブリに厳密な名前を割り当てることも可能性があります。 このプロパティが設定されて、**署名**のページ、**プロジェクト デザイナー**します。  
  
  次のプロパティが設定、**セキュリティ**ページ。  
  
- **ClickOnce のセキュリティ設定を有効にする**決定かどうか[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]マニフェストが生成されます。 プロジェクトが最初に作成されると、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]マニフェストの生成が既定ではオフです。 ウィザードには、最初に発行するときにこのフラグは自動的に起動します。  
  
- **TargetZone**に出力する信頼のレベルを決定する、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション マニフェスト。 指定できる値は、"Internet"、"LocalIntranet"および"Custom"には。 設定を生成する既定のアクセス許可を原因は Internet、LocalIntranet、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション マニフェスト。 LocalIntranet は、既定値と完全な信頼を基本的に意味します。 カスタムでは、基本アプリケーション マニフェスト ファイルで明示的に指定されたアクセス許可のみに出力することを指定します、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション マニフェスト。 アプリケーション マニフェスト ファイルでは、信頼情報の定義だけを含む部分的なマニフェスト ファイルです。 隠しファイルを自動的にプロジェクトに追加のアクセス許可を構成するときに、**セキュリティ**ページ。  
  
  次のプロパティが設定、**発行**ページ。  
  
- `PublishUrl` IDE でする場所、アプリケーションを発行する場所です。 挿入される、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]どちらの場合、アプリケーション マニフェスト、`InstallUrl`または`UpdateUrl`プロパティを指定します。  
  
- `ApplicationVersion` バージョンを指定します、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション。 これは、4 桁のバージョン番号です。 最後の桁がある場合、"*"を`ApplicationRevision`ビルド時に、マニフェストに挿入された値の代わりに使用します。  
  
- `ApplicationRevision` リビジョンを指定します。 これは、IDE に発行するたびにインクリメントされる整数です。 に対して自動的にインクリメントされていないことをビルド コマンドラインで実行します。  
  
- `Install` アプリケーションがインストールされているアプリケーションまたは Web からの実行アプリケーションかどうかを判断します。  
  
- `InstallUrl` ユーザーがアプリケーションのインストール場所は、(非表示)。 場合に、この値が setup.exe ブートス トラップに書き込まれる、指定されている場合、`IsWebBootstrapper`プロパティを有効にします。 アプリケーション マニフェストの場合にも挿入される、`UpdateUrl`が指定されていません。  
  
- `SupportUrl` (非表示) は、場所にリンクされて、**プログラムの追加/削除**インストールされたアプリケーションのダイアログ ボックス。  
  
  次のプロパティで設定されます、**アプリケーションの更新プログラム** ダイアログ ボックスから、**発行**ページ。  
  
- `UpdateEnabled` アプリケーションの更新プログラムを確認するかどうかを示します。  
  
- `UpdateMode` 更新プログラムのフォア グラウンドまたはバック グラウンド更新のいずれかを指定します。  
  
- `UpdateInterval` アプリケーションの更新プログラムを確認する頻度を指定します。  
  
- `UpdateIntervalUnits` 指定するかどうか、`UpdateInterval`時間、日、または週単位の値は。  
  
- `UpdateUrl` (非表示) は、アプリケーションが更新プログラムを受信場所です。 指定した場合、この値は、アプリケーション マニフェストに挿入されます。  
  
- 次のプロパティで設定されます、**発行オプション** ダイアログ ボックスから、**発行**ページ。  
  
- `PublisherName` インストールするか、アプリケーションを実行しているときに表示されるプロンプトに表示されるパブリッシャーの名前を指定します。 インストールされたアプリケーションの場合にも使用上のフォルダーの名前を指定、**開始**メニュー。  
  
- `ProductName` インストールするか、アプリケーションを実行しているときに表示されるプロンプトに表示される製品の名前を指定します。 インストールされたアプリケーションの場合にも使用のショートカット名を指定する、**開始**メニュー。  
  
- 次のプロパティで設定されます、**の前提条件** ダイアログ ボックスから、**発行**ページ。  
  
- `BootstrapperEnabled` setup.exe ブートス トラップを生成するかどうかを決定します。  
  
- `IsWebBootstrapper` setup.exe ブートス トラップが Web 経由で、またはディスク ベースのモードで動作かどうかを判断します。  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL、SupportUrl、PublishURL、および UpdateURL  
 次の表では、ClickOnce 配置の 4 つの URL オプションを示します。  
  
|[URL]|説明|  
|----------------|-----------------|  
|`PublishURL`|Web サイトに、ClickOnce アプリケーションをパブリッシュするかどうかに必要です。|  
|`InstallURL`|任意。 インストールのサイトが異なる場合、この URL オプションを設定、`PublishURL`します。 たとえば、設定する、`PublishURL`に、FTP パスを設定し、 `InstallURL` Web URL にします。|  
|`SupportURL`|任意。 サポート サイトが異なる場合は、この URL オプションを設定、`PublishURL`します。 たとえば、設定する、`SupportURL`会社の顧客のサポート Web サイトにします。|  
|`UpdateURL`|任意。 更新プログラムの場所が異なる場合は、この URL オプションを設定、`InstallURL`します。 たとえば、設定する、`PublishURL`に、FTP パスを設定し、 `UpdateURL` Web URL にします。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)



