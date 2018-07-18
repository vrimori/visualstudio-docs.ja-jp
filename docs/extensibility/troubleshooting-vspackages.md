---
title: Vspackage のトラブルシューティング |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73c754de72238671dd10235e792c43fb6d0a1b5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146197"
---
# <a name="troubleshooting-vspackages"></a>Vspackage のトラブルシューティング
一般的な問題を VSPackage に可能性のある問題を解決するためのヒントを次に示します。  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>VSPackage のトラブルシューティングに抑えるには Visual Studio を起動  
  
-   開始[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]セーフ モードでします。  
  
     開始する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]セーフ モードでコマンド プロンプトで次のように入力します。 **devenv.exe/safemode**です。  
  
     このプロセス中に Vspackage が読み込まれていないに含まれている Vspackage を除く[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>VSPackage が読み込まれないのトラブルシューティング  
  
1.  VSPackage が、通常、実験用のレジストリ ルートを実行する登録されているレジストリ ルートを使用していることを確認します。  
  
     詳細については、次を参照してください。 [、実験用インスタンス](../extensibility/the-experimental-instance.md)です。  
  
2.  VSPackage は、実験用のレジストリ ルートで実行する対象とする場合は、実験用バージョンを実行していることを確認してください[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
     実験用バージョンを実行するには、コマンド ウィンドウで、次を入力: **devenv/rootsuffix exp**です。  
  
3.  VSPackage のレジストリ エントリを確認してください。  
  
     詳細については、次を参照してください。 [Vspackage の登録](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd)と[を管理する Vspackage](../extensibility/managing-vspackages.md)です。  
  
4.  開く、**出力**ウィンドウのインスタンスの[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を VSPackage を読み込むことが失敗しています。 VSPackage が読み込みに失敗する理由に関する情報は、そのウィンドウに表示可能性があります。  
  
    > [!NOTE]
    >  実験用バージョンを開始する場合は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]から、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) の検査、**出力**両方のバージョンのウィンドウ。  
  
5.  アクティビティ ログを調べます。  
  
     詳細については、次を参照してください。[する方法: アクティビティ ログを使用して](../extensibility/how-to-use-the-activity-log.md)です。  
  
6.  IDE によってスローされた例外の詳細についてをクリックして**例外**上、**デバッグ**メニュー、例外を有効にします。 **例外**ダイアログ ボックスでは、これに関する詳細情報を表示する例外の種類を選択します。  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>VSPackage を登録しませんのトラブルシューティング  
  
1.  VSPackage アセンブリが信頼できる場所に格納されていることを確認してください。 RegPkg は、既定の .net セキュリティ構成で、ネットワーク共有などの信頼されていないか部分的に信頼できる場所でアセンブリを登録することはできません。 警告は、ユーザーが信頼されていない場所でプロジェクトを作成するたびに表示されますが、「メッセージを表示しないこの再度」のチェック ボックスは再発を回避してこの警告を回避できます。  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>表示されていないか、コマンドをクリックすると、エラーを生成するコマンドのトラブルシューティング  
  
1.  次のコマンドを入力して、新しいまたは変更されたメニュー コマンドと、IDE 内の既存のものをマージ、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コマンド プロンプト: **devenv/rootsuffix Exp/setup**です。  
  
2.  確認して[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage の UI.dll を見つけることができます。  
  
    1.  レジストリのパッケージ セクションで、VSPackage の CLSID を見つけます。  
  
         HKLM\Software\Microsoft\Visual Studio\\*\<バージョン >* \Packages  
  
    2.  SatelliteDll サブキーによって指定されたパスが正しいことを確認します。  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>VSPackage、予期しない動作をトラブルシューティングするには  
  
1.  コード内にブレークポイントを設定します。  
  
     デバッグするために、適切な出発点には、コンス トラクターおよび初期化メソッドです。 メニュー コマンドなど、評価する領域にブレークポイントを設定することもできます。 ブレークポイントを有効にするには、デバッガーの下で実行する必要があります。  
  
    1.  **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
    2.  **プロパティ ページ**ダイアログ ボックスで、**デバッグ**タブです。  
  
    3.  **コマンドライン引数**ボックスに、開発環境のルートのサフィックスを入力する、VSPackage が対象です。 たとえば、試験的ビルドを選択するには、次のように入力します。: **RootSuffix Exp**です。  
  
    4.  **デバッグ** メニューのをクリックして**デバッグの開始** F5 キーを押します。  
  
        > [!NOTE]
        >  プロジェクトをデバッグする場合は、作成または、プロジェクトの既存のインスタンスを読み込むようになりました。  
  
2.  アクティビティ ログを使用します。  
  
     主要なポイントでのアクティビティ ログに情報を記述して、VSPackage の動作をトレースします。 この手法は、小売り業の環境で VSPackage を実行するときに便利です。 詳細については、次を参照してください。[する方法: アクティビティ ログを使用して](../extensibility/how-to-use-the-activity-log.md)です。  
  
3.  パブリック シンボルを使用します。  
  
     デバッグ中に、読みやすさを向上するには、デバッガーにシンボルを割り当てることができます。  
  
    1.  **ツール/オプション** メニューに移動し、**デバッグ/シンボル** ダイアログ ボックス。  
  
    2.  この追加**シンボル (.pdb) ファイルの位置**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  パフォーマンスを向上させるには、たとえばシンボル キャッシュ フォルダーを指定します。  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>不足している VSPackage またはその依存関係の 1 つのトラブルシューティング  
  
1.  マネージ コードの場合は、参照パスが正しいことを確認します。  
  
    1.  **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
    2.  選択、**参照** タブで、**プロパティ ページ** ダイアログ ボックスと、必ずすべてのパスが正しい。 また、使用することができます、**オブジェクト ブラウザー**の参照先のオブジェクトをブラウズします。  
  
         マネージ コードを使用できます、 [Fuslogvw.exe (アセンブリ バインディング ログ ビューアー)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer)失敗したアセンブリの読み込みの詳細を表示します。  
  
2.  アンマネージ コードの検索で、VSPackage の CLSID、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID レジストリ ノード。  
  
     HKLM\Software\Microsoft\Visual Studio\\*\<バージョン >* \CLSID  
  
 InprocServer32 エントリの VSPackage の dll の正しいパスがあることを確認してください。  
  
## <a name="see-also"></a>関連項目  
 [VSPackage](../extensibility/internals/vspackages.md)