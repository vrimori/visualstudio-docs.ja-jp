---
title: 'チュートリアル: ClickOnce アプリケーションを手動で展開する |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 652c7eee2e4b3830966882afd4a9b9b31c8aceb3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923271"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application"></a>チュートリアル: ClickOnce アプリケーションを手動で展開します。
Visual Studio を使用してデプロイすることはできません場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション、または高度な展開の機能を使用する必要があります使用する必要があります信頼されたアプリケーションの配置など、 *Mage.exe* 、を作成するコマンドラインツール。[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]マニフェストします。 このチュートリアルを作成する方法について説明、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]コマンドラインのいずれかのバージョンを使用した展開 (*Mage.exe*) またはグラフィカル バージョン (*MageUI.exe*) のマニフェストの生成とツールを編集します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルでは、いくつかの前提条件とデプロイを構築する前に選択する必要があるオプションはされています。  
  
- インストール*Mage.exe*と*MageUI.exe*します。  
  
   *Mage.exe*と*MageUI.exe*の一部である、[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]します。 必要か、[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]インストールされているかのバージョン、 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] Visual Studio に含まれています。 詳細については、次を参照してください。 [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) msdn です。  
  
- 展開するアプリケーションを提供します。  
  
   このチュートリアルでは、Windows アプリケーションをデプロイする準備が整いましたがあることを前提としています。 このアプリケーションは、AppToDeploy として参照されます。  
  
- 展開の分散方法を決定します。  
  
   ディストリビューション オプションは次のとおりです。Web、ファイル共有、または CD。 詳細については、「 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)」を参照してください。  
  
- アプリケーションに管理者特権でのレベルの信頼が必要かどうかを決定します。  
  
   アプリケーションでは、完全信頼が必要な場合: たとえば、ユーザーのシステムへのアクセスを完全: を使用することができます、`-TrustLevel`のオプション*Mage.exe*これを設定します。 カスタム アクセス許可は、アプリケーションの設定を定義する場合は、コピー、インターネットまたはイントラネット アクセス許可のセクション別のマニフェストからに、ニーズに合わせて変更してテキスト エディターを使用してアプリケーション マニフェストに追加または*MageUI.exe*します。 詳細については、「[信頼されたアプリケーションの配置の概要](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
- Authenticode 証明書を取得します。  
  
   Authenticode 証明書を使用してデプロイを署名する必要があります。 テスト証明書を生成するには、Visual Studio を使用して*MageUI.exe*、または*MakeCert.exe*と*Pvk2Pfx.exe*ツール、または、証明書から証明書を取得できます証明機関 (CA)。 信頼されたアプリケーションの配置を使用するように選択した場合はすべてのクライアント コンピューターに証明書のインストールを 1 回も行う必要があります。 詳細については、「 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
  > [!NOTE]
  >  CNG 証明書が証明機関から入手できます。 使用してデプロイを登録することもできます。  
  
- アプリケーションに UAC 情報を含むマニフェストがないことを確認します。  
  
   アプリケーションがユーザー アカウント制御 (UAC) の情報を含むマニフェストをなど、含まれるかどうかを確認する必要がある、`<dependentAssembly>`要素。 アプリケーション マニフェストを確認するには、Windows Sysinternals を使用できる[Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035)ユーティリティ。  
  
   アプリケーションに UAC の詳細を含むマニフェストが含まれている場合は、UAC 情報を使用しないで再構築する必要があります。 Visual Studio で c# プロジェクトのプロジェクトのプロパティを開き、[アプリケーション] タブを選択します。**マニフェスト**ドロップダウン リストで、**マニフェストを含まないアプリケーションを作成する**します。 Visual Studio で Visual Basic プロジェクトの場合、プロジェクトのプロパティを開き、アプリケーション タブを選択および をクリックして**UAC 設定の表示**します。 マニフェスト ファイルを開いたときに、1 つ内のすべての要素を削除`<asmv1:assembly>`要素。  
  
- アプリケーションがクライアント コンピューターの前提条件が必要かどうかを決定します。  
  
   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Visual Studio からデプロイされたアプリケーションは、前提条件のインストールのブートス トラップを含めることができます (*setup.exe*)、展開します。 このチュートリアルで作成に必要な 2 つのマニフェストを[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開します。 前提条件のブートス トラップを使用して作成することができます、 [GenerateBootstrapper タスク](../msbuild/generatebootstrapper-task.md)します。  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Mage.exe コマンド ライン ツールを使用してアプリケーションをデプロイするには  
  
1. 格納するディレクトリを作成、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開ファイル。  
  
2. 作成した展開ディレクトリでは、バージョン サブディレクトリを作成します。 初めてアプリケーションを展開する場合は、名前、バージョン サブディレクトリ**1.0.0.0**します。  
  
   > [!NOTE]
   >  配置のバージョンをアプリケーションのバージョンとは異なることはできます。  
  
3. 実行可能ファイル、アセンブリ、リソース、およびデータ ファイルを含む、バージョン サブディレクトリには、すべてのアプリケーション ファイルをコピーします。 必要に応じて、追加のファイルが含まれている追加のサブディレクトリを作成できます。  
  
4. 開く、[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]または Visual Studio コマンド プロンプトし、バージョンのサブディレクトリに変更します。  
  
5. アプリケーション マニフェストへの呼び出しを作成*Mage.exe*します。 次のステートメントは、Intel x86 プロセッサで実行するコンパイルされたコードに対するアプリケーション マニフェストを作成します。  
  
   ```cmd
   mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
   ```  
  
   > [!NOTE]
   >  後にドット (.) を含めるようにしてください、`-FromDirectory`オプションは、現在のディレクトリを示します。 ドットを含めない場合、アプリケーション ファイル パスを指定する必要があります。  
  
6. Authenticode 証明書をアプリケーション マニフェストに署名します。 置換*mycert.pfx*証明書ファイルへのパス。 置換*passwd*証明書ファイルのパスワードに置き換えます。  
  
   ```cmd
   mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
   ```  
  
   Visual Studio と Windows SDK に配布される .NET Framework 4.6.2 SDK 以降*mage.exe* CNG を使用すると、Authenticode 証明書でマニフェストに署名します。 Authenticode 証明書と同じコマンド ライン パラメーターを使用します。
    
7. 配置ディレクトリのルートに変更します。  
  
8. 呼び出しで配置マニフェストを生成*Mage.exe*します。 既定では、 *Mage.exe*マークは、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]その it を両方オンラインで実行できるように、オフライン インストールされているアプリケーションとして展開します。 アプリケーションで使用できるように、ユーザーがオンラインの場合にのみ使用して、`-Install`の値を持つオプション`false`します。 場合は、既定値を使用し、ユーザーがアプリケーションを Web サイトまたはファイル共有からインストールを以下のことを確認の値、 `-ProviderUrl` Web サーバーまたは共有でマニフェストのオプションのアプリケーションの場所を指しています。  
  
   ```cmd  
   mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
   ```  
  
9. Authenticode または CNG 証明書で配置マニフェストに署名します。  
  
    ```cmd  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
10. 配置ディレクトリのすべてのファイルを展開先またはメディアにコピーします。 これにより、Web サイトまたは FTP サイト、ファイル共有、または CD-ROM 上のフォルダーか可能性があります。  
  
11. URL、UNC、またはアプリケーションをインストールするために必要な物理メディアをユーザーに提供します。 URL または UNC を指定する場合は、配置マニフェストに、ユーザーの完全なパスを示す必要があります。 AppToDeploy を配置する場合の例の http://webserver01/AppToDeploy ディレクトリに完全な URL パスになります。 http://webserver01/AppToDeploy/AppToDeploy.applicationします。  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>MageUI.exe のグラフィカル ツールを使用してアプリケーションをデプロイするには  
  
1. 格納するディレクトリを作成、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開ファイル。  
  
2. 作成した展開ディレクトリでは、バージョン サブディレクトリを作成します。 初めてアプリケーションを展開する場合は、名前、バージョン サブディレクトリ**1.0.0.0**します。  
  
   > [!NOTE]
   >  配置のバージョンは、アプリケーションのバージョンとは異なる可能性があります。  
  
3. 実行可能ファイル、アセンブリ、リソース、およびデータ ファイルを含む、バージョン サブディレクトリには、すべてのアプリケーション ファイルをコピーします。 必要に応じて、追加のファイルが含まれている追加のサブディレクトリを作成できます。  
  
4. 開始、 *MageUI.exe*のグラフィカル ツール。  
  
   ```cmd  
   MageUI.exe  
   ```  
  
5. 選択して新しいアプリケーション マニフェストを作成する**ファイル**、**新規**、 **Application Manifest**  メニューから。  
  
6. 既定の**名前** タブで、このデプロイの名前とバージョン番号を入力します。 指定することも、**プロセッサ**x86 など、アプリケーションが組み込まれています。  
  
7. 選択、**ファイル** タブで、省略記号をクリックし、(**.**) ボタンの横に、**アプリケーション ディレクトリ**テキスト ボックス。 A**フォルダーの参照** ダイアログ ボックスが表示されます。  
  
8. アプリケーション ファイルを格納しているバージョンのサブディレクトリを選択し、クリックして**OK**します。  
  
9. インターネット インフォメーション サービス (IIS) を展開する場合は、選択、**を持たない任意のファイルを .deploy 拡張子に追加の設定と**チェック ボックスをオンします。  
  
10. をクリックして、 **Populate**ファイルの一覧にすべてのアプリケーション ファイルを追加するボタンをクリックします。 アプリケーションには、複数の実行可能ファイルが含まれている場合は、スタートアップ アプリケーションとしては、この展開のメイン実行可能ファイルをマークをオンに**エントリ ポイント**から、**ファイルの種類**ドロップダウン リスト。 (アプリケーションには、1 つだけの実行可能ファイルが含まれている場合*MageUI.exe*を対象として設定されます)。  
  
11. 選択、**必要なアクセス許可**タブし、アプリケーションをアサートする必要があることの信頼のレベルを選択します。 既定値は**FullTrust**、ほとんどのアプリケーションに適したされます。  
  
12. 選択**ファイル**、**付けて** メニューから。 署名オプション ダイアログ ボックスでは、アプリケーション マニフェストに署名するよう求められますが表示されます。  
  
13. 場合は、ファイル システム上のファイルとして格納されている証明書がある場合を使用して、**証明書ファイルを使用してサインイン**オプション、およびファイル システムから、省略記号を使用して、証明書を選択します (**.**) ボタンをクリックします。 次に、証明書のパスワードを入力します。  
  
     - または -  
  
     場合は、証明書をコンピューターからアクセス可能な証明書ストアに保持すると、選択、**格納された証明書を使用してサインイン**オプション、および指定された一覧から証明書を選択します。  
  
14. をクリックして**OK**アプリケーション マニフェストに署名します。 **付けて** ダイアログ ボックスが表示されます。  
  
15. **名前を付けて保存**ダイアログ ボックスは、バージョンのディレクトリを指定し、クリックして**保存**します。  
  
16. 選択**ファイル**、**新規**、**配置マニフェスト**メニューの配置マニフェストを作成します。  
  
17. **名前**タブで、この展開の名前とバージョン番号を指定 (**1.0.0.0**この例では)。 指定することも、**プロセッサ**x86 など、アプリケーションが組み込まれています。  
  
18. 選択、**説明**タブをクリックし、値を指定**パブリッシャー**と**製品**します。 (**製品**Windows [スタート] メニュー上のアプリケーションをオフラインで使用するクライアント コンピューターで、アプリケーションをインストールするときに指定された名前を指定します)。  
  
19. 選択、**展開オプション** タブで、および、**開始場所**テキスト ボックスで、Web サーバーまたは共有上のアプリケーション マニフェストの場所を指定します。 たとえば、  *\\\myServer\myShare\AppToDeploy.application*します。  
  
20. 追加した場合、 *.deploy*前の手順で拡張機能の選択も **.deploy ファイル名拡張子を使用して、** ここでします。  
  
21. 選択、**更新オプション**タブをクリックし、このアプリケーションを更新を希望する頻度を指定します。 アプリケーションで使用する場合<xref:System.Deployment.Application.UpdateCheckInfo>をチェックする更新プログラム自体、オフ、**アプリケーションの更新プログラムを確認する必要があります**チェック ボックスをオンします。  
  
22. 選択、**アプリケーション参照**] タブをクリックして、 **[マニフェストの**ボタンをクリックします。 開く ダイアログ ボックスが表示されます。  
  
23. 先ほど作成したアプリケーション マニフェストを選択し、クリックして**オープン**します。  
  
24. 選択**ファイル**、**付けて** メニューから。 A**署名オプション**配置マニフェストに署名するように求めるダイアログ ボックスが表示されます。  
  
25. 場合は、ファイル システム上のファイルとして格納されている証明書がある場合を使用して、**証明書ファイルを使用してサインイン**オプション、およびファイル システムから、省略記号を使用して、証明書を選択します (**.**) ボタンをクリックします。 次に、証明書のパスワードを入力します。  
  
     - または -  
  
     場合は、証明書をコンピューターからアクセス可能な証明書ストアに保持すると、選択、**格納された証明書を使用してサインイン**オプション、および指定された一覧から証明書を選択します。  
  
26. をクリックして**OK**して配置マニフェストに署名します。 **付けて** ダイアログ ボックスが表示されます。  
  
27. **付けて** ダイアログ ボックスで、1 つのディレクトリをクリックし、実際のデプロイのルートへの移行**保存**します。  
  
28. 配置ディレクトリのすべてのファイルを展開先またはメディアにコピーします。 これにより、Web サイトまたは FTP サイト、ファイル共有、または CD-ROM 上のフォルダーか可能性があります。  
  
29. URL、UNC、またはアプリケーションをインストールするために必要な物理メディアをユーザーに提供します。 URL または UNC を指定すると、配置マニフェストの完全なパスをユーザーに与える必要があります。 AppToDeploy を配置する場合の例の http://webserver01/AppToDeploy ディレクトリに完全な URL パスになります。 http://webserver01/AppToDeploy/AppToDeploy.applicationします。  
  
## <a name="next-steps"></a>次の手順  
 アプリケーションの新しいバージョンを展開する必要がある場合は、新しいバージョンにちなんだ名前の新しいディレクトリを作成、1.0.0.1—and が、新しいディレクトリに新しいアプリケーション ファイルをコピーするなど。 次に、作成し新しいアプリケーション マニフェストに署名し、更新、および配置マニフェストに署名するには、前の手順に従う必要があります。 両方で同じより高いバージョンを指定するように注意してください、 *Mage.exe* `-New`と`-Update`呼び出しとして[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]のみ以降のバージョンが最上位の左端の整数値で更新します。 使用した場合*MageUI.exe*、選択を開き、配置マニフェストを更新することができます、**アプリケーション参照**] タブをクリックすると、 **[マニフェストの**ボタン、および更新されたアプリケーション マニフェストを選択します。  
  
## <a name="see-also"></a>関連項目  
 [Mage.exe (マニフェストの生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (マニフェスト生成および編集ツールのグラフィカル クライアント)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)