---
title: "コマンドラインから ClickOnce アプリケーションをビルド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
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
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 86dba79e6e8b7e3f3b2837e494cfeddd2692d0cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="building-clickonce-applications-from-the-command-line"></a>ClickOnce アプリケーションのコマンド ラインからのビルド
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]、統合開発環境 (IDE) で作成される場合でも、コマンドラインからのプロジェクトをビルドすることができます。 実際で作成されたプロジェクトを再構築する[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]のみを持つ別のコンピューターで、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]インストールします。 これにより、自動プロセスを使用してビルドを再生成するなど、中央のビルド ラボまたはを使用して高度なスクリプティング プロジェクト自体のビルドの対象外の手法です。  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>ClickOnce アプリケーションの展開を再現するのに MSBuild の使用  
 プロジェクトをビルドし、作成するには、MSBuild システムをそこで、コマンドラインで msbuild/target:publish を呼び出すとき、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]発行フォルダーでアプリケーションです。 これは選択すると、**発行**IDE でコマンド。  
  
 このコマンドは、Visual Studio コマンド プロンプト環境でのパスでは、msbuild.exe を実行します。  
  
 "Target"は、コマンドを処理する方法には、msbuild のインジケーターです。 Build ターゲットおよび「公開」対象キーのターゲットです。 ビルド ターゲットがビルドを選択する該当するショートカットは、IDE でのコマンド (または f5 キーを押す) します。 プロジェクトをビルドする場合を行うように入力して`msbuild`です。 このコマンドが機能するため、build ターゲットがによって生成されたすべてのプロジェクトの既定のターゲット[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]です。 つまり、明示的にビルド ターゲットを指定する必要はありません。 したがって、`msbuild`入力した場合と同じ操作は、`msbuild /target:build`です。  
  
 `/target:publish`コマンドを発行先を呼び出す MSBuild に指示します。 発行先は、build ターゲットによって異なります。 つまり、発行操作が、ビルド操作のスーパー セットであります。 たとえば、Visual Basic または c# ソース ファイルのいずれかに変更を加えた場合、対応するアセンブリは自動的にして再構築、発行操作します。  
  
 完全を生成する方法について[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]コマンド ライン ツールの Mage.exe を使用して作成する展開、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]マニフェストは、「[チュートリアル: ClickOnce アプリケーションを手動で展開する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)です。  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>作成して、MSBuild を使用して基本的な ClickOnce アプリケーションの構築  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>作成し、ClickOnce プロジェクトの発行  
  
1.  をクリックして**新しいプロジェクト**から、**ファイル**メニュー。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  選択**Windows アプリケーション**し名前を付けます`CmdLineDemo`です。  
  
3.  **ビルド** メニューをクリックして、**発行**コマンド。  
  
     これにより、生成するために、プロジェクトが正しく構成されている、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションの展開。  
  
     発行ウィザードが表示されます。  
  
4.  発行ウィザードで、をクリックして**完了**です。  
  
     Visual Studio では、生成し、Publish.htm と呼ばれる、既定の Web ページを表示します。  
  
5.  プロジェクトを保存しが格納されているフォルダーの場所をメモしておきます。  
  
 上記の手順で作成、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]が最初に発行されているプロジェクト。 これで IDE の外部でビルドを再現することができます。  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>コマンドラインからビルドを再生成するには  
  
1.  [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] を終了します。  
  
2.  Windows から**開始** メニューのをクリックして**すべてのプログラム**、し**Microsoft Visual Studio**、し**Visual Studio Tools**し、**Visual Studio コマンド プロンプト**です。 現在のユーザーのルート フォルダーに、コマンド プロンプトが開きます。  
  
3.  **Visual Studio コマンド プロンプト**、先ほどビルドするプロジェクトの場所に、現在のディレクトリを変更します。 たとえば、「`chdir My Documents\Visual Studio\Projects\CmdLineDemo`です。  
  
4.  生成された既存のファイルを削除する"を作成し、発行、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]プロジェクト、"型`rmdir /s publish`です。  
  
     ここではオプションですを新しいファイルのすべての結果生成されたコマンド ライン ビルドことを確認します。  
  
5.  「`msbuild /target:publish`」と入力します。  
  
 上記の手順が完全に生成されます[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]P を同じ名前のプロジェクトのサブフォルダーにアプリケーション展開**ublish**です。 CmdLineDemo.application は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置マニフェスト。 フォルダー CmdLineDemo_1.0.0.0 CmdLineDemo.exe および CmdLineDemo.exe.manifest、ファイルが含まれています、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション マニフェスト。 Setup.exe は、既定でインストールするように構成するブートス トラップ、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]です。 DotNetFX フォルダーには再頒布可能パッケージが含まれています、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]です。 これは、Web 経由で、または UNC または CD または DVD を使用してアプリケーションを配置する必要があるファイルのセット全体です。  
  
## <a name="publishing-properties"></a>公開プロパティ  
 上記の手順で、アプリケーションを発行すると、次のプロパティが、発行ウィザードでは、プロジェクト ファイルに挿入されます。 これらのプロパティに直接影響を与える方法、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションが生成されます。  
  
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
  
 プロジェクト ファイル自体を変更することがなく、コマンドラインでこれらのプロパティのいずれかをオーバーライドできます。 たとえば、次のビルドは、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ブートス トラップを含まないアプリケーションの展開。  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 公開プロパティで制御[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]から、**発行**、**セキュリティ**、および**署名**のプロパティ ページ、**プロジェクト デザイナー**. 各をアプリケーション デザイナーのさまざまなプロパティ ページを設定する方法を示すと共に、発行のプロパティの説明を次に示します。  
  
-   `AssemblyOriginatorKeyFile`署名に使用されるキー ファイルの決定、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション マニフェスト。 これと同じキーをアセンブリに厳密な名前を割り当てる使用も可能性があります。 このプロパティが設定されて、**署名**のページ、**プロジェクト デザイナー**です。  
  
 次のプロパティが設定、**セキュリティ**ページ。  
  
-   **ClickOnce のセキュリティ設定を有効にする**を決定するかどうか[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]マニフェストが生成されます。 プロジェクトが最初に作成されると、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]マニフェストの生成は既定で無効です。 ウィザードでは、このフラグを初めて発行したときに自動的に起動します。  
  
-   **TargetZone**に出力する信頼のレベルを決定する、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション マニフェスト。 指定できる値は、"Internet"、"LocalIntranet"および"Custom"には。 インターネットと LocalIntranet により、既定の権限に出力するセット、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション マニフェスト。 LocalIntranet は、既定値と基本的には完全な信頼になります。 カスタムでは、基本アプリケーション マニフェスト ファイルで明示的に指定された権限だけに出力することを指定します、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション マニフェスト。 アプリケーション マニフェスト ファイルでは、信頼情報の定義だけを含む部分のマニフェスト ファイルを示します。 隠しファイルを自動的にプロジェクトに追加のアクセス許可を構成するときに、**セキュリティ**ページ。  
  
 次のプロパティが設定、**発行**ページ。  
  
-   `PublishUrl`ここで、アプリケーションの発行を IDE の場所です。 挿入される、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]どちらの場合、アプリケーション マニフェスト、`InstallUrl`または`UpdateUrl`プロパティを指定します。  
  
-   `ApplicationVersion`バージョンを指定、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。 これは、4 桁のバージョン番号です。 最後の数字がある場合、"*"を`ApplicationRevision`ビルド時に、マニフェストに挿入された値と置き換えられます。  
  
-   `ApplicationRevision`リビジョンを指定します。 これは、IDE で発行するたびにインクリメントされる整数です。 自動的に増加がないことを確認はビルド コマンドラインで実行します。  
  
-   `Install`アプリケーションがインストールされているアプリケーションまたは Web からの実行アプリケーションかどうかを判断します。  
  
-   `InstallUrl`(非表示) は、ユーザーがからアプリケーションをインストールする場所の場所です。 場合に、この値が setup.exe ブートス トラップに書き込まれる、指定した場合、`IsWebBootstrapper`プロパティを有効にします。 アプリケーション マニフェストの場合にも挿入された、`UpdateUrl`が指定されていません。  
  
-   `SupportUrl`(非表示) は、場所にリンクされて、**プログラムの追加/削除**インストールされているアプリケーションのダイアログ ボックス。  
  
 次のプロパティが設定されて、**アプリケーションの更新プログラム** ダイアログ ボックスで、**発行**ページ。  
  
-   `UpdateEnabled`更新プログラム、アプリケーションを確認する必要があるかどうかを示します。  
  
-   `UpdateMode`更新プログラムのフォア グラウンドまたはバック グラウンド更新のいずれかを指定します。  
  
-   `UpdateInterval`アプリケーションが更新プログラムを確認する頻度を指定します。  
  
-   `UpdateIntervalUnits`指定するかどうか、`UpdateInterval`時間、日、週単位では、値。  
  
-   `UpdateUrl`(非表示) は、アプリケーションが更新プログラムを受信元となる場所です。 指定した場合、この値は、アプリケーション マニフェストに挿入されます。  
  
-   次のプロパティが設定されて、**発行オプション** ダイアログ ボックスで、**発行**ページ。  
  
-   `PublisherName`インストールするか、アプリケーションを実行しているときに表示されるプロンプトに表示されるパブリッシャーの名前を指定します。 インストールされたアプリケーションの場合も使用されますでフォルダー名を指定、**開始**メニュー。  
  
-   `ProductName`インストールするか、アプリケーションを実行しているときに表示されるプロンプトに表示される製品の名前を指定します。 インストールされたアプリケーションの場合も使用されますでショートカット名を指定、**開始**メニュー。  
  
-   次のプロパティが設定されて、**の前提条件** ダイアログ ボックスで、**発行**ページ。  
  
-   `BootstrapperEnabled`setup.exe ブートス トラップを生成するかどうかを判断します。  
  
-   `IsWebBootstrapper`setup.exe ブートス トラップが Web 経由で、またはディスク ベース モードで動作するかどうかを判断します。  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL、SupportUrl、PublishURL、および UpdateURL  
 次の表は、ClickOnce 配置の 4 つの URL オプションを示します。  
  
|[URL]|説明|  
|----------------|-----------------|  
|`PublishURL`|Web サイトに、ClickOnce アプリケーションをパブリッシュするかどうかに必要です。|  
|`InstallURL`|省略可能です。 インストールのサイトが異なる場合は、この URL オプションを設定、`PublishURL`です。 たとえば、設定する、`PublishURL`を FTP パスに設定し、 `InstallURL` Web URL にします。|  
|`SupportURL`|省略可能です。 サポート サイトと異なる場合は、この URL オプションを設定、`PublishURL`です。 たとえば、設定する、`SupportURL`会社のカスタマー サポート Web サイトにします。|  
|`UpdateURL`|省略可能です。 更新プログラムの場所が異なる場合は、この URL オプションを設定、`InstallURL`です。 たとえば、設定する、`PublishURL`を FTP パスに設定し、 `UpdateURL` Web URL にします。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)