---
title: '方法: ソース管理プラグインのインストール |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3487c796661a8194b9c920f43bae9df87f1ba57d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950265"
---
# <a name="how-to-install-a-source-control-plug-in"></a>方法: ソース管理プラグインのインストール
ソース管理プラグインを作成するには、3 つの手順が含まれます。  

1. このドキュメントのソース管理プラグイン API リファレンスのセクションで定義された関数では、DLL を作成します。  

2. ソース管理プラグイン API 定義の関数を実装します。 ときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]呼び出し、インターフェイスとダイアログ ボックスから使用できるように、プラグイン。  

3. DLL を登録するには、適切なレジストリ エントリを作成します。  

## <a name="integration-with-visual-studio"></a>Visual Studio との統合  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ソース管理プラグイン API に準拠するソース管理プラグインをサポートしています。  

### <a name="register-the-source-control-plug-in"></a>ソース管理プラグインの登録します。  
 ソースをまず見つける必要があります、実行中の統合開発環境 (IDE) は、ソース管理システムを呼び出すことが、前に、API をエクスポートするプラグインの DLL を制御します。  

#### <a name="to-register-the-source-control-plug-in-dll"></a>ソース管理プラグインの DLL を登録するには  

1. 下の 2 つのエントリを追加、 **HKEY_LOCAL_MACHINE**キー、**ソフトウェア**製品名のサブキーの後に、会社の名前のサブキーを指定するサブキー。 パターンは、 **hkey_local_machine \software\\\<会社名 >\\\<製品名 >\\\<エントリ >**  =  *値*します。 2 つのエントリが常に呼び出されます**SCCServerName**と**SCCServerPath**します。 それぞれは、通常の文字列です。  

    たとえば場合、会社名は、Microsoft と SourceSafe の名前は、ソース管理製品をこのレジストリ パスになります**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**します。 このサブキーは最初のエントリの**SCCServerName**は、製品の名前を付け、ユーザーが判読できる文字列です。 2 番目のエントリ**SCCServerPath**は、ソースへの完全パスに接続する IDE プラグインの DLL を制御します。 レジストリ エントリの例を次に示します。  

   |レジストリ エントリの例|サンプル値|  
   |---------------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|  

   > [!NOTE]
   >  SCCServerPath は、SourceSafe プラグインへの完全パスです。 ソース管理プラグインでは、同じレジストリ エントリのパスが異なる会社と製品の名前を使用します。  

2. ソース管理プラグインの動作を変更するのには、次のオプションのレジストリ エントリを使用できます。 これらのエントリは、同じサブキーとして移動**SccServerName**と**SccServerPath**します。  

   - **HideInVisualStudioregistry**コントロール-プラグ-内に表示される、ソースを設定したくない場合、エントリを使用できます、**プラグインの選択**の一覧[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 ソース管理プラグインへの自動切り替えは、このエントリによっても影響します。 このエントリの用途の 1 つは、ソース管理プラグインを置換するソース管理パッケージを指定するが、ソース管理プラグインのソース管理パッケージを使用してから移行するユーザーを容易にできるようにするかどうかは。 ソース管理パッケージがインストールされている場合は、プラグインを非表示にこのレジストリ エントリを設定します。  

      **HideInVisualStudio** DWORD の値に設定されている、 *1*プラグインを非表示にまたは*0*プラグインを表示します。 レジストリ エントリが表示されない場合、既定の動作は、プラグインを表示するのには。  

   - **DisableSccManager**レジストリ エントリを無効にするか、または非表示に使用できる、**起動\<ソース管理サーバー >** 通常下に表示されるメニュー オプション、 **ファイル** > **ソース管理**サブメニューで開く。 このメニューを選択するオプションを呼び出し、 [SccRunScc](../../extensibility/sccrunscc-function.md)関数。 外部プログラムのソース管理プラグインでは対応していないとする可能性がありますを無効または非表示にもそのため、**起動**メニュー オプション。  

      **DisableSccManager** DWORD の値に設定されている、 *0*有効にする、**起動\<ソース管理サーバー >** に設定 メニュー オプション*1*にメニュー オプションを無効にし、設定*2*メニュー オプションを非表示にします。 このレジストリ エントリが表示されない場合、既定の動作では、メニュー オプションを説明します。  

   | レジストリ エントリの例 | サンプル値 |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |


3. サブキーを追加**SourceCodeControlProvider**下で、 **HKEY_LOCAL_MACHINE**キー、**ソフトウェア**サブキー。  

    このサブキーのレジストリ エントリの下**ProviderRegKey**手順 1. でレジストリに配置したサブキーを表す文字列に設定されます。 パターンは、 **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey** = *ソフトウェア\\< 会社名\>\\< 製品名\>*.  

    このサブキーのサンプルの内容を次に示します。  

   |レジストリ エントリ|サンプル値|  
   |--------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  

   > [!NOTE]
   >  ソース管理プラグインは、同じサブキーとエントリの名前を使用してが異なる値になります。  

4. という名前のサブキーを作成**InstalledSCCProviders**下、 **SourceCodeControlProvider**サブキー、およびそのサブキーの下の 1 つのエントリを配置します。  

    このエントリの名前が (同じ SCCServerName エントリに指定された値)、プロバイダーのユーザーが判読できる名前と値が、もう一度、手順 1. で作成されたサブキー。 パターンは、 **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<display name>** = *ソフトウェア\\< 会社名\> \\< 製品名\>* します。  

    例えば:  

   |レジストリ エントリの例|サンプル値|  
   |---------------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  

   > [!NOTE]
   >  複数ソース管理プラグインをこの方法で登録されていることができます。 これは、どのように[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]インストールされているすべてのソース管理プラグイン API ベースのプラグインを検索します。  

## <a name="how-an-ide-locates-the-dll"></a>IDE が DLL を検索する方法  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE は、2 つのソースを見つける方法は、プラグインの DLL を制御します。  

- 既定のソース管理プラグインを検索しをサイレント モードで接続します。  

- 検索登録されているすべてのソース管理プラグインを元のユーザーが 1 つ選択しました。  

  IDE では、最初の方法で、DLL を検索する、 **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider**エントリのサブキー **ProviderRegKey**します。 このエントリの値は、別のサブキーを指します。 IDE がという名前のエントリを検索し、 **SccServerPath**サブキーの下に 2 つ目**HKEY_LOCAL_MACHINE**します。 このエントリの値は、DLL を IDE を指します。  

> [!NOTE]
>  IDE が相対パスから Dll を読み込めません (たとえば、 *.\NewProvider.DLL*)。 DLL への完全なパスを指定する必要があります (たとえば、 *c:\Providers\NewProvider.DLL*)。 これは、承認されていないか、権限を借用したプラグインの Dll の読み込みを防止することで、IDE のセキュリティを強化します。  

 IDE では 2 つ目の方法で、DLL を検索する、 **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders**すべてのエントリのサブキー。 各エントリは、名前と値があります。 ユーザーにこれらの名前の一覧が表示されます。 ユーザーが 名前を IDE は、サブキーを指している選択した名前の値を検索します。 IDE という名前のエントリを探します**SccServerPath**そのサブキーの下で**HKEY_LOCAL_MACHINE**します。 そのエントリの値は、適切な DLL を IDE を指します。  

 ソース管理プラグインは、DLL が見つからないのどちらの方法をサポートする必要があり、その結果、設定**ProviderRegKey**、任意の以前の設定を上書きします。 さらに、その必要があります自体の一覧に追加**InstalledSccProviders**のため、ユーザーが使用するには、ソース管理プラグインの選択を持つことができます。  

> [!NOTE]
>  **HKEY_LOCAL_MACHINE**キーの使用は、1 つだけのソース管理プラグインは、特定のコンピューターでプラグイン既定のソース管理として登録できます (ただし、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース管理プラグインを確認することができます実際に使用する特定のソリューションに対して)。 インストール プロセス中にかどうか、ソース管理プラグインは既に設定; を確認します。そうである場合、ユーザーに求めます新しいソース コントロールの既定値としてインストールされているプラグインを設定するかどうか。 アンインストール中、削除しないでくださいすべてソース管理プラグインでに共通するその他のレジストリ サブキー **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**;、特定の SCC サブキーのみを削除します。  

## <a name="how-the-ide-detects-version-1213-support"></a>IDE はバージョン 1.2 と 1.3 のサポートを検出する方法  
 方法は[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プラグインがサポートのソース管理プラグイン API バージョン 1.2 と 1.3 機能かどうかを検出しますか? 高度な機能を宣言するには、ソース管理プラグインは、対応する関数を実装する必要があります。  

 まず、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]呼び出しによって返される値をチェック、 [SccGetVersion](../../extensibility/sccgetversion-function.md)します。 1.2 以上があります。  

 次に、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を調べることで、特定の新しい機能がサポートされているかどうか、`lpSccCaps`の引数、 [SccInitialize](../../extensibility/sccinitialize-function.md)します。  

 両方の条件が満たされた場合は、バージョン 1.2 および 1.3 でサポートされる新しい関数を呼び出すことできます。  

## <a name="see-also"></a>関連項目  
 [ソース管理プラグインを概要します。](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)