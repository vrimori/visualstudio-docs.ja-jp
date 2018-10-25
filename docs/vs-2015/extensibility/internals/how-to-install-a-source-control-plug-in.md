---
title: '方法: ソース管理プラグインのインストール |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5f8c442aec21042faa4aa992dcdefc4f9d2ad335
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812986"
---
# <a name="how-to-install-a-source-control-plug-in"></a>方法: ソース管理プラグインのインストール
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ソース管理プラグインを作成するには、3 つの手順が含まれます。  
  
1.  このドキュメントのソース管理プラグイン API リファレンスのセクションで定義された関数では、DLL を作成します。  
  
2.  ソース管理プラグイン API 定義の関数を実装します。 ときに[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]呼び出し、インターフェイスとダイアログ ボックスから使用できるように、プラグイン。  
  
3.  DLL を登録するには、適切なレジストリ エントリを作成します。  
  
## <a name="integration-with-visual-studio"></a>Visual Studio との統合  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ソース管理プラグイン API に準拠するソース管理プラグインをサポートしています。  
  
### <a name="registering-the-source-control-plug-in"></a>ソース管理プラグインを登録します。  
 ソースをまず見つける必要があります、実行中の統合開発環境 (IDE) は、ソース管理システムを呼び出すことが、前に、API をエクスポートするプラグインの DLL を制御します。  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>ソース管理プラグインの DLL を登録するには  
  
1.  ソフトウェアのサブキー、製品名のサブキーを続けて、会社名のサブキーを指定するには、HKEY_LOCAL_MACHINE キーの下の 2 つのエントリを追加します。 パターンは、hkey_local_machine \software\\ *[会社名]*\\ *[製品名]*\\ *[entry]* = 値。 SCCServerName と SCCServerPath、2 つのエントリが常に呼び出されます。 それぞれは、通常の文字列です。  
  
     たとえば、会社名が Microsoft と、ソース管理製品である場合の名前は SourceSafe、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe するレジストリのパスとなります。 このサブキー、SCCServerName、最初のエントリは、製品の名前を付け、ユーザーが判読できる文字列です。 2 番目のエントリでは、SCCServerPath は、ソースへの完全パスに接続する IDE プラグインの DLL を制御します。 レジストリ エントリの例を次に示します。  
  
    |レジストリ エントリの例|サンプル値|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  SCCServerPath は、SourceSafe プラグインへの完全パスです。 ソース管理プラグインでは、同じレジストリ エントリのパスが異なる会社と製品の名前を使用します。  
  
2.  ソース管理プラグインの動作を変更するのには、次のオプションのレジストリ エントリを使用できます。 これらのエントリは、SccServerName と SccServerPath として同じサブキーに移動します。  
  
    -   コントロールのプラグ-でのプラグインの選択リストに表示される、ソースを設定したくない場合、HideInVisualStudioregistry エントリを使用できます[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 ソース管理プラグインへの自動切り替えは、このエントリによっても影響します。 このエントリの用途の 1 つは、ソース管理プラグインを置換するソース管理パッケージを指定するが、ソース管理プラグインのソース管理パッケージを使用してから移行するユーザーを容易にできるようにするかどうかは。 ソース管理パッケージがインストールされている場合は、プラグインを非表示にこのレジストリ エントリを設定します。  
  
         HideInVisualStudio は、DWORD 値であり、プラグインを非表示にする 1 またはプラグインを表示するには 0 に設定されています。 レジストリ エントリが表示されない場合、既定の動作は、プラグインを表示するのには。  
  
    -   DisableSccManager のレジストリ エントリを無効にするか、または非表示に使用できる、**起動\<ソース管理サーバー >** 通常下に表示されるメニュー オプション、**ファイル** ->  **ソース管理** をクリックします。 このメニューを選択するオプションを呼び出し、 [SccRunScc](../../extensibility/sccrunscc-function.md)関数。 外部プログラムのソース管理プラグインでは対応していないとする可能性がありますを無効または非表示にもそのため、**起動**メニュー オプション。  
  
         DisableSccManager は DWORD 値が 0 に設定を有効にする、**起動\<ソース管理サーバー >** メニュー オプションを 1 に設定 メニュー オプションを無効にして、メニュー オプションを非表示には 2 に設定します。 このレジストリ エントリが表示されない場合、既定の動作では、メニュー オプションを説明します。  
  
    |レジストリ エントリの例|サンプル値|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  サブキー、SourceCodeControlProvider、ソフトウェアのサブキー HKEY_LOCAL_MACHINE キーの下に追加します。  
  
     このサブキーは、レジストリ エントリ ProviderRegKey を手順 1. でレジストリに配置したサブキーを表す文字列に設定してされます。 パターンは、HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey ソフトウェア =\\ *[会社名]*\\ *[製品名]* します。  
  
     このサブキーのサンプルの内容を次に示します。  
  
    |レジストリ エントリ|サンプル値|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  ソース管理プラグインは、同じサブキーとエントリの名前を使用してが異なる値になります。  
  
4.  SourceCodeControlProvider サブキー InstalledSCCProviders をという名前のサブキーを作成し、そのサブキーの下の 1 つのエントリを配置します。  
  
     このエントリの名前が (同じ SCCServerName エントリに指定された値)、プロバイダーのユーザーが判読できる名前と値が、もう一度、手順 1. で作成されたサブキー。 パターンは、HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\ *[表示名]* ソフトウェア =\\ *[会社名]* \\ *[製品名]* します。  
  
     例えば:  
  
    |レジストリ エントリの例|サンプル値|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  複数ソース管理プラグインをこの方法で登録されていることができます。 これは、どのように[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]インストールされているすべてのソース管理プラグイン API ベースのプラグインを検索します。  
  
## <a name="how-an-ide-locates-the-dll"></a>IDE が DLL を検索する方法  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE は、2 つのソースを見つける方法は、プラグインの DLL を制御します。  
  
- 既定のソース管理プラグインを検索しをサイレント モードで接続します。  
  
- 検索登録されているすべてのソース管理プラグインを元のユーザーが 1 つ選択しました。  
  
  最初の方法で、DLL を検索するには、IDE はエントリ ProviderRegKey HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider サブキーの下で検索します。 このエントリの値は、別のサブキーを指します。 IDE は、その 2 つ目のサブキー HKEY_LOCAL_MACHINE の下で SccServerPath をという名前のエントリを検索します。 このエントリの値は、DLL を IDE を指します。  
  
> [!NOTE]
>  IDE では、相対パス (たとえば、.\NewProvider.DLL) から Dll が読み込まれません。 DLL への完全なパスを指定する必要があります (たとえば、c:\Providers\NewProvider.DLL)。 これは、承認されていないか、権限を借用したプラグインの Dll の読み込みを防止することで、IDE のセキュリティを強化します。  
  
 2 番目の方法で、DLL を検索する IDE ですべてのエントリの HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders サブキーの下で検索<em>します。</em> 各エントリは、名前と値があります。 IDE では、これらの名前の一覧を表示、ユーザーに<em>します。</em> ユーザーが 名前を IDE は、サブキーを指している選択した名前の値を検索します。 IDE は、そのサブキー hkey_local_machine SccServerPath をという名前のエントリを探します。 そのエントリの値は、適切な DLL を IDE を指します。  
  
 ソース管理プラグインは、DLL が見つからないのどちらの方法をサポートして、その結果、ProviderRegKey、過去の設定の上書きを設定する必要があります。 さらに、その必要があります自体の一覧に追加 InstalledSccProviders のため、ユーザーが使用するには、ソース管理プラグインの選択を持つことができます。  
  
> [!NOTE]
>  指定されたコンピューターでプラグイン既定のソース管理として 1 つだけのソース管理プラグインを登録できます HKEY_LOCAL_MACHINE キーを使用しているため (ただし、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]どのソース管理プラグインの実際に使用するかを決定できる、特定のソリューションです。) インストール プロセス中にかどうか、ソース管理プラグインは既に設定; を確認します。そうである場合、ユーザーに求めます新しいソース コントロールの既定値としてインストールされているプラグインを設定するかどうか。 アンインストール-インストール中に削除しないでくださいすべてソース管理プラグインで HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider; に共通するその他のレジストリ サブキー特定の SCC サブキーのみを削除します。  
  
## <a name="how-the-ide-detects-version-1213-support"></a>IDE はバージョン 1.2 と 1.3 のサポートを検出する方法  
 方法は[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]プラグインがサポートのソース管理プラグイン API バージョン 1.2 と 1.3 機能かどうかを検出しますか? 高度な機能を宣言するには、ソース管理プラグインは対応する関数を実装する必要があります。  
  
 まず、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]呼び出しによって返される値をチェック、 [SccGetVersion](../../extensibility/sccgetversion-function.md)します。 1.2 以上があります。  
  
 次に、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]を調べることで、特定の新しい機能がサポートされているかどうか、`lpSccCaps`の引数、 [SccInitialize](../../extensibility/sccinitialize-function.md)します。  
  
 両方の条件が満たされた場合は、バージョン 1.2 および 1.3 でサポートされる新しい関数を呼び出すことできます。  
  
## <a name="see-also"></a>関連項目  
 [はじめに](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

