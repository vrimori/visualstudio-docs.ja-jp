---
title: ClickOnce のセキュリティと配置 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ec2e74623c39640517ae73786d7865143bf1505
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce のセキュリティと配置
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 展開テクノロジをインストールして最小限のユーザー操作で実行できる自己更新の Windows ベースのアプリケーションを作成することができます。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 発行および Visual Basic および Visual c# でプロジェクトを開発している場合は、ClickOnce テクノロジで配置されたアプリケーションを更新するためには、完全にサポートを提供します。 Visual C アプリケーションの展開方法の詳細については、次を参照してください。 [Visual c アプリケーションの ClickOnce 配置](/cpp/ide/clickonce-deployment-for-visual-cpp-applications)です。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 展開は、展開における 3 つの主な問題を克服します。  
  
-   **アプリケーションの更新中における問題。** Microsoft Windows インストーラーの展開でアプリケーションが更新されるたびにユーザーが msp ファイルでは、更新プログラムをインストールしてインストールされた製品に適用します。[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開、更新プログラムを自動的に提供することができます。 アプリケーションの変更された部分のみがダウンロードされ、更新されたアプリケーションの全体はサイド バイ サイドの新しいフォルダーから再インストールされます。  

-   **ユーザーのコンピューターに及ぼす影響。** Windows インストーラーの展開、多くの場合、アプリケーションはバージョン管理の競合が発生する可能性を伴うの共有コンポーネントに依存しています。[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開、各アプリケーションは自己完結型、およびその他のアプリケーションに干渉することはできません。  
  
-   **セキュリティ アクセス許可。** Windows インストーラーの展開は、管理者権限を必要とし、限られたユーザーにのみインストールが制限されます。[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開は管理者権限をもたないユーザーにもインストールを可能とさせ、アプリケーションに必要なコード アクセス セキュリティのアクセス許可のみを付与します。  
  
 以前は、これらの問題が原因で、開発者で容易にするインストールのための豊富なユーザー インターフェイスを犠牲にして、Windows ベースのアプリケーションではなく Web アプリケーションを作成することもありました。 使用して配置されたアプリケーションを使用して、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]、両方のテクノロジの両方を活かすことができます。  
  
## <a name="what-is-a-clickonce-application"></a>ClickOnce アプリケーションとは何ですか。  
 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションは、Windows Presentation Foundation (.xbap)、Windows フォーム (.exe)、コンソール アプリケーション (.exe)、または Office ソリューション (.dll) を使用してパブリッシュ[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]テクノロジです。 発行することができます、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 3 つの方法でアプリケーション。 Web ページから、ネットワーク ファイル共有、または CD-ROM などのメディアからです。 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションはエンドユーザーのコンピューターにインストールされているし、コンピューターがオフライン、または完全に何も、エンドユーザーのコンピューターにインストールせず、オンラインのみのモードで実行することができる場合でもローカルで実行できます。 詳細については、「[ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)」を参照してください。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、自己更新することができます。使用可能になり、更新されたファイルを自動的に置き換えると、新しいバージョンのチェックインが可能です。 開発者は、更新動作を指定できます。ネットワーク管理者が制御できますも更新方法、たとえば、更新を必須としてマークします。 更新プログラムことができますもロールバック以前のバージョンに、エンドユーザーまたは管理者です。 詳細については、次を参照してください。 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)です。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションは、分離性、インストールまたは実行されている、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションは、既存のアプリケーションを中断できません。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、自己完結型です。各[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションにインストールされ、セキュリティで保護された、ユーザーごとに、アプリケーションごとのキャッシュから実行します。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、インターネットまたはイントラネット セキュリティ ゾーンで実行されます。 必要に応じて、アプリケーションは、管理者特権でのセキュリティのアクセス許可を要求できます。 詳細については、「[ClickOnce アプリケーションの発行](../deployment/securing-clickonce-applications.md)」を参照してください。  
  
## <a name="how-clickonce-security-works"></a>ClickOnce のセキュリティのしくみ  
 コア[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]セキュリティ証明書、コード アクセス セキュリティ ポリシー、および ClickOnce 信頼プロンプトに基づきます。  
  
### <a name="certificates"></a>証明書  
 Authenticode 証明書を使用して、アプリケーションの発行元の信頼性を確認します。 Authenticode を使用するとアプリケーションの展開は、ClickOnce は、有害なプログラムの合法的なプログラム確立されている、信頼できるソースからのものとして、それ自体を防ぐのに役立ちます。 必要に応じて、証明書は、アプリケーションの署名にも使用できるし、配置が、ファイルが改ざんされていないことを証明するためにマニフェストします。 詳細については、次を参照してください。 [ClickOnce と Authenticode](../deployment/clickonce-and-authenticode.md)です。 証明書は、信頼される発行者の一覧を持つクライアント コンピューターの構成にも使用できます。 アプリケーションが信頼された発行元になる場合は、ユーザーが介入せずインストールできます。 詳細については、「 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
### <a name="code-access-security"></a>コード アクセス セキュリティ  
 コード アクセス セキュリティにより、コードには保護されたリソースへのアクセスを制限します。 ほとんどの場合は、権限を制限するインターネットまたはローカル イントラネット ゾーンを選択できます。 使用して、**セキュリティ** ページで、 **ProjectDesigner**アプリケーションの適切なゾーンを要求します。 エンド ユーザー エクスペリエンスをエミュレートするために制限されたアクセス許可を持つアプリケーションをデバッグすることもできます。 詳細については、「[ClickOnce アプリケーションのコード アクセス セキュリティ](../deployment/code-access-security-for-clickonce-applications.md)」を参照してください。  
  
### <a name="clickonce-trust-prompt"></a>ClickOnce 信頼プロンプト  
 アプリケーションは、ゾーンでは、以上のアクセス許可を要求している場合、エンドユーザーは、信頼の決定するように求められますことができます。 エンドユーザーは、Windows フォーム アプリケーション、Windows Presentation Foundation アプリケーション、コンソール アプリケーション、XAML ブラウザー アプリケーション、および Office ソリューションなどの ClickOnce アプリケーションが信頼して実行できるかどうかを決定できます。 詳細については、次を参照してください。[する方法: ClickOnce 信頼プロンプト動作を構成する](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)です。  
  
## <a name="how-clickonce-deployment-works"></a>ClickOnce 配置のしくみ  
 コア[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開アーキテクチャは 2 つの XML マニフェスト ファイルに基づいて: アプリケーション マニフェストと配置マニフェスト。 ClickOnce アプリケーションがインストールされている、更新方法と更新された日時を記述するファイルが使用されます。  
  
### <a name="publishing-clickonce-applications"></a>ClickOnce アプリケーションの発行  
 アプリケーション マニフェストには、アプリケーション自体がについて説明します。 これには、アセンブリ、依存関係と、アプリケーション、必要なアクセス許可、および更新プログラムを利用できる場所を構成するファイルが含まれます。 アプリケーション開発者は、Visual Studio またはマニフェストの生成および編集ツール (Mage.exe) で発行ウィザードを使用して、アプリケーション マニフェストを作成できる、[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]です。 詳細については、次を参照してください。[する方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)です。  
  
 配置マニフェストは、アプリケーションを展開する方法について説明します。 これには、アプリケーション マニフェストの場所とクライアントで実行するアプリケーションのバージョンが含まれます。  
  
### <a name="deploying-clickonce-applications"></a>ClickOnce アプリケーションの配置  
 その作成した後、配置マニフェストが配置場所にコピーされます。 Web サーバー、ネットワーク ファイル共有、または、CD などのメディアを使用できます。 アプリケーション マニフェストとアプリケーションのすべてのファイルも、配置マニフェストで指定されている配置場所にコピーされます。 展開場所と同じにできますか、別の場所を指定できます。 使用する場合、**発行ウィザード**Visual Studio で、コピー操作は自動的に実行します。  
  
### <a name="installing-clickonce-applications"></a>ClickOnce アプリケーションをインストールします。  
 配置場所に配置される、後に、エンドユーザーはダウンロードして、Web ページ上、またはフォルダーに配置マニフェスト ファイルを表すアイコンをクリックしてアプリケーションをインストールできます。 ほとんどの場合、エンドユーザーが後にインストールが進行し、その他の介入なしに、アプリケーションが開始されて、インストールの確認をユーザーに確認する単純なダイアログ ボックスが表示されます。 高度な権限、またはアプリケーションが信頼された証明書によって署名されていないかどうか、アプリケーションが必要な場合、ダイアログ ボックスには、インストールを続行する前に、アクセス許可を付与するユーザーもが求められます。 ClickOnce のインストールですが、ユーザー単位は、管理者特権が必要な前提条件がある場合アクセス許可の昇格が必要あります。 高度な権限の詳細については、次を参照してください。 [ClickOnce アプリケーションのセキュリティで保護する](../deployment/securing-clickonce-applications.md)です。  
  
 証明書信頼できる、コンピューター レベルまたはエンタープライズ レベルで信頼された証明書で署名された ClickOnce アプリケーションをサイレント モードでインストールできるようにします。 信頼された証明書の詳細については、次を参照してください。[信頼されたアプリケーション展開の概要](../deployment/trusted-application-deployment-overview.md)です。  
  
 ユーザーのアプリケーションを追加することができます**開始**メニューおよび、**プログラム追加と削除**グループにおいて、**コントロール パネルの**です。 その他の展開テクノロジとは異なりに何も追加、 **Program Files**フォルダー、レジストリ、管理者権限がありませんがインストールに必要です  
  
> [!NOTE]
>  アプリケーションに追加されるを防止することも、**開始**メニューおよび**プログラム追加と削除**グループ、実質的に Web アプリケーションと同様に動作させます。 詳細については、「[ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)」を参照してください。  
  
### <a name="updating-clickonce-applications"></a>ClickOnce アプリケーションの更新  
 新しいアプリケーション マニフェストを生成し、展開の場所にファイルをコピー、アプリケーション開発者は、更新されたバージョンのアプリケーションを作成するときに、通常は、元のアプリケーションの展開フォルダーの兄弟フォルダーです。 管理者は、新しいバージョンのアプリケーションの場所を指す配置マニフェストを更新します。  
  
> [!NOTE]
>  **発行ウィザード**Visual Studio では、次の手順を実行する使用できます。  
  
 配置場所だけでなく、配置マニフェストには、更新プログラムの場所 (Web ページまたはネットワーク ファイル共有)、アプリケーションが更新されたバージョンのチェックも含まれます。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] **発行**プロパティを使用して、アプリケーションが更新プログラムの確認と、どのくらいの頻度を指定します。 配置マニフェストで更新動作を指定するかをにより、アプリケーションのユーザー インターフェイスでユーザーの選択肢として提示する、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Api です。 さらに、**発行**を以前のバージョンにロールバックするまたは更新を必須にするのには、プロパティを採用されていることができます。 詳細については、次を参照してください。 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)です。  
  
### <a name="third-party-installers"></a>サード パーティ製のインストーラー  
 ClickOnce インストーラー、アプリケーションと共にサード パーティ コンポーネントをインストールするをカスタマイズすることができます。 再頒布可能パッケージ (.exe または .msi ファイル) があるし、パッケージの言語に依存しない製品マニフェストと言語に固有のパッケージ マニフェストを記述する必要があります。 詳細については、次を参照してください。[ブートス トラップ パッケージを作成する](../deployment/creating-bootstrapper-packages.md)です。  
  
## <a name="clickonce-tools"></a>ClickOnce ツール  
 次の表は、生成、編集、署名、および、アプリケーション マニフェストと配置マニフェストに再署名に使用できるツールを示します。  
  
|ツール|説明|  
|----------|-----------------|  
|[[セキュリティ] ページ (プロジェクト デザイナー)](../ide/reference/security-page-project-designer.md)|記号、アプリケーション マニフェストと配置マニフェスト。|  
|[[発行] ページ (プロジェクト デザイナー)](../ide/reference/publish-page-project-designer.md)|生成し、Visual Basic および Visual c# アプリケーションのアプリケーションおよび配置マニフェストを編集します。|  
|[Mage.exe (マニフェストの生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Visual Basic、Visual c#、および Visual C アプリケーションのアプリケーションおよび配置マニフェストを生成します。<br /><br /> 署名し、アプリケーション マニフェストと配置マニフェストに再署名します。<br /><br /> バッチ スクリプトおよびコマンド プロンプトから実行できます。|  
|[MageUI.exe (マニフェスト生成および編集ツールのグラフィカル クライアント)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|生成し、アプリケーション マニフェストと配置マニフェストを編集します。<br /><br /> 署名し、アプリケーション マニフェストと配置マニフェストに再署名します。|  
|[GenerateApplicationManifest タスク](../msbuild/generateapplicationmanifest-task.md)|アプリケーション マニフェストを生成します。<br /><br /> MSBuild から実行できます。 詳細については、次を参照してください。 [MSBuild リファレンス](../msbuild/msbuild-reference.md)です。|  
|[GenerateDeploymentManifest タスク](../msbuild/generatedeploymentmanifest-task.md)|配置マニフェストを生成します。<br /><br /> MSBuild から実行できます。 詳細については、次を参照してください。 [MSBuild リファレンス](../msbuild/msbuild-reference.md)です。|  
|[SignFile タスク](../msbuild/signfile-task.md)|記号、アプリケーション マニフェストと配置マニフェスト。<br /><br /> MSBuild から実行できます。 詳細については、次を参照してください。 [MSBuild リファレンス](../msbuild/msbuild-reference.md)です。|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|アプリケーション マニフェストと配置マニフェストを生成する、独自のアプリケーションを開発します。|  
  
 次の表は、これらのブラウザーで ClickOnce アプリケーションをサポートするために必要な .NET Framework のバージョンを示します。  
  
|ブラウザー|.NET Framework のバージョン|  
|-------------|----------------------------|  
|Internet Explorer|2.0、3.0、3.5、4、3.5 SP1|  
|Firefox|2.0 SP1、3.5 SP1 は、4|  
  
## <a name="see-also"></a>関連項目  
 [Windows Vista の ClickOnce 配置](../deployment/clickonce-deployment-on-windows-vista.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce での COM コンポーネントの配置](../deployment/deploying-com-components-with-clickonce.md)   
 [ClickOnce アプリケーションのコマンド ラインからのビルド](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [System.Deployment.Application を使用する ClickOnce アプリケーションのデバッグ](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
