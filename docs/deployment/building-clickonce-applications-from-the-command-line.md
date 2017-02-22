---
title: "ClickOnce アプリケーションのコマンド ラインからのビルド | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 配置, コマンド ラインから"
  - "発行"
  - "発行, ClickOnce"
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce アプリケーションのコマンド ラインからのビルド
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] では、統合開発環境 \(IDE: Integrated Development Environment\) で作成されたプロジェクトをコマンド ラインでビルドすることもできます。  実際、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] で作成したプロジェクトを、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] しかインストールされていない別のコンピューターで再度ビルドできます。  これにより、たとえば中央のビルド ラボで、またはプロジェクト自体のビルドの範囲を超えた高度なスクリプト技術によって、自動化されたプロセスを使用してビルドを再生成できます。  
  
## MSBuild による ClickOnce アプリケーションの配置の再生成  
 コマンド ラインで msbuild \/target:publish を起動すると、このコマンドは MSBuild システムに対して、プロジェクトをビルドして publish フォルダー内に [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを作成するように指示します。  これは、IDE で **\[発行\]** コマンドを選択するのと同じです。  
  
 このコマンドにより、Visual Studio のコマンド プロンプト環境のパス上にある msbuild.exe が実行されます。  
  
 "target" \(ターゲット\) は、MSBuild にコマンドの処理方法を示すインジケーターです。  主なターゲットは "build" ターゲットと "publish" ターゲットです。  build ターゲットは、IDE で \[ビルド\] コマンドを選択する \(または F5 キーを押す\) のと同じです。  単にプロジェクトのビルドを行う場合は、「`msbuild`」と入力します。  このコマンドが機能するのは、build ターゲットが [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] で生成されるすべてのプロジェクトの既定のターゲットであるためです。  つまり、ビルド ターゲットを明示的に指定する必要はありません。  したがって、「`msbuild`」と入力することは、「`msbuild /target:build`」と入力するのと同じ操作になります。  
  
 `/target:publish` コマンドは、publish ターゲットを呼び出すように MSBuild に指示します。  publish ターゲットは build ターゲットに依存します。  つまり、発行操作はビルド操作のスーパーセットです。  たとえば、Visual Basic のソース ファイルや C\# のソース ファイルのいずれかを変更した場合、対応するアセンブリが発行操作によって自動的にビルドし直されます。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] のマニフェストを作成する Mage.exe コマンド ライン ツールを使用して完全な [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の配置を生成する方法については、「[チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)」を参照してください。  
  
## MSBuild による基本的な ClickOnce アプリケーションの作成とビルド  
  
#### ClickOnce プロジェクトを作成して発行するには  
  
1.  **\[ファイル\]** メニューの **\[新しいプロジェクト\]** をクリックします。  **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
2.  **\[Windows アプリケーション\]** をクリックし、「`CmdLineDemo`」という名前を付けます。  
  
3.  **\[ビルド\]** メニューの **\[発行\]** をクリックします。  
  
     この手順により、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの配置を生成するためのプロジェクトが正しく設定されます。  
  
     発行ウィザードが表示されます。  
  
4.  発行ウィザードで、**\[完了\]** をクリックします。  
  
     Publish.htm という名前の既定の Web ページが生成され、表示されます。  
  
5.  プロジェクトを保存し、プロジェクトが格納されたフォルダーの場所をメモします。  
  
 前の手順により、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] プロジェクトが作成され、初めて発行されました。  次に、IDE の外からビルドを再生成します。  
  
#### コマンド ラインでビルドを再生成するには  
  
1.  [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] を終了します。  
  
2.  Windows の **\[スタート\]** メニューをクリックし、**\[すべてのプログラム\]** をポイントします。次に、**\[Microsoft Visual Studio\]** をポイントし、**\[Visual Studio Tools\]** をポイントし、**\[Visual Studio コマンド プロンプト\]** をクリックします。  これにより、現在のユーザーのルート フォルダー内でコマンド プロンプトが開きます。  
  
3.  **\[Visual Studio コマンド プロンプト\]** で、現在のディレクトリを先ほどビルドしたプロジェクトの場所に変更します。  たとえば、「`chdir My Documents\Visual Studio\Projects\CmdLineDemo`」のように入力します。  
  
4.  「[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] プロジェクトを作成して発行するには」で生成された既存のファイルを削除するために、「`rmdir /s publish`」と入力します。  
  
     この手順は省略可能ですが、これにより、新たなファイルがコマンド ラインからのビルドで生成されたファイルだけになります。  
  
5.  「`msbuild /target:publish`」と入力します。  
  
 前の手順により、プロジェクトの **Publish** という名前のサブフォルダー内に、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの配置が生成されます。  CmdLineDemo.application は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の配置マニフェストです。  CmdLineDemo\_1.0.0.0 フォルダーには、CmdLineDemo.exe ファイルと、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーション マニフェストである CmdLineDemo.exe.manifest ファイルが含まれています。  Setup.exe はブートストラップであり、既定では [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] をインストールするように構成されます。  DotNetFX フォルダーには、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の再頒布パッケージが含まれています。  これが、Web、UNC、または CD か DVD を介してアプリケーションを配置するために必要なすべてのファイルのセットです。  
  
## 発行プロパティ  
 上記の手順でアプリケーションを発行するときに、発行ウィザードによって次のプロパティがプロジェクト ファイルに挿入されます。  これらのプロパティは、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの生成方法に直接影響します。  
  
 CmdLineDemo.vbproj または CmdLineDemo.csproj は、次のようになっています。  
  
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
  
 これらのプロパティはいずれも、プロジェクト ファイル自体を変更することなくコマンド ラインでオーバーライドできます。  たとえば、次のように設定すると、ブートストラップを含まない [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの配置をビルドできます。  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 発行プロパティは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の**プロジェクト デザイナー**の **\[発行\]**、**\[セキュリティ\]**、および **\[署名\]** の各プロパティ ページで制御されます。  発行プロパティの説明と、アプリケーション デザイナーのさまざまなプロパティ ページで各プロパティを設定する方法を次に示します。  
  
-   `AssemblyOriginatorKeyFile` は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーション マニフェストへの署名に使用するキー ファイルを決定します。  これと同じキーを、アセンブリへの厳密な名前の割り当てに使用することもできます。  このプロパティは、**プロジェクト デザイナー**の **\[署名\]** ページで設定します。  
  
 次のプロパティは、**\[セキュリティ\]** ページで設定します。  
  
-   **\[ClickOnce セキュリティ設定を有効にする\]** は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] マニフェストを生成するかどうかを決定します。  プロジェクトが最初に作成されたときには、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] のマニフェスト生成は既定で無効になっています。  最初に発行を行うときに、ウィザードでこのフラグが自動的にオンに設定されます。  
  
-   **\[ターゲット ゾーン\]** は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーション マニフェストに与える信頼のレベルを決定します。  設定できる値は、"Internet"、"LocalIntranet"、および "Custom" です。  Internet または LocalIntranet に設定した場合、既定のアクセス許可セットが [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーション マニフェストに与えられます。  LocalIntranet は既定値であり、基本的には完全な信頼を意味します。  Custom に設定した場合は、基本のアプリケーション マニフェスト ファイルに明示的に指定されたアクセス許可だけが [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーション マニフェストに与えられます。  app.manifest ファイルは、信頼情報の定義だけを含む部分的なマニフェスト ファイルです。  これは隠しファイルであり、**\[セキュリティ\]** ページでアクセス許可を設定すると、自動的にプロジェクトに追加されます。  
  
 次のプロパティは、**\[発行\]** ページで設定します。  
  
-   `PublishUrl` は、IDE でのアプリケーションの発行先の場所です。  これは、`InstallUrl` プロパティと `UpdateUrl` プロパティがいずれも指定されていない場合に、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーション マニフェストに挿入されます。  
  
-   `ApplicationVersion` は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションのバージョンを指定します。  これは 4 桁のバージョン番号です。  最後の桁が "\*" の場合は、`ApplicationRevision` の代わりに、ビルド時にマニフェストに挿入された値が使用されます。  
  
-   `ApplicationRevision` はリビジョンを指定します。  これは、IDE で発行を行うたびにインクリメントされる整数です。  コマンド ラインで実行されるビルドの場合、この値は自動的にインクリメントされません。  
  
-   `Install` は、アプリケーションがインストールされるアプリケーションか、または Web から実行されるアプリケーションであるかを決定します。  
  
-   `InstallUrl` \(上記のコードには示されていない\) は、アプリケーションのインストール元の場所です。  指定した場合、`IsWebBootstrapper` プロパティが有効になっているときは、この値が setup.exe ブートストラップに書き込まれます。  また、`UpdateUrl` が指定されていないときは、アプリケーション マニフェストにもこの値が挿入されます。  
  
-   `SupportUrl` \(上記のコードには示されていない\) は、**\[プログラムの追加と削除\]** ダイアログ ボックスでインストール済みアプリケーションにリンクされる場所です。  
  
 次のプロパティは、**\[発行\]** ページからアクセスする **\[アプリケーションの更新\]** ダイアログ ボックスで設定します。  
  
-   `UpdateEnabled` は、アプリケーションが更新プログラムを確認するかどうかを指定します。  
  
-   `UpdateMode` は、フォアグラウンド更新かバックグラウンド更新のいずれかを指定します。  
  
-   `UpdateInterval` は、アプリケーションが更新プログラムを確認する頻度を指定します。  
  
-   `UpdateIntervalUnits` は、`UpdateInterval` の単位を時間、日、週のいずれかに指定します。  
  
-   `UpdateUrl` \(上記のコードには示されていない\) は、アプリケーションが更新プログラムを受け取る場所です。  指定されている場合、この値がアプリケーション マニフェストに挿入されます。  
  
-   次のプロパティは、**\[発行\]** ページからアクセスする **\[発行オプション\]** ダイアログ ボックスで設定します。  
  
-   `PublisherName` は、アプリケーションのインストール時または実行時にプロンプトに表示される発行者の名前を指定します。  インストールされるアプリケーションの場合は、この値が **\[スタート\]** メニューに表示されるフォルダー名の指定にも使用されます。  
  
-   `ProductName` は、アプリケーションのインストール時または実行時にプロンプトに表示される製品名を指定します。  インストールされるアプリケーションの場合は、この値が **\[スタート\]** メニューに表示されるショートカットの名前の指定にも使用されます。  
  
-   次のプロパティは、**\[発行\]** ページからアクセスする **\[必須コンポーネント\]** ダイアログ ボックスで設定します。  
  
-   `BootstrapperEnabled` は、setup.exe ブートストラップを生成するかどうかを決定します。  
  
-   `IsWebBootstrapper` は、setup.exe ブートストラップが Web を介して機能するか、またはディスク ベースのモードで機能するかを決定します。  
  
## InstallURL、SupportUrl、PublishURL、および UpdateURL  
 次の表に、ClickOnce 配置の 4 つの URL オプションを示します。  
  
|URL オプション|Description|  
|---------------|-----------------|  
|`PublishURL`|ClickOnce アプリケーションを Web サイトに発行する場合に必要です。|  
|`InstallURL`|省略可能です。  インストール サイトが `PublishURL` とは異なる場合、この URL オプションを設定します。  たとえば、`PublishURL` を FTP パスに設定し、`InstallURL` を Web の URL に設定することもできます。|  
|`SupportURL`|省略可能です。  サポート サイトが `PublishURL` とは異なる場合、この URL オプションを設定します。  たとえば、`SupportURL` を会社のカスタマー サポート Web サイトに設定することができます。|  
|`UpdateURL`|省略可能です。  更新プログラムの場所が `InstallURL` とは異なる場合、この URL オプションを設定します。  たとえば、`PublishURL` を FTP パスに設定し、`UpdateURL` を Web の URL に設定することもできます。|  
  
## 参照  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)