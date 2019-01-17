---
title: アプリケーション展開の前提条件 |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 0baff8d685a1ac5f4899edc2f1dbf6ddf9c2e5b9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941074"
---
# <a name="application-deployment-prerequisites"></a>アプリケーション配置の必要条件

アプリケーションをインストールし、正常に実行するには、まず、アプリケーションが対象のコンピュータに依存するすべてのコンポーネントをインストールします。 ほとんどのアプリケーションなどを使用して作成[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]依存関係を持つ、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]します。 この場合は、共通言語ランタイムの正しいバージョンを対象のコンピューター上に存在するアプリケーションをインストールする前にあります。  

 これらの前提条件を選択することができます、 **Prerequisites Dialog Box**し、インストールの一部として、.NET Framework およびその他の再頒布可能パッケージをインストールします。 この方法は*ブートストラップ*と呼ばれます。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] という名前の Windows 実行可能プログラムが生成されます*Setup.exe*とも呼ばれる、*ブートス トラップ*します。 ブートストラップは、アプリケーションが実行される前にこれらの必須コンポーネントをインストールします。 これらの前提条件を選択する方法についての詳細については、次を参照してください。[の前提条件 ダイアログ ボックス](../ide/reference/prerequisites-dialog-box.md)します。  

 各必須コンポーネントはブートストラップ パッケージです。 ブートス トラップ パッケージは、ディレクトリと、前提条件をインストールする方法について説明するマニフェスト ファイルを含むファイルのグループです。 アプリケーションの必須コンポーネントが **[必須コンポーネント]** ダイアログ ボックスに表示されない場合は、カスタム ブートストラップ パッケージを作成して Visual Studio に追加できます。 それにより、**[必須コンポーネント]** ダイアログ ボックスで必須コンポーネントを選択できるようになります。 詳細については、次を参照してください。[ブートス トラップ パッケージを作成する](../deployment/creating-bootstrapper-packages.md)します。  

 既定では、ブートストラップは ClickOnce の配置で有効です。 ClickOnce の配置に生成されるブートストラップは署名付きです。 コンポーネントは、ブートス トラップを無効にできますが、すべてのターゲット コンピューターで、コンポーネントの正しいバージョンが既にインストールされていることが確実場合にのみ。  

## <a name="bootstrapping-and-clickonce-deployment"></a>ブートストラップと ClickOnce 配置  
 クライアント コンピューターでアプリケーションをインストールする前に[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション マニフェストで指定された要件があることを確認するクライアントを検査します。 次の要件が含まれます。  

- 最低限必要な共通言語ランタイムのバージョン。これはアプリケーション マニフェストにアセンブリ依存関係として指定されます。  

- アプリケーションに最低限必要な Windows オペレーティング システムのバージョン。これは、アプリケーション マニフェストに `<osVersionInfo>` 要素を使用して指定されます。 (を参照してください[\<依存関係 > 要素](../deployment/dependency-element-clickonce-application.md))。  

- アセンブリ マニフェストにアセンブリ依存関係の宣言で指定されたグローバル アセンブリ キャッシュ (GAC) にプレインストールする必要がありますすべてのアセンブリの最小バージョン。  

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 不足している前提条件を検出できるし、ブートス トラップを使用して、前提条件をインストールすることができます。 詳細については、「[方法 :ClickOnce アプリケーションと共に必須コンポーネントをインストールする](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)」を参照してください。  

> [!NOTE]
>  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] や *MageUI.exe* などのツールによって生成されたマニフェスト内の値を変更するには、アプリケーション マニフェストをテキスト エディターで編集した後に、アプリケーション マニフェストと配置マニフェストの両方に再署名する必要があります。 詳細については、「[方法 :アプリケーション マニフェストと配置マニフェストの再署名](../deployment/how-to-re-sign-application-and-deployment-manifests.md)」を参照してください。  

 Visual Studio と ClickOnce を使用してアプリケーションを配置する場合、既定で選択されるブートストラップ パッケージは、ソリューション内の .NET Framework のバージョンによって異なります。 ただし、対象の .NET Framework のバージョンを変更する場合は、**[必須コンポーネント]** ダイアログ ボックスのオプションを手動で更新する必要があります。  

|対象の .NET Framework|選択されるブートストラップ パッケージ|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows インストーラー 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows インストーラー 3.1|  

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置では、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 発行ウィザードで作成された *Publish.htm* ページが、アプリケーションのみをインストールするリンクまたはアプリケーションとブートストラップ コンポーネントの両方をインストールするリンクのいずれかを指します。  

 ClickOnce 発行ウィザードまたは Visual Studio の [発行] ページを使用してブートストラップを生成する場合、*Setup.exe* は自動的に署名されます。 ただし、顧客の証明書を使用してブートストラップに署名する場合は、後でファイルに署名できます。  

## <a name="bootstrapping-and-msbuild"></a>ブートストラップと MSBuild  
 使用しない場合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ではなく、コマンドラインでのアプリケーションをコンパイルは、作成できますが、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Microsoft Build Engine (MSBuild) タスクを使用してアプリケーションをブートス トラップします。 詳細については、次を参照してください。 [GenerateBootstrapper タスク](../msbuild/generatebootstrapper-task.md)します。  

 ブートストラップの代わりに、Microsoft SMS (Systems Management Server) などの電子ソフトウェア配布システムを使用して、コンポーネントを事前に配置することもできます。  

## <a name="bootstrapper-setupexe-command-line-arguments"></a>ブートストラップ (Setup.exe) のコマンド ライン引数  
 *Setup.exe*によって生成された[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]MSBuild タスクは、次のコマンドライン引数のセットをサポートしています。 その他の引数は、アプリケーションのインストーラーに転送されます。  

 ブートス トラップ オプションを変更する場合は、未署名のブートス トラップの変更し、ブートス トラップ ファイルを後でサインインする必要があります。  


| コマンド ライン引数 | 説明 |
| - | - |
| **-?、-h、-help** | [ヘルプ] ダイアログ ボックスを表示します。 |
| **-- 用の url** | このセットアップ用に保存されている URL とコンポーネントの URL を表示します。 |
| **-url =** `location` | *Setup.exe* が [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを検索する URL を設定します。 |
| **-用 =** `location` | *Setup.exe* が [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] などの依存関係を検索する URL を設定します。 |
| **homesite-=** `true`**&#124;** `false` | ときに`true`、仕入先のサイトで適切な場所からの依存関係をダウンロードします。 この設定をオーバーライド、 **- 用**設定します。 ときに`false`で指定された URL から依存関係がダウンロード **- 用**します。 |

## <a name="operating-system-support"></a>オペレーティング システムのサポート  
 Visual Studio ブートス トラップは、低いメンテナンス サーバー環境を提供する機能が制限された Windows Server 2008 の Server Core または Windows Server 2008 R2 Server Core でサポートされていません。 たとえば、Server Core インストール オプションは、完全な .NET Framework に依存する Visual Studio の機能を実行することはできませんが、.NET Framework 3.5 Server Core プロファイルのみをサポートします。  

## <a name="see-also"></a>関連項目  
 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)
