---
title: "サイド バイ サイドのファイルの関連付けを管理します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "既定の設定、動詞"
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# サイド バイ サイドのファイルの関連付けを管理します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackage がファイルの関連付けを提供するファイルを開くに [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の特定のバージョンを起動する必要のあるインストールの処理方法を決定する必要があります。  互換性のない形式は問題を使用します。  
  
 ユーザーは既存のファイルをデータを失うことで新しいバージョンで読み込むために以前のバージョンと互換性があると新しいバージョンの製品が必要になります。  理想的にはVSPackage は以前のバージョンの形式の読み込みと保存できます。  これも当てはまらない場合VSPackage の新しいバージョンへのファイル形式にアップグレードすることを指定します。  この方法にはやアップグレードされたファイルが旧バージョンで開くことができません。  
  
 形式は互換性するとこの問題を回避するには拡張子を変更できます。  たとえばVSPackage Version 1 では拡張子を使用 .mypkg10 バージョン 2.mypkg20 拡張子を使用できます。  この違いは特定のファイルを開く VSPackage を指定します。  以前の拡張子に関連付けられているプログラムの一覧に新しい VSPackage を追加するとユーザーはファイルを右クリックし新しい VSPackage で開くことができます。  この時点でVSPackageファイルが新しいファイル形式にアップグレードしたりファイルを開きVSPackage の以前のバージョンとの互換性を維持することを指定できます。  
  
> [!NOTE]
>  これらの方法を組み合わせることもできます。  たとえば古いファイルを読み込んで下位互換性を提供しユーザーが文書を保存するとファイル形式にアップグレードすることを指定できます。  
  
## 問題の発生  
 複数の side\-by\-side VSPackage に同じ拡張子を使用して拡張子に関連付けられた [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] バージョンを選択する必要があります。  2 種類の方法を示します :  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の最新バージョンのファイルをインストールしたユーザーのコンピューターでを開きます。  
  
     この方法ではインストーラーは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の最新バージョンを判断しファイルの関連付けに作成されたレジストリ エントリに含めるを行います。  Windows インストーラー パッケージでは[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の最新バージョンを示すプロパティを設定するカスタム動作を追加できます。  
  
    > [!NOTE]
    >  ここで「最新の\) 」は 「サポートされているバージョン」。これらのインストーラーのエントリが自動的に [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の今後のリリースを検出しません。  [システム要件の検出](../extensibility/internals/detecting-system-requirements.md) と [インストール後に実行する必要がありますコマンド](../extensibility/internals/commands-that-must-be-run-after-installation.md) のエントリはここで示したものと似ています [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のバージョンをサポートする必要があります。  
  
     CustomAction テーブルの次の行は [インストール後に実行する必要がありますコマンド](../extensibility/internals/commands-that-must-be-run-after-installation.md) で説明する AppSearch と RegLocator の表に設定するプロパティに DEVENV\_EXE\_LATEST のプロパティを設定します。  InstallExecuteSequence のテーブルの行が実行されるシーケンスのカスタム動作を早期スケジュールします。  条件の列の値はロジックを処理します :  
  
    -   は唯一の現在のバージョンの Visual Studio .NET 2002 では最新バージョンです。  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がある場合にのみVisual Studio .NET 2003 では最新バージョンです。  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は唯一の現在のバージョンの最新バージョンです。  
  
     最終的には DEVENV\_EXE\_LATEST が devenv.exe の最新バージョンのパスを含む。  
  
    ### Visual Studio の最新バージョンを決定する CustomAction テーブルの行  
  
    |動作|種類|ソース|Target|  
    |--------|--------|---------|------------|  
    |CA\_SetDevenvLatest\_2002|51|DEVENV\_EXE\_LATEST|\[入力\] DEVENV\_EXE\_2002|  
    |CA\_SetDevenvLatest\_2003|51|DEVENV\_EXE\_LATEST|\[入力\] DEVENV\_EXE\_2003|  
    |CA\_SetDevenvLatest\_2005|51|DEVENV\_EXE\_LATEST|\[入力\] DEVENV\_EXE\_2005|  
  
    ### Visual Studio の最新バージョンを決定 InstallExecuteSequence テーブルの行  
  
    |動作|状態|シーケンス|  
    |--------|--------|-----------|  
    |CA\_SetDevenvLatest\_2002|DEVENV\_EXE\_2002\(または\) DEVENV\_EXE\_2005 DEVENV\_EXE\_2003|410|  
    |CA\_SetDevenvLatest\_2003|DEVENV\_EXE\_2003DEVENV\_EXE\_2005|420|  
    |CA\_SetDevenvLatest\_2005|DEVENV\_EXE\_2005|430|  
  
     Windows インストーラー パッケージのレジストリの表に *ProgID*HKEY\_CLASSES\_ROOT \\ \\ Shell \\ \\ を表示するために DEVENV\_EXE\_LATEST のプロパティを使用してコマンド キーの既定値\]\[DEVENV\_EXE\_LATEST 「 %1 " は  
  
-   VSPackage で使用できるバージョンのが最適な選択できる共有ランチャー プログラムを実行します。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の開発者はソリューション内の複数の複雑な書式の要件を行う場合はこの方法を選択し[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のバージョンの結果を返します。  この方法では拡張子として起動プログラムのハンドラーを登録します。  起動ツールはファイルを確認し[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のバージョンを VSPackage が特定のファイルを処理できるかを決定します。  たとえばユーザーが VSPackage の特定のバージョンで最後に保存されたファイルを開くとが起動 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のバージョンのVSPackage を呼び出すことができます。  さらに常に最新バージョンが最初に起動ツールを構成できます。  起動ページではユーザーがファイルの形式をアップグレードするように要求できます。  ファイルの形式にはバージョン番号が含まれている場合起動は形式をインストールする VSPackage を一つ以上より後であるバージョンの場合はユーザーに通知できます。  
  
     起動にはVSPackage のすべてのバージョンで共有される Windows インストーラーのコンポーネントが必要です。  このプロセスにはVSPackage のすべてのバージョンがインストールされるまで常に最新バージョンがインストールされ削除されています。  このようにVSPackage の 1 種類のバージョンがインストールされていても起動アンマネージ コンポーネントのファイルの関連付けやそのほかのレジストリ エントリは維持されます。  
  
## アンマネージ インストールとファイルの関連付け  
 ファイルの関連付けのレジストリ エントリを書き込みますVSPackage をインストールするとファイルの関連付けを削除します。  したがって拡張子に関連するプログラムはありません。  Windows インストーラーではVSPackage のインストール時に追加したレジストリ エントリを 「復元されません」。  ユーザーのファイルの関連付けを修正する方法を示します :  
  
-   前に説明したように起動共有コンポーネントを使用します。  
  
-   ユーザーがファイルの関連付けを所有しユーザーがする VSPackage のバージョンの修復を実行するように指示します。  
  
-   適切なレジストリ エントリを次別の実行可能プログラムを提供します。  
  
-   ユーザーがファイルの関連付けを選択し消失関連付けをクリアできるダイアログ ボックスまたは構成オプション ページを提供します。  ユーザーにインストール後に実行するように指示します。  
  
## 参照  
 [サイド バイ サイド配置のファイル名拡張子を登録します。](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [ファイル名拡張子の動詞を登録します。](../extensibility/registering-verbs-for-file-name-extensions.md)