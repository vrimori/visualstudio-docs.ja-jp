---
title: '方法: ソース管理プラグインのインストール |Microsoft ドキュメント'
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
ms.openlocfilehash: 4ffabd7adf35956163c8744eae6539e96990f38a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133558"
---
# <a name="how-to-install-a-source-control-plug-in"></a>方法: ソース管理プラグインのインストール
ソース管理プラグインを作成するには、3 つの手順が含まれます。  
  
1.  このドキュメントのソース管理プラグイン API リファレンスのセクションで定義された関数を DLL を作成します。  
  
2.  ソース管理プラグイン API 定義の関数を実装します。 ときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]呼び出し、により、インターフェイスとダイアログ ボックス、プラグインから入手できます。  
  
3.  適切なレジストリ エントリを作成する、DLL を登録します。  
  
## <a name="integration-with-visual-studio"></a>Visual Studio との統合  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ソース管理プラグイン API に準拠するソース管理プラグインをサポートしています。  
  
### <a name="registering-the-source-control-plug-in"></a>ソース管理プラグインを登録します。  
 ソースが見つける必要がありますまず実行中の統合開発環境 (IDE) は、ソース管理システムに呼び出すことができます、前に、API をエクスポートするプラグインの DLL を制御します。  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>ソース管理プラグインの DLL を登録するには  
  
1.  製品名のサブキーを続けて、会社名サブキーを指定する、ソフトウェア サブキー HKEY_LOCAL_MACHINE キーに 2 つのエントリを追加します。 パターンは、hkey_local_machine \software\\ *[会社名]*\\ *[製品名]*\\ *[入力]* = 値です。 SCCServerName と SCCServerPath、2 つのエントリが常に呼び出されます。 各は、正規の文字列です。  
  
     たとえば、会社名が Microsoft と、ソース管理製品の場合はという名前の SourceSafe、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe するレジストリのパスとなります。 このサブキーには、最初のエントリ、SCCServerName は、製品の名前を付け、ユーザーが判読できる文字列です。 2 番目のエントリでは、SCCServerPath は、ソースへの完全パスに接続する IDE プラグインの DLL を制御します。 レジストリ エントリの例を次に示します。  
  
    |レジストリ エントリの例|サンプル値|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  SCCServerPath は、SourceSafe プラグインへの完全パスです。 ソース管理プラグインでは、同じレジストリ エントリのパスが異なる会社と製品の名前を使用します。  
  
2.  ソース管理プラグインの動作を変更するのには、次のオプションのレジストリ エントリを使用できます。 これらのエントリは、SccServerName および SccServerPath として同じサブキーに移動します。  
  
    -   コントロールのプラグ-内のプラグインの選択 一覧に表示される、ソースを設定したくない場合、HideInVisualStudioregistry エントリを使用できます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 ソース管理プラグインを自動切り替えは、このエントリによっても影響します。 このエントリの用途の 1 つは、かどうか、ソース管理プラグインを置換するソース管理パッケージを指定する必要しますが、ソース管理プラグイン ソース管理パッケージを使用してから移行するユーザーを容易にできるようにします。 ソース管理パッケージがインストールされている場合は、このレジストリ エントリ、プラグインを非表示を設定します。  
  
         HideInVisualStudio は、DWORD の値は、プラグインを非表示を 1 またはプラグインを表示する場合は 0 に設定されています。 レジストリ エントリが表示されない場合、既定の動作は、プラグインを表示するのには。  
  
    -   DisableSccManager レジストリ エントリを無効または非表示に使用できる、**起動\<ソース管理サーバー >** 下に通常表示されるメニュー オプション、**ファイル** ->  **ソース管理** をクリックします。 このメニューを選択するオプションを呼び出し、 [SccRunScc](../../extensibility/sccrunscc-function.md)関数。 ソース管理プラグインには、外部プログラムのことはできませんし、したがってを無効にするにまたはでも非表示にする場合があります、**起動**メニュー オプション。  
  
         DisableSccManager は DWORD 値が 0 に設定を有効にする、**起動\<ソース管理サーバー >** メニュー オプションを 1 に設定 メニュー オプションを無効にして、メニュー オプションを非表示にする 2 に設定します。 このレジストリ エントリが表示されない場合、既定の動作では、メニュー オプションを説明します。  
  
    |レジストリ エントリの例|サンプル値|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  下のサブキー、SourceCodeControlProvider、ソフトウェア サブキー HKEY_LOCAL_MACHINE キーを追加します。  
  
     このサブキーにレジストリ エントリ ProviderRegKey éý ' è を手順 1. でレジストリに配置したサブキーを表す文字列。 パターンは、HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey ソフトウェアを =\\ *[会社名]*\\ *[製品名]* です。  
  
     このサブキーにサンプルの内容を次に示します。  
  
    |レジストリ エントリ|サンプル値|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  同じサブキーとエントリ名、ソース管理プラグインが使用されますが、値が異なる場合します。  
  
4.  SourceCodeControlProvider サブキーの下で InstalledSCCProviders をという名前のサブキーを作成し、そのサブキーの下の 1 つのエントリを配置します。  
  
     このエントリの名前が (同じ SCCServerName エントリに指定された値)、プロバイダーのユーザーが判読できる名前と値が、もう一度、手順 1. で作成されたサブキー。 パターンは、HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\ *[表示名]* ソフトウェアを =\\ *[会社名]* \\ *[製品名]* です。  
  
     例えば:  
  
    |レジストリ エントリの例|サンプル値|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  複数ソース管理プラグインをこの方法で登録されていることができます。 これは、どのように[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]すべてのインストール ソース管理プラグイン API ベースのプラグインを検索します。  
  
## <a name="how-an-ide-locates-the-dll"></a>IDE が DLL を検索する方法  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE は、2 つのソースを見つける方法は、プラグイン DLL を制御します。  
  
-   既定のソース管理プラグインを検索し、サイレントに接続します。  
  
-   検索登録されているすべてのソース管理プラグイン元となる、ユーザーが 1 つ選択します。  
  
 最初の方法で、DLL を検索するには、IDE ではエントリ ProviderRegKey HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider サブキーの下で検索します。 このエントリの値は、別のサブキーを指します。 IDE は、その 2 つ目のサブキー HKEY_LOCAL_MACHINE の下で SccServerPath をという名前のエントリを探します。 このエントリの値は、DLL に IDE を指します。  
  
> [!NOTE]
>  IDE では、相対パス (たとえば、.\NewProvider.DLL) から Dll が読み込まれません。 DLL への完全パスを指定する必要があります (たとえば、c:\Providers\NewProvider.DLL)。 これは、承認されていないか、権限を借用したプラグインの Dll の読み込みを実行できないようにして、IDE のセキュリティを強化します。  
  
 2 番目の方法で、DLL を検索する IDE ですべてのエントリの HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders サブキーの下で検索*です。* 各エントリには、名前と値があります。 IDE では、これらの名前の一覧を表示をユーザーに*です。* 名前を選択すると、IDE はサブキーを指している選択した名前の値を検索します。 IDE は、そのサブキー hkey_local_machine SccServerPath をという名前のエントリを探します。 そのエントリの値は、正しい DLL を IDE を指します。  
  
 ソース管理プラグインは、2 つの DLL を検索する方法をサポートし、その結果、ProviderRegKey、元のすべての設定を上書きを設定する必要があります。 さらに、その必要があります自体の一覧に追加 InstalledSccProviders のため、ユーザーが使用するソース管理プラグインの選択肢を持つことができます。  
  
> [!NOTE]
>  HKEY_LOCAL_MACHINE キーを使用するための 1 つだけのソース管理プラグインが、既定のソース管理プラグイン特定のコンピューター上として登録されていることができます (ただし、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]するソース管理プラグインの実際に使用するかを決定できる、特定のソリューションです。) インストール プロセス中にかどうか、ソース管理プラグインが既に設定されているを確認します。場合は、ユーザーに確認、新しいソース コントロールの既定値としてインストールされるプラグインを設定するかどうかを指定します。 アンインストールが、中に削除しないでくださいすべてソース管理プラグイン HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider; 内に共通するその他のレジストリ サブキー特定の SCC サブキーのみを削除します。  
  
## <a name="how-the-ide-detects-version-1213-support"></a>IDE がバージョン 1.2/1.3 のサポートを検出する方法  
 方法は[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プラグインがサポート ソース コントロールのプラグイン API バージョン 1.2、1.3 機能かどうかを検出しますか? 高度な機能を宣言するには、ソース管理プラグインは、対応する関数を実装する必要があります。  
  
 最初に、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]呼び出しで返される値を調べて、 [SccGetVersion](../../extensibility/sccgetversion-function.md)です。 1.2 以上にする必要があります。  
  
 次に、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を調べることによって、特定の新機能がサポートされているかどうかを判断、`lpSccCaps`の引数で、 [SccInitialize](../../extensibility/sccinitialize-function.md)です。  
  
 2 つの条件が満たされた場合は、1.2 および 1.3 のバージョンでサポートされる新しい関数が呼び出すことができます。  
  
## <a name="see-also"></a>関連項目  
 [はじめに](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)