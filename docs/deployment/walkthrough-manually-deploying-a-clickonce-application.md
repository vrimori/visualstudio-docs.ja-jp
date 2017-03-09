---
title: "チュートリアル : ClickOnce アプリケーションを手動で配置する | Microsoft Docs"
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
  - "ClickOnce 配置, 手動"
  - "ClickOnce 配置, SDK ツール"
  - "配置 (アプリケーションを) [ClickOnce], ClickOnce の手動配置"
  - "Mage.exe, ClickOnce の手動配置"
  - "MageUI.exe, ClickOnce の手動配置"
  - "マニフェスト [ClickOnce]"
  - "ClickOnce の手動配置"
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: 49
caps.handback.revision: 47
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# チュートリアル : ClickOnce アプリケーションを手動で配置する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio を使用して [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを配置できない場合、または信頼されたアプリケーションの配置のような高度な配置機能を使用する必要がある場合は、Mage.exe というコマンド ライン ツールを使用して [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] マニフェストを作成します。  このチュートリアルでは、マニフェストの生成および編集ツールのコマンド ライン バージョン \(Mage.exe\) または GUI バージョン \(MageUI.exe\) を使用して [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置を作成する方法について説明します。  
  
## 必須コンポーネント  
 このチュートリアルには、必須コンポーネントと、配置をビルドする前に選択する必要のあるオプションがいくつかあります。  
  
-   Mage.exe と MageUI.exe をインストールします。  
  
     Mage.exe と MageUI.exe は [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] に含まれています。  インストール済みの [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] または Visual Studio に同梱されているバージョンの [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] が必要です。  詳細については、MSDN の「[Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044)」を参照してください。  
  
-   配置するアプリケーションを用意します。  
  
     このチュートリアルは、配置する準備が整っている Windows アプリケーションがあることを前提としています。  このアプリケーションを、AppToDeploy と呼びます。  
  
-   配置の配布方法を決定します。  
  
     配布オプションには、Web、ファイル共有、または CD があります。  詳細については、「[ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)」を参照してください。  
  
-   アプリケーションがより高いレベルの信頼を必要とするかどうかを決定します。  
  
     アプリケーションが完全な信頼 \(ユーザーのシステムへのフル アクセスなど\) を必要とする場合は、Mage.exe の `-TrustLevel` オプションを使用して完全信頼を設定できます。  アプリケーションにカスタム化したアクセス許可セットを定義する場合には、他のマニフェストからインターネット セクションまたはイントラネット セクションをコピーし、必要に合わせて変更し、テキスト エディターまたは MageUI.exe を使用してアプリケーション マニフェストに追加します。  詳細については、「[信頼されたアプリケーションの配置の概要](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
-   Authenticode 証明書を取得します。  
  
     Authenticode 証明書を使用して配置に署名する必要があります。  Visual Studio、MageUI.exe、または MakeCert.exe および Pvk2Pfx.exe の各ツールを使用してテスト証明書を生成するか、証明機関 \(CA: Certificate Authority\) から証明書を取得することができます。  信頼されたアプリケーションの配置を使用する場合には、すべてのクライアント コンピューターに証明書を 1 回だけインストールする必要もあります。  詳細については、「[信頼されたアプリケーションの配置の概要](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
-   アプリケーションに UAC 情報を含むマニフェストがないことを確認します。  
  
     アプリケーションに、`<dependentAssembly>` 要素などのユーザー アカウント制御 \(UAC: User Account Control\) 情報を含むマニフェストがあるかどうかを確認する必要があります。  アプリケーション マニフェストを調べるには、Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) ユーティリティを使用できます。  
  
     アプリケーションに UAC 情報を含むマニフェストがある場合は、UAC 情報が含まれないようにアプリケーションをビルドし直す必要があります。  Visual Studio の C\# プロジェクトの場合は、プロジェクトのプロパティを開いて \[アプリケーション\] タブをクリックします。  **\[マニフェスト\]** ボックスの一覧の **\[マニフェストなしでアプリケーションを作成します\]** をクリックします。  Visual Studio の Visual Basic プロジェクトの場合は、プロジェクトのプロパティを開いて \[アプリケーション\] タブをクリックし、**\[UAC 設定の表示\]** をクリックします。  開いているマニフェスト ファイルで、1 つの `<asmv1:assembly>` 要素内のすべての要素を削除します。  
  
-   アプリケーションがクライアント コンピューターで必須コンポーネントを必要とするかどうかを決定します。  
  
     Visual Studio から配置する [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションでは、必須コンポーネントをインストールするブートストラップ \(setup.exe\) を配置に含めることができます。  このチュートリアルでは、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置に必要なマニフェストを 2 つ作成します。  必須コンポーネント ブートストラップを作成するには、[GenerateBootstrapper Task](../msbuild/generatebootstrapper-task.md) を使用できます。  
  
### コマンド ライン ツール Mage.exe でアプリケーションを配置するには  
  
1.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置ファイルを格納するディレクトリを作成します。  
  
2.  作成した配置ディレクトリに、バージョン サブディレクトリを作成します。  初めてアプリケーションを配置する場合は、バージョン サブディレクトリに 1.0.0.0 という名前を付けます。  
  
    > [!NOTE]
    >  配置のバージョンは、アプリケーションのバージョンとは異なる場合もあります。  
  
3.  実行可能ファイル、アセンブリ、リソース ファイル、データ ファイルなど、すべてのアプリケーション ファイルをバージョン サブディレクトリにコピーします。  必要に応じて、追加ファイルを格納する追加サブディレクトリを作成することもできます。  
  
4.  [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] または Visual Studio コマンド プロンプトを開いて、バージョン サブディレクトリに移動します。  
  
5.  Mage.exe を呼び出して、アプリケーション マニフェストを作成します。  次のステートメントは、Intel x86 プロセッサで実行されるようにコンパイルされたコードのアプリケーション マニフェストを作成します。  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  必ずドット \(.\) を `-FromDirectory` オプションの後に入力してください \(現在のディレクトリを示します\)。  ドットを入力しない場合は、アプリケーション ファイルのパスを指定する必要があります。  
  
6.  Authenticode 証明書を使用してアプリケーション マニフェストに署名します。  *mycert.pfx* は証明書ファイルのパスに置き換えます。  *passwd* は証明書ファイルのパスワードに置き換えます。  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
7.  配置ディレクトリのルートに移動します。  
  
8.  Mage.exe を呼び出して、配置マニフェストを作成します。  既定では、Mage.exe は [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置を、オンラインでもオフラインでも実行できるように、インストール アプリケーションとして指定します。  ユーザーがオンラインの場合にだけアプリケーションを使用できるようにする場合は、`-Install` オプションを使用し、値を `false` に設定します。  既定値を使用して、Web サイトまたはファイル共有からユーザーがアプリケーションをインストールするようにする場合は、`-ProviderUrl` オプションの値が Web サーバー上または共有サイト上のアプリケーション マニフェストの場所を指していることを確認してください。  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Authenticode 証明書を使用して配置マニフェストに署名します。  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
10. 配置ディレクトリ内のすべてのファイルを配置先またはメディアにコピーします。  コピー先は、Web サイトのフォルダー、FTP サイトのフォルダー、ファイル共有、または CD\-ROM のいずれかです。  
  
11. ユーザーがアプリケーションをインストールするために必要な URL、UNC、または物理メディアを指定します。  URL または UNC を指定する場合は、配置マニフェストの完全パスをユーザーに示す必要があります。  たとえば、AppToDeploy を http:\/\/webserver01\/ の AppToDeploy ディレクトリに配置する場合、URL の完全パスは http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application です。  
  
### MageUI.exe グラフィカル ツールでアプリケーションを配置するには  
  
1.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置ファイルを格納するディレクトリを作成します。  
  
2.  作成した配置ディレクトリに、バージョン サブディレクトリを作成します。  初めてアプリケーションを配置する場合は、バージョン サブディレクトリに 1.0.0.0 という名前を付けます。  
  
    > [!NOTE]
    >  配置のバージョンは、アプリケーションのバージョンとは異なる場合もあります。  
  
3.  実行可能ファイル、アセンブリ、リソース ファイル、データ ファイルなど、すべてのアプリケーション ファイルをバージョン サブディレクトリにコピーします。  必要に応じて、追加ファイルを格納する追加サブディレクトリを作成することもできます。  
  
4.  MageUI.exe グラフィカル ツールを起動します。  
  
    ```  
    MageUI.exe  
    ```  
  
5.  **\[File\]** メニューの **\[New\]** をポイントし、**\[Application Manifest\]** をクリックして、アプリケーション マニフェストを新規作成します。  
  
6.  既定で表示される **\[Name\]** ページで、この配置の名前およびバージョン番号を入力します。  また、アプリケーションがビルドされる対象の**プロセッサ**も指定します \(x86 など\)。  
  
7.  **\[Files\]** タブをクリックし、**\[Application Directory\]** ボックスの横の省略記号 \(**\[...\]**\) ボタンをクリックします。  \[Browse For Folder\] ダイアログ ボックスが表示されます。  
  
8.  アプリケーション ファイルが格納されているバージョン サブディレクトリを選択し、**\[OK\]** をクリックします。  
  
9. インターネット インフォメーション サービス \(IIS: Internet Information Services\) から配置する場合は、**\[When populating add the .deploy extension to any file that does not have it\]** チェック ボックスをオンにします。  
  
10. **\[Populate\]** をクリックし、アプリケーション ファイルすべてをファイル リストに追加します。  アプリケーションに実行可能ファイルが複数含まれている場合は、**\[File Type\]** ボックスの **\[Entry Point\]** をオンにして、この配置のメイン実行可能ファイルをスタートアップ アプリケーションとして指定します。  アプリケーションの実行可能ファイルが 1 つだけの場合は、そのファイルが MageUI.exe によってメイン実行可能ファイルとしてマークされます。  
  
11. **\[Permissions Required\]** タブをクリックし、アプリケーションが要求する信頼のレベルを選択します。  既定値は **\[FullTrust\]** です。この設定は、ほとんどのアプリケーションに適しています。  
  
12. **\[File\]** メニューの **\[Save As\]** をクリックします。  \[Signing Options\] ダイアログ ボックスが表示され、アプリケーション マニフェストに署名するように求めるメッセージが表示されます。  
  
13. 証明書をファイルとしてファイル システムに保存してある場合には、**\[Sign with certificate file\]** オプションの省略記号 \(**\[...\]**\) ボタンをクリックして、ファイル システム上の証明書を選択します。  次に、証明書パスワードを入力します。  
  
     または  
  
     使用しているコンピューターからアクセスできる証明書ストアに証明書が保存されている場合には、**\[Sign with stored certificate\]** オプションをクリックし、表示された一覧から証明書を選択します。  
  
14. **\[OK\]** をクリックしてアプリケーション マニフェストに署名します。  \[名前を付けて保存\] ダイアログ ボックスが表示されます。  
  
15. \[Save As\] ダイアログ ボックスで、バージョン ディレクトリを指定して **\[Save\]** をクリックします。  
  
16. **\[File\]** メニューの **\[New\]** をポイントし、**\[Deployment Manifest\]** をクリックして、配置マニフェストを作成します。  
  
17. **\[Name\]** ページで、この配置の名前とバージョン番号 \(この例の場合は、1.0.0.0\) を指定します。  また、アプリケーションがビルドされる対象の**プロセッサ**も指定します \(x86 など\)。  
  
18. **\[Description\]** タブをクリックし、**\[Publisher\]** ボックスおよび **\[Product\]** ボックスで値を指定します。  **\[Product\]** はアプリケーションに付けられる名前で、オフラインで使用するためにアプリケーションをクライアント コンピューターにインストールしたときに Windows の \[スタート\] メニューに表示されます。  
  
19. **\[Deployment Options\]** タブをクリックし、**\[Start Location\]** ボックスで、Web サーバー上または共有サイト上のアプリケーション マニフェストの場所を指定します   \(\\\\myServer\\myShare\\AppToDeploy.application など\)。  
  
20. 前の手順で .deploy 拡張子を追加した場合は、ここで **\[Use .deploy file name extension\]** もオンにします。  
  
21. **\[Update Options\]** タブをクリックし、このアプリケーションを更新する頻度を指定します。  アプリケーションが <xref:System.Deployment.Application.UpdateCheckInfo> を使用して自動的に更新プログラムをチェックする場合は、**\[This application should check for updates\]** チェック ボックスをオフにします。  
  
22. **\[Application Reference\]** タブをクリックし、**\[Select Manifest\]** ボタンをクリックします。  \[Open\] ダイアログ ボックスが表示されます。  
  
23. 作成したアプリケーション マニフェストを選択し、**\[Open\]** をクリックします。  
  
24. **\[File\]** メニューの **\[Save As\]** をクリックします。  \[Signing Options\] ダイアログ ボックスが表示され、配置マニフェストに署名するように求めるメッセージが表示されます。  
  
25. 証明書をファイルとしてファイル システムに保存してある場合には、**\[Sign with certificate file\]** オプションの省略記号 \(**\[...\]**\) ボタンをクリックして、ファイル システム上の証明書を選択します。  次に、証明書パスワードを入力します。  
  
     または  
  
     使用しているコンピューターからアクセスできる証明書ストアに証明書が保存されている場合には、**\[Sign with stored certificate\]** オプションをクリックし、表示された一覧から証明書を選択します。  
  
26. **\[OK\]** をクリックして配置マニフェストに署名します。  \[名前を付けて保存\] ダイアログ ボックスが表示されます。  
  
27. **\[Save As\]** ダイアログ ボックスで、1 つ上のディレクトリ \(配置のルート\) に移動して、**\[Save\]** をクリックします。  
  
28. 配置ディレクトリ内のすべてのファイルを配置先またはメディアにコピーします。  コピー先は、Web サイトのフォルダー、FTP サイトのフォルダー、ファイル共有、または CD\-ROM のいずれかです。  
  
29. ユーザーがアプリケーションをインストールするために必要な URL、UNC、または物理メディアを指定します。  URL または UNC を指定する場合は、配置マニフェストの完全パスをユーザーに示す必要があります。  たとえば、AppToDeploy を http:\/\/webserver01\/ の AppToDeploy ディレクトリに配置する場合、URL の完全パスは http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application です。  
  
## 次の手順  
 アプリケーションの新しいバージョンを配置するときは、新しいディレクトリを作成し、それに新しいバージョン番号 \(たとえば 1.0.0.1\) を使用した名前を付け、その新しいディレクトリに新しいアプリケーション ファイルをコピーします。  次に、前の手順に従って新しいアプリケーション マニフェストを作成して署名し、配置マニフェストを更新して署名する必要があります。  Mage.exe の `-New` と `–Update` の両方の呼び出しで、同じ上位のバージョンを指定するように注意してください。[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] では左端の整数が最も重要であると見なされ、上位のバージョンのみが更新されます。  MageUI.exe を使用した場合は、配置マニフェストを開いて **\[Application Reference\]** タブをクリックし、**\[Select Manifest\]** ボタンをクリックして更新したアプリケーション マニフェストを選択すると、配置マニフェストを更新できます。  
  
## 参照  
 [Mage.exe \(マニフェストの生成および編集ツール\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(マニフェスト生成および編集ツールのグラフィカル クライアント\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)