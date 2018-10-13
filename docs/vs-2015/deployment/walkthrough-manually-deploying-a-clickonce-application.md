---
title: 'チュートリアル: ClickOnce アプリケーションを手動で展開する |Microsoft Docs'
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
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: 51
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 4e8874324c5e5cbfb5bc42e5c6c23666b5e14b67
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236172"
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>チュートリアル : ClickOnce アプリケーションを手動で配置する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio を使用してデプロイすることはできませんがある場合、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション、または高度な展開の機能を使用する必要があります。 信頼されたアプリケーションの配置などを作成するコマンド ライン ツール Mage.exe を使用する必要があります、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]マニフェスト。 このチュートリアルを作成する方法について説明する[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]コマンド ライン バージョン (Mage.exe) またはマニフェストの生成および編集ツールのグラフィカル バージョン (MageUI.exe) を使用して展開します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルでは、いくつかの前提条件とデプロイを構築する前に選択する必要があるオプションはされています。  
  
-   Mage.exe および MageUI.exe をインストールします。  
  
     Mage.exe および MageUI.exe の一部である、[!INCLUDE[winsdklong](../includes/winsdklong-md.md)]します。 必要か、[!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)]インストールされているかのバージョン、 [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] Visual Studio に含まれています。 詳細については、次を参照してください。 [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) msdn です。  
  
-   展開するアプリケーションを提供します。  
  
     このチュートリアルでは、Windows アプリケーションをデプロイする準備が整いましたがあることを前提としています。 このアプリケーションは、AppToDeploy として参照されます。  
  
-   展開の分散方法を決定します。  
  
     分布オプションを含める: Web、ファイル共有、または CD。 詳細については、「 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)」を参照してください。  
  
-   アプリケーションに管理者特権でのレベルの信頼が必要かどうかを決定します。  
  
     アプリケーションでは、完全信頼が必要な場合: たとえば、ユーザーのシステムへのアクセスを完全: を使用することができます、 `-TrustLevel` Mage.exe のオプションは、この設定。 カスタム アクセス許可は、アプリケーションの設定を定義する場合は、もう 1 つのマニフェストからインターネットまたはイントラネット アクセス許可のセクションをコピーに、ニーズに合わせて変更およびテキスト エディターまたは MageUI.exe を使用して、アプリケーション マニフェストに追加します。 詳細については、「 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
-   Authenticode 証明書を取得します。  
  
     Authenticode 証明書を使用してデプロイを署名する必要があります。 テスト証明書を生成するには、Visual Studio、MageUI.exe、または MakeCert.exe および Pvk2Pfx.exe ツールを使用してまたは証明書機関 (CA) から証明書を取得できます。 信頼されたアプリケーションの配置を使用するように選択した場合はすべてのクライアント コンピューターに証明書のインストールを 1 回も行う必要があります。 詳細については、「 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
    > [!NOTE]
    >  CNG 証明書が証明機関から入手できます。 使用してデプロイを登録することもできます。  
  
-   アプリケーションに UAC 情報を含むマニフェストがないことを確認します。  
  
     アプリケーションがユーザー アカウント制御 (UAC) の情報を含むマニフェストをなど、含まれるかどうかを確認する必要がある、`<dependentAssembly>`要素。 アプリケーション マニフェストを確認するには、Windows Sysinternals を使用できる[Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035)ユーティリティ。  
  
     アプリケーションに UAC の詳細を含むマニフェストが含まれている場合は、UAC 情報を使用しないで再構築する必要があります。 Visual Studio で c# プロジェクトのプロジェクトのプロパティを開き、[アプリケーション] タブを選択します。**マニフェスト**ドロップダウン リストで、**マニフェストを含まないアプリケーションを作成する**します。 Visual Studio で Visual Basic プロジェクトの場合、プロジェクトのプロパティを開き、アプリケーション タブを選択および をクリックして**UAC 設定の表示**します。 マニフェスト ファイルを開いたときに、1 つ内のすべての要素を削除`<asmv1:assembly>`要素。  
  
-   アプリケーションがクライアント コンピューターの前提条件が必要かどうかを決定します。  
  
     [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Visual Studio からデプロイされたアプリケーションは、デプロイの前提条件のインストール ブートス トラップ (setup.exe) を含めることができます。 このチュートリアルで作成に必要な 2 つのマニフェストを[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]展開します。 前提条件のブートス トラップを使用して作成することができます、 [GenerateBootstrapper タスク](../msbuild/generatebootstrapper-task.md)します。  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Mage.exe コマンド ライン ツールを使用してアプリケーションをデプロイするには  
  
1.  格納するディレクトリを作成、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]展開ファイル。  
  
2.  作成した展開ディレクトリでは、バージョン サブディレクトリを作成します。 初めてアプリケーションを展開する場合は、名前、バージョン サブディレクトリ**1.0.0.0**します。  
  
    > [!NOTE]
    >  配置のバージョンをアプリケーションのバージョンとは異なることはできます。  
  
3.  実行可能ファイル、アセンブリ、リソース、およびデータ ファイルを含む、バージョン サブディレクトリには、すべてのアプリケーション ファイルをコピーします。 必要に応じて、追加のファイルが含まれている追加のサブディレクトリを作成できます。  
  
4.  開く、[!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)]または Visual Studio コマンド プロンプトし、バージョンのサブディレクトリに変更します。  
  
5.  Mage.exe への呼び出しでは、アプリケーション マニフェストを作成します。 次のステートメントは、Intel x86 プロセッサで実行するコンパイルされたコードに対するアプリケーション マニフェストを作成します。  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  後にドット (.) を含めるようにしてください、`-FromDirectory`オプションは、現在のディレクトリを示します。 ドットを含めない場合、アプリケーション ファイル パスを指定する必要があります。  
  
6.  Authenticode 証明書をアプリケーション マニフェストに署名します。 置換*mycert.pfx*証明書ファイルへのパス。 置換*passwd*証明書ファイルのパスワードに置き換えます。  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     CNG 証明書を使用してアプリケーション マニフェストをサインインするには、次の手順を使用します。 置換*cngCert.pfx*証明書ファイルへのパス。  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7.  配置ディレクトリのルートに変更します。  
  
8.  Mage.exe への呼び出しで配置マニフェストを生成します。 既定では、Mage.exe ではマーク、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]その it を両方オンラインで実行できるように、オフライン インストールされているアプリケーションとして展開します。 アプリケーションで使用できるように、ユーザーがオンラインの場合にのみ使用して、`-Install`の値を持つオプション`false`します。 場合は、既定値を使用し、ユーザーがアプリケーションを Web サイトまたはファイル共有からインストールを以下のことを確認の値、 `-ProviderUrl` Web サーバーまたは共有でマニフェストのオプションのアプリケーションの場所を指しています。  
  
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
  
10. 配置ディレクトリのすべてのファイルを展開先またはメディアにコピーします。 これにより、Web サイトまたは FTP サイト、ファイル共有、または CD-ROM 上のフォルダーか可能性があります。  
  
11. URL、UNC、またはアプリケーションをインストールするために必要な物理メディアをユーザーに提供します。 URL または UNC を指定する場合は、配置マニフェストに、ユーザーの完全なパスを示す必要があります。 AppToDeploy を配置する場合の例の http://webserver01/ AppToDeploy ディレクトリに完全な URL パスになります。 http://webserver01/AppToDeploy/AppToDeploy.application します。  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>MageUI.exe のグラフィカル ツールを使用してアプリケーションをデプロイするには  
  
1.  格納するディレクトリを作成、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]展開ファイル。  
  
2.  作成した展開ディレクトリでは、バージョン サブディレクトリを作成します。 初めてアプリケーションを展開する場合は、名前、バージョン サブディレクトリ**1.0.0.0**します。  
  
    > [!NOTE]
    >  配置のバージョンは、アプリケーションのバージョンとは異なる可能性があります。  
  
3.  実行可能ファイル、アセンブリ、リソース、およびデータ ファイルを含む、バージョン サブディレクトリには、すべてのアプリケーション ファイルをコピーします。 必要に応じて、追加のファイルが含まれている追加のサブディレクトリを作成できます。  
  
4.  MageUI.exe のグラフィカル ツールを起動します。  
  
    ```  
    MageUI.exe  
    ```  
  
5.  選択して新しいアプリケーション マニフェストを作成する**ファイル**、**新規**、 **Application Manifest**  メニューから。  
  
6.  既定の**名前** タブで、このデプロイの名前とバージョン番号を入力します。 指定することも、**プロセッサ**x86 など、アプリケーションが組み込まれています。  
  
7.  選択、**ファイル** タブで、省略記号をクリックし、(**.**) ボタンの横に、**アプリケーション ディレクトリ**テキスト ボックス。 フォルダーの参照 ダイアログ ボックスが表示されます。  
  
8.  アプリケーション ファイルを格納しているバージョンのサブディレクトリを選択し、クリックして**OK**します。  
  
9. インターネット インフォメーション サービス (IIS) を展開する場合は、選択、**を持たない任意のファイルを .deploy 拡張子に追加の設定と**チェック ボックスをオンします。  
  
10. をクリックして、 **Populate**ファイルの一覧にすべてのアプリケーション ファイルを追加するボタンをクリックします。 アプリケーションには、複数の実行可能ファイルが含まれている場合は、スタートアップ アプリケーションとしては、この展開のメイン実行可能ファイルをマークをオンに**エントリ ポイント**から、**ファイルの種類**ドロップダウン リスト。 (アプリケーションには、1 つだけの実行可能ファイルが含まれる、MageUI.exe は対象として設定する。)  
  
11. 選択、**必要なアクセス許可**タブし、アプリケーションをアサートする必要があることの信頼のレベルを選択します。 既定値は**FullTrust**、ほとんどのアプリケーションに適したされます。  
  
12. 選択**ファイル**、**付けて** メニューから。 署名オプション ダイアログ ボックスでは、アプリケーション マニフェストに署名するよう求められますが表示されます。  
  
13. 場合は、ファイル システム上のファイルとして格納されている証明書がある場合を使用して、**証明書ファイルを使用してサインイン**オプション、およびファイル システムから、省略記号を使用して、証明書を選択します (**.**) ボタンをクリックします。 次に、証明書のパスワードを入力します。  
  
     - または -  
  
     場合は、証明書をコンピューターからアクセス可能な証明書ストアに保持すると、選択、**格納された証明書を使用してサインイン**オプション、および指定された一覧から証明書を選択します。  
  
14. をクリックして**OK**アプリケーション マニフェストに署名します。 名前を付けて保存 ダイアログ ボックスが表示されます。  
  
15. 名前を付けて保存] ダイアログ ボックスで、[バージョンのディレクトリを指定し、クリックして**保存**します。  
  
16. 選択**ファイル**、**新規**、**配置マニフェスト**メニューの配置マニフェストを作成します。  
  
17. **名前**タブで、この展開の名前とバージョン番号を指定 (**1.0.0.0**この例では)。 指定することも、**プロセッサ**x86 など、アプリケーションが組み込まれています。  
  
18. 選択、**説明**タブをクリックし、値を指定**パブリッシャー**と**製品**します。 (**製品**Windows [スタート] メニュー上のアプリケーションをオフラインで使用するクライアント コンピューターで、アプリケーションをインストールするときに指定された名前を指定します)。  
  
19. 選択、**展開オプション** タブで、および、**開始場所**テキスト ボックスで、Web サーバーまたは共有上のアプリケーション マニフェストの場所を指定します。 たとえば、 \\\myServer\myShare\AppToDeploy.application します。  
  
20. 前の手順で .deploy 拡張子を追加した場合も選択 **.deploy ファイル名拡張子を使用して、** ここです。  
  
21. 選択、**更新オプション**タブをクリックし、このアプリケーションを更新を希望する頻度を指定します。 アプリケーションで使用する場合<xref:System.Deployment.Application.UpdateCheckInfo>をチェックする更新プログラム自体、オフ、**アプリケーションの更新プログラムを確認する必要があります**チェック ボックスをオンします。  
  
22. 選択、**アプリケーション参照**] タブをクリックして、 **[マニフェストの**ボタンをクリックします。 開く ダイアログ ボックスが表示されます。  
  
23. 先ほど作成したアプリケーション マニフェストを選択し、クリックして**オープン**します。  
  
24. 選択**ファイル**、**付けて** メニューから。 署名オプション ダイアログ ボックスでは、配置マニフェストに署名するよう求められますが表示されます。  
  
25. 場合は、ファイル システム上のファイルとして格納されている証明書がある場合を使用して、**証明書ファイルを使用してサインイン**オプション、およびファイル システムから、省略記号を使用して、証明書を選択します (**.**) ボタンをクリックします。 次に、証明書のパスワードを入力します。  
  
     - または -  
  
     場合は、証明書をコンピューターからアクセス可能な証明書ストアに保持すると、選択、**格納された証明書を使用してサインイン**オプション、および指定された一覧から証明書を選択します。  
  
26. をクリックして**OK**して配置マニフェストに署名します。 名前を付けて保存 ダイアログ ボックスが表示されます。  
  
27. **付けて** ダイアログ ボックスで、1 つのディレクトリをクリックし、実際のデプロイのルートへの移行**保存**します。  
  
28. 配置ディレクトリのすべてのファイルを展開先またはメディアにコピーします。 これにより、Web サイトまたは FTP サイト、ファイル共有、または CD-ROM 上のフォルダーか可能性があります。  
  
29. URL、UNC、またはアプリケーションをインストールするために必要な物理メディアをユーザーに提供します。 URL または UNC を指定すると、配置マニフェストの完全なパスをユーザーに与える必要があります。 AppToDeploy を配置する場合の例の http://webserver01/ AppToDeploy ディレクトリに完全な URL パスになります。 http://webserver01/AppToDeploy/AppToDeploy.application します。  
  
## <a name="next-steps"></a>次の手順  
 アプリケーションの新しいバージョンを展開する必要がある場合は、新しいバージョンにちなんだ名前の新しいディレクトリを作成、1.0.0.1—and が、新しいディレクトリに新しいアプリケーション ファイルをコピーするなど。 次に、作成し新しいアプリケーション マニフェストに署名し、更新、および配置マニフェストに署名するには、前の手順に従う必要があります。 両方、Mage.exe で同じより高いバージョンを指定するように注意`-New`と`–Update`呼び出し、として[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]のみ以降のバージョンが最上位の左端の整数値で更新します。 MageUI.exe を使用した場合ことができますを更新する、配置マニフェストを開き、選択、**アプリケーション参照**] タブをクリックすると、 **[マニフェストの**ボタンをクリックし、選択し、更新されました。アプリケーション マニフェスト。  
  
## <a name="see-also"></a>関連項目  
 [Mage.exe (マニフェストの生成および編集ツール)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (マニフェスト生成および編集ツールのグラフィカル クライアント)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)



