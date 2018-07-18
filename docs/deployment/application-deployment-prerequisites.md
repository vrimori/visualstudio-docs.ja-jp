---
title: アプリケーション展開の前提条件 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 48f72640bdf8efc53b278e4600c6b262dc1a26bf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31565693"
---
# <a name="application-deployment-prerequisites"></a>アプリケーション配置の必要条件
アプリケーションが正常にインストールされ、実行されるようにするには、アプリケーションが依存しているすべてのコンポーネントがターゲット コンピューターに既にインストールされていることを最初に確認する必要があります。 たとえば、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を使用して作成されたほとんどのアプリケーションは、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] に依存します。アプリケーションをインストールする前に、共通言語ランタイムの適切なバージョンが、ターゲット コンピューター上に存在している必要があります。  
  
 これらの前提条件を選択することができます、**の前提条件 ダイアログ ボックス**.NET Framework およびその他の再頒布可能パッケージ、インストールの一部としてインストールします。 この実習と呼ばれる*ブートス トラップ*です。 次に、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]とも呼ばれる、Setup.exe をという名前の Windows 実行可能プログラムを生成、*ブートス トラップ*です。 ブートストラップは、アプリケーションが実行される前にこれらの必須コンポーネントをインストールします。 これらの前提条件の選択の詳細については、次を参照してください。[の前提条件 ダイアログ ボックス](../ide/reference/prerequisites-dialog-box.md)です。  
  
 各必須コンポーネントはブートストラップ パッケージです。 ブートストラップ パッケージは、必須コンポーネントのインストール方法を記述するマニフェスト ファイルを含むディレクトリおよびファイルのグループです。 アプリケーションの前提条件が記載されていない場合、**前提条件 ダイアログ ボックス**、カスタム ブートス トラップ パッケージを作成して Visual Studio に追加します。 前提条件を選択してから、**の前提条件 ダイアログ ボックス**です。 詳細については、次を参照してください。[ブートス トラップ パッケージを作成する](../deployment/creating-bootstrapper-packages.md)です。  
  
 既定では、ブートストラップは ClickOnce の配置で有効です。 ClickOnce の配置に生成されるブートストラップは署名付きです。 ブートストラップは任意のコンポーネントに対して無効にできますが、これは、該当するコンポーネントの正しいバージョンが既にすべてのターゲット コンピューターにインストールされていることを確認した場合のみに限定してください。  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>ブートストラップと ClickOnce 配置  
 アプリケーションをクライアント コンピューターにインストールする前に、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] はクライアントを検査して、アプリケーション マニフェストに一定の必要条件が指定されているかどうかを確認します。 次に例を示します。  
  
-   最低限必要な共通言語ランタイムのバージョン。これはアプリケーション マニフェストにアセンブリ依存関係として指定されます。  
  
-   アプリケーションに最低限必要な Windows オペレーティング システムのバージョン。これは、アプリケーション マニフェストに `<osVersionInfo>` 要素を使用して指定されます。 (を参照してください[\<依存関係 > 要素](../deployment/dependency-element-clickonce-application.md))  
  
-   グローバル アセンブリ キャッシュ (GAC) にプレインストールされる必要があるすべてのアセンブリの最小バージョン。これは、アセンブリ マニフェストでアセンブリ依存関係の宣言によって指定されます。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 不足している前提条件を検出できるし、ブートス トラップを使用して、前提条件をインストールすることができます。 詳細については、次を参照してください。[する方法: ClickOnce アプリケーションと共に必須コンポーネントをインストール](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)です。  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] や MageUI.exe などのツールによって生成されたマニフェスト内の値を変更するには、アプリケーション マニフェストをテキスト エディターで編集した後に、アプリケーション マニフェストと配置マニフェストの両方に再署名する必要があります。 詳細については、「 [方法: アプリケーション マニフェストおよび配置マニフェストに再署名する](../deployment/how-to-re-sign-application-and-deployment-manifests.md)」を参照してください。  
  
 Visual Studio と ClickOnce を使用してアプリケーションを配置する場合、既定で選択されるブートストラップ パッケージは、ソリューション内の .NET Framework のバージョンによって異なります。 ただし、対象の .NET Framework バージョンを変更する場合は、オプションを更新する必要があります、**の前提条件 ダイアログ ボックス**手動でします。  
  
|対象の .NET Framework|選択されるブートストラップ パッケージ|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows インストーラー 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows インストーラー 3.1|  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置では、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 発行ウィザードで作成された Publish.htm ページが、アプリケーションのみをインストールするリンクまたはアプリケーションとブートストラップ コンポーネントの両方をインストールするリンクのいずれかを指します。  
  
 ClickOnce 発行ウィザードまたは Visual Studio の [発行] ページを使用してブートストラップを生成する場合、Setup.exe は自動的に署名されます。 ただし、顧客の証明書を使用してブートストラップに署名する場合は、後でファイルに署名できます。  
  
## <a name="bootstrapping-and-msbuild"></a>ブートストラップと MSBuild  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を使用せず、アプリケーションをコマンド ラインでコンパイルする場合は、Microsoft Build Engine (MSBuild) タスクを使用して [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ブートストラップ アプリケーションを作成できます。 詳細については、次を参照してください。 [GenerateBootstrapper タスク](../msbuild/generatebootstrapper-task.md)です。  
  
 ブートストラップの代わりに、Microsoft SMS (Systems Management Server) などの電子ソフトウェア配布システムを使用して、コンポーネントを事前に配置することもできます。  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>ブートストラップ (Setup.exe) のコマンド ライン引数  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって作成される Setup.exe と MSBuild タスクは、次の小さなコマンド ライン引数セットをサポートします。 ブートストラップ アプリケーションに提供されるこれ以外のすべての引数は、アプリケーション インストーラーに渡されます。  
  
 ブートストラップ オプションを変更する場合は、未署名のブートストラップを変更し、後でブートストラップ ファイルに署名する必要があります。  
  
|コマンド ライン引数|説明|  
|---------------------------|-----------------|  
|**-?, -h, -help**|[ヘルプ] ダイアログ ボックスを表示します。|  
|**-url, -componentsurl**|このセットアップ用に保存されている URL とコンポーネントの URL を表示します。|  
|**-url =** `location`|Setup.exe が [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを検索する URL を設定します。|  
|**-componentsurl =** `location`|Setup.exe が [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] などの依存関係を検索する URL を設定します。 |  
|**homesite-=** `true`**&#124;** `false`|`true`の場合、ベンダーサイトの適切な場所から依存関係がダウンロードされます。 これによって **- componentsurl** の設定が上書きされます。 `false` の場合は、**-componentsurl** で指定された URL から依存関係がダウンロードされます。|  

## <a name="operating-system-support"></a>オペレーティング システムのサポート  
 Visual Studio ブートストラップは、Windows Server 2008 Server Core ではサポートされていません。また、機能が限定された、メンテナンスの容易なサーバー環境を提供する Windows Server 2008 R2 Server Core でもサポートされていません。 たとえば、Server Core のインストール オプションでは、.NET Framework 3.5 Server Core プロファイルのみがサポートされています。そのため、完全な .NET Framework を必要とする Visual Studio の機能は実行できません。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)
