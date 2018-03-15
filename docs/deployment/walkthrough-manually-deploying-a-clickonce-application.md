---
title: "チュートリアル: ClickOnce アプリケーションを手動で展開する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 2e0035641a8ed374892060dbaabe79d808150cc2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>チュートリアル : ClickOnce アプリケーションを手動で配置する
展開する Visual Studio を使用できない場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション、または高度な展開機能を使用する必要があります。 信頼されたアプリケーションの配置などを作成するコマンド ライン ツールの Mage.exe を使用する必要があります、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]マニフェスト。 このチュートリアルを作成する方法について説明、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]コマンド ライン バージョン (Mage.exe) またはマニフェストの生成および編集ツールのグラフィカルなバージョン (MageUI.exe) を使用して展開します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルでは、前提条件と、展開を構築する前に選択する必要のあるオプションの一部はされています。  
  
-   Mage.exe および MageUI.exe をインストールします。  
  
     Mage.exe および MageUI.exe の一部である、[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]です。 必要がありますか、[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]インストールされているかのバージョン、 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] Visual Studio に含まれています。 詳細については、次を参照してください。 [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) msdn です。  
  
-   展開するアプリケーションを提供します。  
  
     このチュートリアルでは、Windows アプリケーションを展開する準備ができていることと仮定します。 このアプリケーションは、AppToDeploy として参照されます。  
  
-   展開の配布方法を決定します。  
  
     配布オプションがあります: Web、ファイル共有、または CD。 詳細については、「 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)」を参照してください。  
  
-   アプリケーションが管理者特権のレベルの信頼を必要とするかどうかを決定します。  
  
     アプリケーションでは、完全信頼が必要な場合 — たとえば、完全なユーザーのシステムへのアクセス: 使用することができます、 `-TrustLevel` Mage.exe のオプションは、この設定です。 アプリケーションの設定、カスタム アクセス許可を定義する場合は、他のマニフェストからインターネットまたはイントラネット アクセス許可のセクションをコピー、ニーズに合わせて変更でき、テキスト エディターまたは MageUI.exe を使用してアプリケーション マニフェストに追加できます。 詳細については、「 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
-   Authenticode 証明書を取得します。  
  
     Authenticode 証明書で配置に署名する必要があります。 証明書を取得すると、証明書機関 (CA) からまたは Visual Studio、MageUI.exe、または MakeCert.exe および Pvk2Pfx.exe ツールを使用してテスト証明書を生成できます。 信頼されたアプリケーションの配置を使用するように選択すると、すべてのクライアント コンピューターに証明書のインストールを 1 回も実行する必要があります。 詳細については、「 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
    > [!NOTE]
    >  CNG 証明書、証明機関から取得できる配置を登録することもできます。  
  
-   アプリケーションに UAC 情報を含むマニフェストがないことを確認します。  
  
     ユーザー アカウント制御 (UAC) 情報を含むマニフェストがアプリケーションになどに含めるかどうかを決定する必要があります、`<dependentAssembly>`要素。 アプリケーション マニフェストを検証するには、Windows Sysinternals を使用することができます[Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035)ユーティリティです。  
  
     アプリケーションに UAC の詳細を含むマニフェストが含まれている場合は、UAC 情報を使用しないで再構築する必要があります。 Visual Studio の c# プロジェクトのプロジェクトのプロパティを開き、[アプリケーション] タブを選択します。**マニフェスト**ドロップダウン リストで、**マニフェストを含まないアプリケーションを作成する**です。 Visual Studio で Visual Basic プロジェクトの場合、プロジェクトのプロパティを開き、[アプリケーション] タブを選択してをクリックして**UAC 設定の表示**です。 マニフェスト ファイルを開いたときに、1 つ内のすべての要素を削除する`<asmv1:assembly>`要素。  
  
-   アプリケーションにクライアント コンピューターでの前提条件が必要かどうかを決定します。  
  
     [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Visual Studio からアプリケーションを配置には、展開に伴う前提条件のインストール ブートス トラップ (setup.exe) を含めることができます。 このチュートリアルに必要な 2 つのマニフェストの作成、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開します。 前提条件のブートス トラップを使用して作成することができます、 [GenerateBootstrapper タスク](../msbuild/generatebootstrapper-task.md)です。  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Mage.exe コマンド ライン ツールを使用してアプリケーションを配置するには  
  
1.  格納するディレクトリを作成、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開ファイル。  
  
2.  作成した、配置ディレクトリでは、バージョン サブディレクトリを作成します。 これが初めてアプリケーションを展開することである場合は、名前、version サブディレクトリ**1.0.0.0**です。  
  
    > [!NOTE]
    >  配置のバージョンは、アプリケーションのバージョンとは異なるできます。  
  
3.  実行可能ファイル、アセンブリ、リソース、およびデータ ファイルを含む、バージョンのサブディレクトリには、すべてのアプリケーション ファイルをコピーします。 必要に応じて、追加のファイルを格納する追加サブディレクトリを作成できます。  
  
4.  開く、[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]または Visual Studio コマンド プロンプトし、バージョンのサブディレクトリに変更します。  
  
5.  Mage.exe への呼び出しで、アプリケーション マニフェストを作成します。 次のステートメントでは、Intel x86 プロセッサで実行するコンパイルされたコードのアプリケーション マニフェストを作成します。  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  後にドット (.) を含めるようにしてください、`-FromDirectory`オプションは、現在のディレクトリを示します。 ドットを指定しない場合、アプリケーション ファイル パスを指定する必要があります。  
  
6.  Authenticode 証明書を使用してアプリケーション マニフェストに署名します。 置き換える*mycert.pfx*を証明書ファイルへのパス。 置き換える*passwd*証明書ファイルのパスワードを使用します。  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     CNG 証明書を使用してアプリケーション マニフェストをサインインするには、次の手順を使用します。 置き換える*cngCert.pfx*を証明書ファイルへのパス。  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7.  配置ディレクトリのルートに移動します。  
  
8.  Mage.exe への呼び出しで配置マニフェストを生成します。 既定では、Mage.exe ではマーク、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]が実行できるようにする両方オンラインとオフラインのインストールされているアプリケーションとして展開します。 アプリケーション使用できるようにする、ユーザーがオンラインのときにのみ、使用、`-Install`の値を持つオプション`false`です。 場合は、既定値を使用して、ユーザーが Web サイトまたはファイル共有からアプリケーションをインストール、以下のことを確認の値、`-ProviderUrl`アプリケーションの場所へのポインターのオプションは、Web サーバーまたは共有フォルダーのマニフェストします。  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Authenticode または CNG 証明書で配置マニフェストに署名します。  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
     または  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
10. 展開ディレクトリでのすべてのファイルを配置先メディアにコピーします。 Web サイトや FTP サイト、ファイル共有、または CD-ROM 上のフォルダーがあります。  
  
11. URL、UNC、またはアプリケーションをインストールするために必要な物理メディアをユーザーに提供します。 URL または UNC を指定する場合は、配置マニフェストに、ユーザーの完全パスを示す必要があります。 AppToDeploy が http://webserver01/ AppToDeploy ディレクトリ内に展開されている場合など、完全な URL パスでは、http://webserver01/AppToDeploy/AppToDeploy.application になります。  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>MageUI.exe のグラフィカル ツールを使用してアプリケーションを配置するには  
  
1.  格納するディレクトリを作成、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開ファイル。  
  
2.  作成した、配置ディレクトリでは、バージョン サブディレクトリを作成します。 これが初めてアプリケーションを展開することである場合は、名前、version サブディレクトリ**1.0.0.0**です。  
  
    > [!NOTE]
    >  配置のバージョンは、アプリケーションのバージョンとは異なる可能性があります。  
  
3.  実行可能ファイル、アセンブリ、リソース、およびデータ ファイルを含む、バージョンのサブディレクトリには、すべてのアプリケーション ファイルをコピーします。 必要に応じて、追加のファイルを格納する追加サブディレクトリを作成できます。  
  
4.  MageUI.exe のグラフィカル ツールを起動します。  
  
    ```  
    MageUI.exe  
    ```  
  
5.  選択して、新しいアプリケーション マニフェストを作成する**ファイル**、**新規**、 **Application Manifest**  メニューからです。  
  
6.  既定の**名前** タブで、この展開の名前とバージョン番号を入力します。 指定しても、**プロセッサ**x86 など、アプリケーションが組み込まれています。  
  
7.  選択、**ファイル** タブで、省略記号ボタンをクリックし、(**.**) ボタンを**アプリケーション ディレクトリ**テキスト ボックス。 フォルダーの参照 ダイアログ ボックスが表示されます。  
  
8.  アプリケーションの場合、ファイルを格納しているバージョンのサブディレクトリを選択し、クリックして**OK**です。  
  
9. インターネット インフォメーション サービス (IIS) から、展開する場合は、選択、**を持たない任意のファイルを .deploy 拡張子に追加の設定と**チェック ボックスをオンします。  
  
10. をクリックして、 **Populate**ファイル リストに、すべてのアプリケーション ファイルを追加するボタンをクリックします。 アプリケーションに 1 つ以上の実行可能ファイルが含まれている場合は、スタートアップ アプリケーションとしてこの展開のメインの実行可能ファイルをマーク を選択して**エントリ ポイント**から、**ファイルの種類**ドロップダウン リスト。 (アプリケーション実行可能ファイルを 1 つだけが含まれている場合 MageUI.exe は対象として設定する。)  
  
11. 選択、**必要なアクセス許可**タブし、アサートするアプリケーションが必要な信頼のレベルを選択します。 既定値は**FullTrust**、ほとんどのアプリケーションに適したされます。  
  
12. 選択**ファイル**、**名前を付けて保存** メニューからです。 アプリケーション マニフェストに署名するよう求められます Signing Options ダイアログ ボックスが表示されます。  
  
13. 場合は、ファイル システム上のファイルとして格納されている証明書がある場合を使用して、**証明書ファイルを使用してサインイン**し、省略記号ボタンを使用して、ファイル システムから証明書を選択 (**.**) ボタンをクリックします。 次に、証明書のパスワードを入力します。  
  
     - または -  
  
     場合は、証明書をコンピューターからアクセス可能な証明書ストアに保持すると、選択、**保存された証明書を使用してサインイン**オプション、および指定されたリストから証明書を選択します。  
  
14. をクリックして**OK**してアプリケーション マニフェストに署名します。 名前を付けて保存 ダイアログ ボックスが表示されます。  
  
15. 名前を付けて保存] ダイアログ ボックスで、[バージョンのディレクトリを指定し、クリックして**保存**です。  
  
16. 選択**ファイル**、**新規**、**配置マニフェストは**配置マニフェストを作成するのには、メニューからです。  
  
17. **名前**タブで、この展開の名前とバージョン番号を指定 (**1.0.0.0**この例では)。 指定しても、**プロセッサ**x86 など、アプリケーションが組み込まれています。  
  
18. 選択、**説明**タブをクリックし、値を指定**パブリッシャー**と**Produc * * * t**です。 (**製品**Windows [スタート] メニュー上のアプリケーションをオフラインで使用するクライアント コンピューターで、アプリケーションをインストールするときに指定された名前を指定します)。  
  
19. 選択、**展開オプション** タブで、および、**開始場所**テキスト ボックスで、Web サーバーまたは共有に、アプリケーション マニフェストの場所を指定します。 たとえば、 \\\myServer\myShare\AppToDeploy.application です。  
  
20. 前の手順では .deploy 拡張子を追加した場合も選択**.deploy ファイル名拡張子を使用して**ここです。  
  
21. 選択、**更新オプション**タブをクリックし、更新するには、このアプリケーションと同様に、どのくらいの頻度を指定します。 アプリケーションで使用する場合<xref:System.Deployment.Application.UpdateCheckInfo>をチェックする更新プログラム自体、クリア、**アプリケーションの更新プログラムを確認する必要があります**チェック ボックスをオンします。  
  
22. 選択、**アプリケーション参照**] タブでをクリックし、 **[マニフェストの**ボタンをクリックします。 [開く] ダイアログ ボックスが表示されます。  
  
23. 先ほど作成したアプリケーション マニフェストを選択し、クリックして**開く**です。  
  
24. 選択**ファイル**、**名前を付けて保存** メニューからです。 配置マニフェストに署名するよう求められます Signing Options ダイアログ ボックスが表示されます。  
  
25. 場合は、ファイル システム上のファイルとして格納されている証明書がある場合を使用して、**証明書ファイルを使用してサインイン**し、省略記号ボタンを使用して、ファイル システムから証明書を選択 (**.**) ボタンをクリックします。 次に、証明書のパスワードを入力します。  
  
     - または -  
  
     場合は、証明書をコンピューターからアクセス可能な証明書ストアに保持すると、選択、**保存された証明書を使用してサインイン**オプション、および指定されたリストから証明書を選択します。  
  
26. をクリックして**OK**して配置マニフェストに署名します。 名前を付けて保存 ダイアログ ボックスが表示されます。  
  
27. **名前を付けて保存**ダイアログ ボックスで、1 つのディレクトリをクリックして、展開のルートに移動**保存**です。  
  
28. 展開ディレクトリでのすべてのファイルを配置先メディアにコピーします。 Web サイトや FTP サイト、ファイル共有、または CD-ROM 上のフォルダーがあります。  
  
29. URL、UNC、またはアプリケーションをインストールするために必要な物理メディアをユーザーに提供します。 URL または UNC を指定すると、配置マニフェストの完全パスをユーザーに示す必要があります。 AppToDeploy が http://webserver01/ AppToDeploy ディレクトリ内に展開されている場合など、完全な URL パスでは、http://webserver01/AppToDeploy/AppToDeploy.application になります。  
  
## <a name="next-steps"></a>次の手順  
 アプリケーションの新しいバージョンを展開する必要がある場合は、新しいバージョンにちなんだ名前の新しいディレクトリを作成します: 1.0.0.1—and が、新しいディレクトリに新しいアプリケーション ファイルをコピーするなどです。 次に、作成し、新しいアプリケーション マニフェストに署名し、更新、および配置マニフェストに署名するには、前の手順に従う必要があります。 両方の Mage.exe で同じより高いバージョンを指定するように注意する`-New`と`-Update`呼び出し、として[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]最上位の左端の整数値で以降のバージョンの更新のみです。 場合 MageUI.exe を使用することができますを更新する、配置マニフェストを開いてを選択すると、**アプリケーション参照**] タブをクリックすると、 **[マニフェスト**ボタンをクリックしを選択して、更新されました。アプリケーション マニフェスト。  
  
## <a name="see-also"></a>参照  
 [Mage.exe (マニフェストの生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (マニフェスト生成および編集ツールのグラフィカル クライアント)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)