---
title: "Vspackage のトラブルシューティング |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 933b0177e3287717b2cfb900996b947db7034ee5
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshooting-vspackages"></a>Vspackage のトラブルシューティング
一般的な問題、VSPackage に可能性のあるし、問題を解決するためのヒントを次に示します。  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>により、Visual Studio を起動する VSPackage をトラブルシューティングするには  
  
-   開始[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]セーフ モードにします。  
  
     開始する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]セーフ モードでコマンド プロンプトで次のように入力します。 **devenv.exe/safemode**します。  
  
     この処理中に VSPackages は読み込まれませんに含まれている Vspackage を除く[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>VSPackage が読み込まれないのトラブルシューティング  
  
1.  VSPackage が実行するには通常実験用のレジストリ ルート登録されているレジストリ ルートを使用していることを確認します。  
  
     詳細については、次を参照してください。[の実験用インスタンス](../extensibility/the-experimental-instance.md)します。  
  
2.  VSPackage が実験用のレジストリ ルートで実行する対象となる場合のテスト バージョンを実行していること確認[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。  
  
     実験用のバージョンを実行するには、コマンド ウィンドウで、次を入力: **devenv/rootsuffix exp**します。  
  
3.  VSPackage のレジストリ エントリを確認してください。  
  
     詳細については、次を参照してください。[登録 VSPackages](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd)と[管理 VSPackages](../extensibility/managing-vspackages.md)します。  
  
4.  開いている、**出力**ウィンドウのインスタンスの[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を VSPackage を読み込むことが失敗しています。 VSPackage が読み込みに失敗した理由に関する情報は、そのウィンドウに表示可能性があります。  
  
    > [!NOTE]
    >  実験用のバージョンを開始する場合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]から、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) の検査、**出力**両方のバージョンのウィンドウです。  
  
5.  アクティビティ ログを調べます。  
  
     詳細については、次を参照してください。[方法:、動作状況ログを使用して](../extensibility/how-to-use-the-activity-log.md)します。  
  
6.  クリックして、IDE によってスローされた例外の詳細については、**例外**上、**デバッグ**メニュー、例外を有効にします。 **例外**ダイアログ ボックスでは、に関する詳細情報を表示する例外の種類を選択します。  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>登録されない VSPackage をトラブルシューティングするには  
  
1.  VSPackage のアセンブリが信頼できる場所に格納されていることを確認します。 RegPkg は、既定の .net セキュリティの構成でネットワーク共有などの信頼されていないか部分的に信頼された場所にアセンブリを登録することはできません。 警告は、ユーザーが信頼されていない場所でプロジェクトを作成するときに表示されますが、「メッセージを表示しないこのもう一度」チェック ボックスは再発を回避してこの警告を回避できます。  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>表示されていない、またはコマンドをクリックすると、エラーが発生する、コマンドのトラブルシューティング  
  
1.  次のコマンドを入力して、新しいまたは変更されたメニュー コマンドと、IDE 内の既存のものをマージ、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コマンド プロンプト: **devenv/rootsuffix Exp/setup**します。  
  
2.  確認して[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage の UI.dll を見つけることができます。  
  
    1.  VSPackage の CLSID をレジストリのパッケージ セクションにあります。  
  
         HKLM\Software\Microsoft\Visual Studio\\*\<バージョン >*\Packages  
  
    2.  SatelliteDll サブキーで指定されたパスが正しいことを確認します。  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>予期しない動作を VSPackage のトラブルシューティング  
  
1.  コード内にブレークポイントを設定します。  
  
     デバッグするための適切な出発点には、コンス トラクターおよび初期化メソッドです。 メニュー コマンドなど、評価する領域にブレークポイントを設定することもできます。 ブレークポイントを有効にするには、デバッガーの下で実行する必要があります。  
  
    1.  **プロジェクト** メニューのをクリックして**プロパティ**します。  
  
    2.  **プロパティ ページ**ダイアログ ボックスで、**デバッグ** タブをクリックします。  
  
    3.  **コマンドライン引数**ボックスに、開発環境のルートのサフィックスを入力する、vs パッケージが対象です。 たとえば、実験用ビルドを選択するには、次のように入力します。: **RootSuffix Exp**します。  
  
    4.  **デバッグ** メニューのをクリックして**デバッグ開始** F5 キーを押します。  
  
        > [!NOTE]
        >  プロジェクトをデバッグする場合は、作成するか、プロジェクトの既存のインスタンスを読み込むようになりました。  
  
2.  動作状況ログを使用します。  
  
     主要なポイントで、動作状況ログに情報を書き込むことによって、VSPackage 動作をトレースします。 VSPackage を小売環境で実行すると、この手法は特に便利です。 詳細については、次を参照してください。[方法:、動作状況ログを使用して](../extensibility/how-to-use-the-activity-log.md)します。  
  
3.  パブリック シンボルを使用します。  
  
     デバッグ中に、読みやすさを向上するには、デバッガーにシンボルを割り当てることができます。  
  
    1.  **ツール/オプション** メニューの に移動し、**デバッグ/シンボル** ダイアログ ボックス。  
  
    2.  この追加**シンボル ファイル (.pdb) の位置**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  パフォーマンスを向上させるには、たとえばシンボル キャッシュ フォルダーを指定します。  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>不足している VSPackage またはその依存関係の&1; つのトラブルシューティング  
  
1.  マネージ コード参照のパスが正しいことを確認します。  
  
    1.  **プロジェクト** メニューのをクリックして**プロパティ**します。  
  
    2.  選択、**参照** タブで、**プロパティ ページ**のすべてのパスが正しい ダイアログ ボックスを確認します。 また、使用することができます、**オブジェクト ブラウザー**の参照先のオブジェクトをブラウズします。  
  
         マネージ コードを使用することができます、 [Fuslogvw.exe (アセンブリ バインディング ログ ビューアー)](http://msdn.microsoft.com/Library/e32fa443-0778-4cc3-bf36-5c8ea297d296)障害が発生したアセンブリの読み込みの詳細を表示します。  
  
2.  アンマネージ コードの検索に VSPackage の CLSID、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID レジストリ ノード。  
  
     HKLM\Software\Microsoft\Visual Studio\\*\<バージョン >*\CLSID  
  
 InprocServer32 エントリがある VSPackage dll のパスが正しいことを確認します。  
  
## <a name="see-also"></a>関連項目  
 [Vspackages にあります。](../extensibility/internals/vspackages.md)
