---
title: "ClickOnce のセキュリティと配置 | Microsoft Docs"
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
  - "ClickOnce 配置"
  - "配置 (アプリケーションを) [ClickOnce]"
  - "発行, ClickOnce"
  - "Windows アプリケーション, ClickOnce 配置"
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
caps.latest.revision: 32
caps.handback.revision: 32
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce のセキュリティと配置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] は、Windows ベースの自己更新型アプリケーションを作成できる配置テクノロジです。作成されたアプリケーションは、ユーザーとの対話を最小限に抑えてインストールおよび実行できます。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、プロジェクトが Visual Basic または Visual C\# で開発されている場合、ClickOnce テクノロジで配置されるアプリケーションの発行と更新が完全にサポートされます。  Visual C\+\+ アプリケーションの配置については、「[Visual C\+\+ アプリケーションの ClickOnce 配置](/visual-cpp/ide/clickonce-deployment-for-visual-cpp-applications)」を参照してください。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置を使用すると、配置に関する 3 つの主な問題を解決できます。  
  
-   **アプリケーションの更新における問題。**Microsoft Windows インストーラーによる配置では、ユーザーはアプリケーションが更新されるたびに更新プログラムの msp ファイルをインストールして、インストール済みの製品に適用できます。[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] による配置では、更新を自動的に提供できます。  アプリケーションの変更された部分だけがダウンロードされ、次に、更新されたアプリケーション全体が新しい side\-by\-side フォルダーから再インストールされます。  
  
-   **ユーザーのコンピューターへの影響。**Windows インストーラーの配置では、多くの場合、アプリケーションはバージョン管理の競合が発生する可能性を伴う共有コンポーネントに依存しています。[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の配置では、各アプリケーションは独立しているため、他のアプリケーションに干渉することはありません。  
  
-   **セキュリティ アクセス許可。**Windows インストーラーの配置には管理者権限が必要で、一部のユーザーだけがインストールを許可されます。[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の配置では管理者権限を持たないユーザーがアプリケーションをインストールでき、アプリケーションに必要なコード アクセス セキュリティのアクセス許可だけが付与されます。  
  
 これまで、これらの問題が原因で、開発者はインストールの容易さと引き換えに豊富なユーザー インターフェイスを犠牲にして、Windows ベースのアプリケーションではなく Web アプリケーションを作成することもありました。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] を使用して配置されたアプリケーションでは、両方のテクノロジの長所を活かすことができます。  
  
## ClickOnce アプリケーションとは  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションとは、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] テクノロジを使用して発行された Windows Presentation Foundation アプリケーション \(.xbap\)、Windows フォーム アプリケーション \(.exe\)、コンソール アプリケーション \(.exe\)、または Office ソリューション \(.dll\) のことです。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、Web ページ、ネットワーク ファイル共有、または CD\-ROM などのメディアを使用する 3 とおりの方法で発行できます。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、エンド ユーザーのコンピューターにインストールし、コンピューターがオフラインのときにもローカルで実行できます。または、エンド ユーザーのコンピューターに永続的にインストールせずに、オンライン専用モードで実行することもできます。  詳細については、「[ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)」を参照してください。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、自己更新型にできます。つまり、新しいバージョンがないかどうかをチェックし、新しいバージョンが利用できるようになると更新されたファイルを自動的に置き換えます。  開発者は、更新動作を指定できます。ネットワーク管理者は、更新を必須としてマークするなど、更新方法を制御できます。  また、エンド ユーザーまたは管理者が、更新を以前のバージョンにロールバックすることもできます。  詳細については、「[ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)」を参照してください。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは分離されているため、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションのインストールや実行によって、既存のアプリケーションが破損することはありません。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは単体で動作します。各 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、ユーザーごとにアプリケーション単位のキャッシュにインストールされ、実行されます。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、インターネットまたはイントラネットのセキュリティ ゾーンで実行されます。  必要であれば、アプリケーションは高いレベルのセキュリティ アクセス許可を要求できます。  詳細については、「[ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)」を参照してください。  
  
## ClickOnce のセキュリティのしくみ  
 コア [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] のセキュリティは、証明書、コード アクセス セキュリティ ポリシー、および ClickOnce 信頼プロンプトに基づいています。  
  
### 証明書  
 アプリケーションの発行元の信頼性を検証するために、Authenticode 証明書が使用されます。  ClickOnce では、アプリケーションの配置に Authenticode を使用して、有害なプログラムが定評のある信頼性の高い発行元からの正規のプログラムとして偽ることを防ぎます。  必要な場合は、証明書でアプリケーションと配置マニフェストに署名して、ファイルが改ざんされていないことを証明することもできます。  詳細については、「[ClickOnce と Authenticode](../deployment/clickonce-and-authenticode.md)」を参照してください。  証明書は、信頼された発行元の一覧をクライアント コンピューターに保存するように構成する場合にも使用できます。  信頼された発行元から発行されたアプリケーションは、ユーザーによる操作を必要とせずにインストールできます。  詳細については、「[信頼されたアプリケーションの配置の概要](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
### コード アクセス セキュリティ  
 コード アクセス セキュリティにより、保護されたリソースに対するコードのアクセスが制限されます。  ほとんどの場合は、インターネット ゾーンかローカル イントラネット ゾーンを選択することでアクセス許可を制限できます。  アプリケーションに適したゾーンを要求するには、**プロジェクト デザイナー**の **\[セキュリティ\]** ページを使用します。   また、エンド ユーザーの操作をエミュレートするために、制限されたアクセス許可を使用してアプリケーションをデバッグすることもできます。  詳細については、「[ClickOnce アプリケーションのコード アクセス セキュリティ](../deployment/code-access-security-for-clickonce-applications.md)」を参照してください。  
  
### ClickOnce 信頼プロンプト  
 アプリケーションからゾーンの設定よりも高いアクセス許可を要求する場合、信頼するかどうかをエンド ユーザーに確認するメッセージを表示できます。  エンド ユーザーは、Windows フォーム アプリケーション、Windows Presentation Foundation アプリケーション、コンソール アプリケーション、XAML ブラウザー アプリケーション、Office ソリューションなどの ClickOnce アプリケーションの実行を信頼するかどうかを決定できます。  詳細については、「[方法: ClickOnce 信頼プロンプトの動作を構成する](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)」を参照してください。  
  
## ClickOnce の配置のしくみ  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の配置のコア アーキテクチャは、アプリケーション マニフェストと配置マニフェストの 2 つの XML マニフェスト ファイルに基づいています。  これらのファイルは、ClickOnce アプリケーションのインストール元、更新方法、および更新時間を記述するために使用されます。  
  
### ClickOnce アプリケーションの発行  
 アプリケーション マニフェストでは、アプリケーション自体について記述します。  これには、アセンブリ、アプリケーションを構成する依存関係とファイル、必須アクセス許可、更新プログラムを入手できる場所などが含まれます。  アプリケーション開発者は、Visual Studio の発行ウィザード、または [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] のマニフェスト生成および編集ツール \(Mage.exe\) を使用して、アプリケーション マニフェストを作成します。  詳細については、「[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)」を参照してください。  
  
 配置マニフェストでは、アプリケーションの配置方法を記述します。  これには、アプリケーション マニフェストの場所や、クライアントで実行するアプリケーションのバージョンなどが含まれます。  
  
### ClickOnce アプリケーションの配置  
 配置マニフェストを作成したら、配置場所にコピーします。  この場所は、Web サーバー、ネットワーク ファイル共有、CD などのメディアのいずれでもかまいません。  アプリケーション マニフェストとすべてのアプリケーション ファイルも、配置マニフェストで指定した配置場所にコピーします。  これは、配置場所と同じ場所にすることも、別の場所にすることもできます。  Visual Studio の**発行ウィザード**を使用すると、コピー操作は自動的に実行されます。  
  
### ClickOnce アプリケーションのインストール  
 配置マニフェストが配置場所に配置されると、エンド ユーザーは Web ページ上またはフォルダー内の配置マニフェスト ファイルを表すアイコンをクリックすることで、アプリケーションをダウンロードし、インストールできます。  ほとんどの場合、エンド ユーザーには、インストールするかどうかを確認する簡単なダイアログ ボックスが表示され、その後にインストールが進行します。アプリケーションは、エンド ユーザーの介入をそれ以上必要とせずに起動されます。  昇格されたアクセス許可がアプリケーションに必要な場合や、信頼された証明書でアプリケーション署名されていない場合も、インストールを続行する前に、アクセス許可を付与するかどうかをユーザーに確認するダイアログ ボックスが表示されます。  ClickOnce のインストールはユーザー単位で行われますが、管理者特権を必要とする必須コンポーネントがある場合は、アクセス許可の昇格が必要になることがあります。  アクセス許可の昇格の詳細については、「[ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)」を参照してください。  
  
 証明書はコンピューター レベルまたはエンタープライズ レベルで信頼できるため、信頼された証明書で署名された ClickOnce アプリケーションはサイレント インストールできます。  信頼された証明書の詳細については、「[信頼されたアプリケーションの配置の概要](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
 アプリケーションは、ユーザーの **\[スタート\]** メニューと、**コントロール パネル**の **\[プログラムの追加と削除\]** グループに追加できます。  他の配置テクノロジとは異なり、**Program Files** フォルダーまたはレジストリには何も追加されず、インストールするための管理者権限は必要ありません。  
  
> [!NOTE]
>  **\[スタート\]** メニューと **\[プログラムの追加と削除\]** グループにアプリケーションが追加されないようにし、実質的に Web アプリケーションのように動作させることもできます。  詳細については、「[ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)」を参照してください。  
  
### ClickOnce アプリケーションの更新  
 アプリケーション開発者は、アプリケーションの更新バージョンの作成時に、新しいアプリケーション マニフェストを生成し、ファイルを配置場所 \(通常は元のアプリケーション配置フォルダーの兄弟フォルダー\) にコピーします。  管理者は、配置マニフェストを更新して、アプリケーションの新しいバージョンの場所を参照します。  
  
> [!NOTE]
>  これらの手順を実行するには、Visual Studio の**発行ウィザード**を使用できます。  
  
 配置マニフェストには、配置場所だけでなく、アプリケーションが最新バージョンをチェックする更新プログラムの場所 \(Web ページまたはネットワーク ファイル共有\) も含めることができます。  アプリケーションが更新プログラムをチェックする時期と頻度を指定するには、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の **"発行"** プロパティを使用します。  更新動作は、配置マニフェストで指定できます。また、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API によって、アプリケーションのユーザー インターフェイスにユーザーの選択肢として表示することもできます。  **"発行"** プロパティを使用して、更新を必須にしたり、旧バージョンにロールバックしたりすることもできます。  詳細については、「[ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)」を参照してください。  
  
### サードパーティ製インストーラー  
 ClickOnce インストーラーは、サードパーティ製コンポーネントと自社製アプリケーションを一緒にインストールするようにカスタマイズできます。  この場合、再頒布可能パッケージ \(.exe または .msi ファイル\) を用意すると共に、言語に依存しない製品マニフェストと言語固有のパッケージ マニフェストを含むパッケージを記述する必要があります。  詳細については、「[ブートストラップ パッケージの作成](../deployment/creating-bootstrapper-packages.md)」を参照してください。  
  
## ClickOnce のツール  
 次の表は、アプリケーション マニフェストおよび配置マニフェストの生成、編集、署名、および再署名に使用できるツールの一覧です。  
  
|ツール|Description|  
|---------|-----------------|  
|[\[セキュリティ\] ページ \(プロジェクト デザイナー\)](../Topic/Security%20Page,%20Project%20Designer.md)|アプリケーション マニフェストと配置マニフェストに署名します。|  
|[\[発行\] ページ \(プロジェクト デザイナー\)](../Topic/Publish%20Page,%20Project%20Designer.md)|Visual Basic アプリケーションおよび Visual C\# アプリケーションのアプリケーション マニフェストと配置マニフェストを生成および編集します。|  
|[Mage.exe \(マニフェストの生成および編集ツール\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)|Visual Basic アプリケーション、Visual C\# アプリケーション、および Visual C\+\+ アプリケーションのアプリケーション マニフェストと配置マニフェストを生成します。<br /><br /> アプリケーション マニフェストと配置マニフェストに署名および再署名します。<br /><br /> バッチ スクリプトおよびコマンド プロンプトから実行できます。|  
|[MageUI.exe \(マニフェスト生成および編集ツールのグラフィカル クライアント\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)|アプリケーション マニフェストと配置マニフェストを生成および編集します。<br /><br /> アプリケーション マニフェストと配置マニフェストに署名および再署名します。|  
|[GenerateApplicationManifest Task](../msbuild/generateapplicationmanifest-task.md)|アプリケーション マニフェストを生成します。<br /><br /> MSBuild から実行できます。  詳細については、「[MSBuild Reference](../msbuild/msbuild-reference.md)」を参照してください。|  
|[GenerateDeploymentManifest Task](../msbuild/generatedeploymentmanifest-task.md)|配置マニフェストを生成します。<br /><br /> MSBuild から実行できます。  詳細については、「[MSBuild Reference](../msbuild/msbuild-reference.md)」を参照してください。|  
|[SignFile Task](../msbuild/signfile-task.md)|アプリケーション マニフェストと配置マニフェストに署名します。<br /><br /> MSBuild から実行できます。  詳細については、「[MSBuild Reference](../msbuild/msbuild-reference.md)」を参照してください。|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|アプリケーション マニフェストと配置マニフェストを生成する独自のアプリケーションを開発します。|  
  
 次の表は、各ブラウザーで ClickOnce アプリケーションをサポートするために必要な .NET Framework のバージョンの一覧です。  
  
|ブラウザー|.NET Framework のバージョン|  
|-----------|---------------------------|  
|Internet Explorer|2.0、3.0、3.5、3.5 SP1、4|  
|Firefox|2.0 SP1、3.5 SP1、4|  
  
## 参照  
 [Windows Vista の ClickOnce 配置](../deployment/clickonce-deployment-on-windows-vista.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce での COM コンポーネントの配置](../deployment/deploying-com-components-with-clickonce.md)   
 [ClickOnce アプリケーションのコマンド ラインからのビルド](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [System.Deployment.Application を使用する ClickOnce アプリケーションのデバッグ](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)