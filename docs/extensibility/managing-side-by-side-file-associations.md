---
title: サイド バイ サイドのファイルの関連付けの管理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e9144125786e7aa5f2a70823a033d49ac3fa2990
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146807"
---
# <a name="managing-side-by-side-file-associations"></a>サイド バイ サイドのファイルの関連付けを管理します。
VSPackage では、ファイルの関連付けを提供する場合をサイド バイ サイド インストールを処理する方法を決定する必要がありますの特定のバージョン[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ファイルを開くに呼び出す必要があります。 互換性のないファイル形式は複合問題です。  
  
 ユーザーは、データを失うことがなく、新しいバージョンで既存のファイルを読み込むことができるように、以前のバージョンに合うように、製品の新しいバージョンを期待します。 理想的には、VSPackage が両方を読み込んで以前のバージョンのファイル形式を保存します。 True でない場合は、ファイル形式を VSPackage の新しいバージョンにアップグレードを提案する必要があります。 このアプローチの欠点は、以前のバージョンで、アップグレードされたファイルを開くことができないことです。  
  
 この問題を回避するのには、ファイル形式が互換性のないようになったときの拡張機能を変更できます。 たとえば、拡張機能、.mypkg10、およびバージョン 2 は、拡張機能を使用でした、VSPackage のバージョン 1 を使用 .mypkg20 です。 この違いは、特定のファイルを開き、VSPackage を識別します。 古い拡張子に関連付けられているプログラムの一覧に新しい Vspackage を追加する場合に、ファイルを右クリックし、新しい VSPackage で開くことを選択します。 その時点では、VSPackage は、ファイルを新しい形式にアップグレードまたはファイルを開き、VSPackage の旧バージョンとの互換性を維持を提供できます。  
  
> [!NOTE]
>  これらのアプローチを組み合わせることができます。 たとえば、古いファイルを読み込んで旧バージョンとの互換性を提供し、ファイル形式をアップグレードして、ユーザーがそれを保存するときに提供できます。  
  
## <a name="facing-the-problem"></a>この問題に直面しています。  
 バージョンを選択する必要があるする場合は、同じ拡張機能を使用する複数のサイド バイ サイド Vspackage、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]拡張機能に関連付けられています。 2 つの方法を次に示します。  
  
-   最新バージョンのファイルを開く[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ユーザーのコンピューターにインストールします。  
  
     この方法では、インストーラーがの最新バージョンを判断する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ファイルの関連付け用に記述されたレジストリ エントリで含むとします。 Windows インストーラー パッケージでの最新バージョンを示すプロパティを設定するカスタム アクションを含めることができます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
    > [!NOTE]
    >  このコンテキストでは、「最新」は"サポートされる最新バージョンです" これらのインストーラーのエントリは今後のリリースを自動的に検出されない[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 内のエントリ[システム要件の検出](../extensibility/internals/detecting-system-requirements.md)し、[コマンドする必要がある実行後にインストール](../extensibility/internals/commands-that-must-be-run-after-installation.md)はここに示すものに似ておりの他のバージョンをサポートするために必要な[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。  
  
     CustomAction テーブル内の次の行が、AppSearch によって設定されたプロパティである DEVENV_EXE_LATEST プロパティを設定し、で説明した RegLocator テーブル[コマンドする必要がある実行後にインストール](../extensibility/internals/commands-that-must-be-run-after-installation.md)です。 InstallExecuteSequence テーブル内の行は、execute シーケンスの早い段階でカスタム アクションをスケジュールします。 ロジックの作業を行うための条件列の値:  
  
    -   Visual Studio .NET 2002 は、だけ現在のバージョンである場合、最新のバージョンです。  
  
    -   のみ存在する場合は、最新バージョンを visual Studio .NET 2003 であると[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]は存在しません。  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のみの現在のバージョンである場合、最新のバージョンです。  
  
     最終的な結果は、DEVENV_EXE_LATEST に最新バージョンの devenv.exe のパスが含まれているです。  
  
    ### <a name="customaction-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Visual Studio の最新バージョンを決定する CustomAction テーブル行  
  
    |アクション|型|ソース|ターゲット|  
    |------------|----------|------------|------------|  
    |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|  
    |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|  
    |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|  
  
    ### <a name="installexecutesequence-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Visual Studio の最新バージョンを決定する InstallExecuteSequence テーブル行  
  
    |アクション|条件|シーケンス|  
    |------------|---------------|--------------|  
    |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 および NOT (DEVENV_EXE_2003 または DEVENV_EXE_2005)|410|  
    |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 と DEVENV_EXE_2005 されません。|420|  
    |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|  
  
     Windows インストーラー パッケージのレジストリの表に DEVENV_EXE_LATEST プロパティを使用するには、HKEY_CLASSES_ROOT に書き込む*ProgId*ShellOpenCommand キーの既定値、[DEVENV_EXE_LATEST]「1%」  
  
-   使用可能な VSPackage のバージョンから最適な選択できるようにする共有ランチャー プログラムを実行します。  
  
     開発者[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソリューションおよびプロジェクトの多くのバージョンに起因するは、複数の形式の複雑な要件を処理するには、この方法を選択[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 この方法では、拡張機能ハンドラーとしてランチャー プログラムを登録します。 起動プログラムがファイルをチェックしのバージョンを決定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]と VSPackage は、その特定のファイルを処理できます。 たとえば場合、VSPackage の特定のバージョンによって最後に保存するファイルを開くと、起動プログラムで起動できますその VSPackage の一致するバージョン[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 さらに、ユーザーは、常に最新バージョンを開始する起動プログラムを構成する可能性があります。 ランチャーもでしたするようユーザーに、ファイルの形式にアップグレードします。 ファイルの形式には、バージョン番号が含まれている場合、ランチャーだった場合に、ユーザーが 1 つ以上インストールされている Vspackage のよりも後のバージョンからのファイル形式です。  
  
     起動プログラムは、VSPackage のすべてのバージョンで共有されている Windows インストーラー コンポーネントでなければなりません。 このプロセスにより、最新バージョンが常にインストールされているし、VSPackage のすべてのバージョンがアンインストールされるまでは削除されません。 これにより、ファイルの関連付けとランチャ コンポーネントの場合は、他のレジストリ エントリは保持されます、VSPackage の 1 つのバージョンをアンインストールした場合でもです。  
  
## <a name="uninstall-and-file-associations"></a>アンインストールして、ファイルの関連付け  
 ファイルの関連付けのレジストリ エントリを書き込みます、VSPackage をアンインストールするには、ファイルの関連付けを削除します。 したがって、拡張機能では、関連付けられているプログラムはありません。 Windows インストーラーはありません"recover"、VSPackage がインストールされているときに追加されたレジストリ エントリ。 ユーザーのファイルの関連付けを修正する方法を次に示します。  
  
-   前述したように共有ランチャ コンポーネントを使用します。  
  
-   ユーザーがファイルの関連付けを所有する、VSPackage のバージョンの修復を実行するユーザーに指示します。  
  
-   適切なレジストリ エントリを書き換える独立した実行可能プログラムを提供します。  
  
-   ユーザーがファイルの関連付けを選択し、失われたアソシエーションを再利用できる構成オプション ページまたはダイアログ ボックスを提供します。 アンインストール後に実行するユーザーに指示します。  
  
## <a name="see-also"></a>関連項目  
 [サイド バイ サイド配置のファイル名拡張子を登録します。](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [ファイル名拡張子の動詞を登録する](../extensibility/registering-verbs-for-file-name-extensions.md)