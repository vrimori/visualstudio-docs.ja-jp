---
title: "方法: ソース管理プラグインのインストール | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理プラグインのインストール [Visual Studio SDK]"
  - "ソース管理プラグインをインストールします。"
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: 32
caps.handback.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: ソース管理プラグインのインストール
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソース管理プラグインを作成するには、3 つの手順が含まれます。  
  
1.  このドキュメントのソース管理プラグインの API のリファレンス セクションで定義された関数を DLL を作成します。  
  
2.  ソース管理プラグインの API 定義の関数を実装します。 ときに [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] への呼び出しのインターフェイスとダイアログ ボックスから使用できるように、プラグインします。  
  
3.  適切なレジストリ エントリを作成して、DLL を登録します。  
  
## <a name="integration-with-visual-studio"></a>Visual Studio との統合  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ソース管理プラグインの API に準拠するソース管理プラグインをサポートしています。  
  
### <a name="registering-the-source-control-plug-in"></a>ソース管理プラグインを登録します。  
 ソースを最初に検索する必要がありますソース管理システムに、実行中の統合開発環境 (IDE) を呼び出すことのできる前に、API をエクスポートするプラグインの DLL を制御します。  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>ソース管理プラグイン DLL を登録するには  
  
1.  内のソフトウェアのサブキー、製品の名前のサブキーの後に、会社名サブキーを指定するには、HKEY_LOCAL_MACHINE キーの下の 2 つのエントリを追加します。 パターンは、hkey_local_machine \software\\*[会社名]*\\*[製品名]*\\*[entry]* = の値。 SCCServerName と SCCServerPath、2 つのエントリが常に呼び出されます。 それぞれは、正規の文字列です。  
  
     たとえば、会社名には、Microsoft であり、ソース管理製品場合名前は SourceSafe、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe するレジストリのパスとです。 このサブキーには、最初のエントリでは、SCCServerName は、お使いの製品の名前を付けるユーザーが判読できる文字列です。 2 番目のエントリでは、SCCServerPath では、ソースへの完全パスに接続する IDE プラグインの DLL を制御します。 レジストリ エントリの例を次に示します。  
  
    |レジストリ エントリの例|サンプル値|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  SCCServerPath は、SourceSafe プラグインへの完全パスです。 ソース管理プラグインでは、同じレジストリ エントリのパスが異なる会社と製品の名前を使用します。  
  
2.  ソース管理プラグインの動作を変更するは、次のオプションのレジストリ エントリを使用できます。 これらのエントリは、SccServerName および SccServerPath として同じサブキーに移動します。  
  
    -   コントロール プラグのアドインのプラグインの選択] 一覧に表示される、ソースを設定したくない場合は、HideInVisualStudioregistry 入力を使用することができます [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 このエントリは、ソース管理プラグインに自動切り替えも影響します。 このエントリの用途の 1 つは、ソース管理プラグインを置換するソース管理パッケージを指定するが、プラグインのソース管理パッケージのソース管理を使用してから移行するユーザーを容易にできるようにするかどうかです。 ソース管理パッケージがインストールされている場合は、このレジストリ エントリは、非表示にするプラグインを設定します。  
  
         HideInVisualStudio は、DWORD 値であり、プラグインを非表示にする場合は 1 またはプラグインを表示する場合は 0 に設定されています。 レジストリ エントリが表示されない場合、既定の動作は、プラグインを表示するのには。  
  
    -   DisableSccManager レジストリ エントリが無効にするか、または非表示にすることできます、 **起動 \< ソース管理サーバー>** 下に通常表示されるメニュー オプション、 **ファイル** -> **ソース管理** サブメニューを選択します。 このメニューを選択するオプションを呼び出し、 [SccRunScc](../../extensibility/sccrunscc-function.md) 関数です。 ソース管理プラグインには、外部プログラムのことはできませんし、したがってすることも無効にするか、または非表示にも、 **起動** メニュー オプション。  
  
         DisableSccManager は DWORD 値が 0 に設定を有効にする、 **起動 \< ソース管理サーバー>** メニュー オプションを 1 に設定] メニューのオプションを無効にして、メニュー オプションを非表示にする 2 に設定します。 このレジストリ エントリが表示されない場合、既定の動作では、メニュー オプションを説明します。  
  
    |レジストリ エントリの例|サンプル値|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  サブキー、SourceCodeControlProvider、ソフトウェアのサブキーに HKEY_LOCAL_MACHINE キーを追加します。  
  
     このサブキーにレジストリ エントリ ProviderRegKey を手順 1. でレジストリに置かれているサブキーを表す文字列に設定してされます。 パターンは、HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey ソフトウェアを =\\*[会社名]*\\*[製品名]*します。  
  
     このサブキーのサンプルの内容を次に示します。  
  
    |レジストリ エントリ|サンプル値|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  同じサブキーとエントリ名、ソース管理プラグインが使用されますが、値が異なる場合します。  
  
4.  SourceCodeControlProvider サブキーの下で InstalledSCCProviders という名前のサブキーを作成し、そのサブキーの下の 1 つのエントリを配置します。  
  
     このエントリの名前が (同じ SCCServerName エントリに指定された値として)、プロバイダーのユーザーが判読できる名前と値が、もう一度、手順 1. で作成されたサブキー。 パターンは、HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\*[表示名]* ソフトウェアを =\\*[会社名]*\\*[製品名]*します。  
  
     例:  
  
    |レジストリ エントリの例|サンプル値|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  複数ソース管理プラグインをこの方法で登録されていることができます。 これは、どのように [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] インストールされているすべてのソース管理プラグインの API ベースのプラグインを検索します。  
  
## <a name="how-an-ide-locates-the-dll"></a>IDE が DLL を検索する方法  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE は、2 つのソースを見つける方法は、プラグイン DLL を制御します。  
  
-   既定のソース管理プラグインを検索し、それには自動的に接続します。  
  
-   検索登録されているすべてのソース管理プラグイン元となる、いずれかを選択します。  
  
 最初の方法では、DLL を検索、IDE はエントリ ProviderRegKey HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider サブキーの下で検索します。 このエントリの値は、別のサブキーを指します。 IDE は、し、その 2 つ目のサブキー HKEY_LOCAL_MACHINE の下に SccServerPath という名前のエントリを探します。 このエントリの値は、DLL を IDE を指します。  
  
> [!NOTE]
>  IDE では、相対パス (たとえば、.\NewProvider.DLL) の Dll が読み込まれません。 DLL への完全パスを指定する必要があります (たとえば、c:\Providers\NewProvider.DLL)。 これは、承認されていない、または偽装のプラグイン Dll の読み込みを実行できないようにして、IDE のセキュリティを強化します。  
  
 2 番目の方法で、DLL を検索するために、IDE がすべてのエントリの HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders サブキーは*です。* 各エントリには、名前と値があります。 IDE では、これらの名前の一覧を表示、ユーザーに*します。* 名前を選択すると、IDE は、サブキーを指している選択した名前の値を検索します。 IDE は、HKEY_LOCAL_MACHINE の下には、そのサブキーに SccServerPath という名前のエントリを探します。 そのエントリの値は、適切な DLL を IDE を指します。  
  
 ソース管理プラグインでは、DLL が見つからないのどちらの方法をサポートし、その結果、ProviderRegKey、過去の設定の上書きを設定する必要があります。 さらに重要なにする必要があります自体の一覧に追加 InstalledSccProviders ユーザーに参照を使用するには、どのソース管理プラグインの選択できるようにします。  
  
> [!NOTE]
>  として、既定のソース管理プラグイン任意のコンピューター上の 1 つだけのソース管理プラグインを登録できます HKEY_LOCAL_MACHINE キーを使用しているため (ただし、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] するソース管理プラグインに実際には、特定のソリューションを使用するかを決定できる)。 インストール プロセス中を確認するかどうかは、ソース管理プラグインが既に設定されます。その場合、ユーザーに求めます新しいソース コントロールの既定値としてインストールされているプラグインを設定するかどうか。 アンインストール中に削除しないですべてソース管理プラグインで HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider; に共通するその他のレジストリ サブキー特定のソース コード管理のサブキーだけを削除します。  
  
## <a name="how-the-ide-detects-version-1213-support"></a>IDE がバージョン 1.2 または 1.3 のサポートを検出する方法  
 方法は [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] プラグインがサポートのソース管理プラグインの API バージョン 1.2 および 1.3 機能するかどうかを検出するでしょうか。 高度な機能を宣言するには、ソース管理プラグインは、対応する関数を実装する必要があります。  
  
 1 つは、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の呼び出しによって返される値を調べ、 [SccGetVersion](../../extensibility/sccgetversion-function.md)します。 1.2 以上にする必要があります。  
  
 次に、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を調べることによって、特定の新機能がサポートされているかどうかを `lpSccCaps` の引数、 [SccInitialize](../../extensibility/sccinitialize-function.md)します。  
  
 2 つの条件が満たされる場合は、バージョン 1.2 および 1.3 ではサポート新しい関数を呼び出すことができます。  
  
## <a name="see-also"></a>参照  
 [作業の開始](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)