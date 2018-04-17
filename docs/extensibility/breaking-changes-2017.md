---
title: Visual Studio 2017 拡張機能における重大な変更 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/09/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 068b71a78149bb1c52e28bc47245d0dc888496bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Visual Studio 2017 機能拡張の変更

Visual Studio 2017 では、Visual Studio のユーザーシステムへの影響を軽減させる[高速で軽量な Visual Studio インストール エクスペリエンス](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer)を提供するとともに、インストールされるワークロードと機能をユーザーが幅広く選択することを可能にしています。 これらの機能強化をサポートするため、機能拡張モデルに変更を加え、Visual Studio の拡張性にいくつかの重大な変更を行いました。 このドキュメントでは、これらの変更に関する技術的な詳細とその対処方法について説明します。 一部の情報は特定の時点の実装の詳細であり、後に変更される可能性がありますのでご注意ください。

## <a name="changes-affecting-vsix-format-and-installation"></a>VSIX 形式とインストールに影響のある変更

軽量インストール エクスペリエンスをサポートするために VSIX v3 (バージョン 3) 形式を導入しています。

VSIX 形式における変更は次のとおりです:

* セットアップの前提条件の宣言。 Visual Studio の軽量で、高速なインストールを実現するため、 インストーラーはより多くの構成オプションをユーザーへ提供するようになりました。 その結果、拡張機能によって必要とされる機能とコンポーネントがインストールされていることを確かめるために、拡張機能はその依存関係を宣言する必要があります。
  * Visual Studio 2017 インストーラーは、拡張機能のインストールの過程で、必要なコンポーネントを取得し、自動的なインストールをユーザーに提供します。
  * 新しい VSIX v3 形式を使用せずに構築された拡張機能をインストールしようとするとき、ユーザーは警告を受けるようになります。例え、拡張機能のマニフェストで 15.0 のバージョンを対象とするとマークされている場合でも同様です。
* VSIX 形式の機能を強化します。 サイド バイ サイド インストールをもサポートする Visual Studio の[影響の少ないインストール](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install)で提供するため、ほとんどの構成データはシステム レジストリに保存されなくなり、Visual Studio 固有のアセンブリが GAC から取り除かれました。 また VSIX 形式と VSIX インストールエンジンの機能が強化されたため、一部のインストールの種類においては、MSI や EXE の代わりにそれらの機能を使用して拡張機能をインストールできるようになりました。

  新しい機能は次のとおりです。

  * 指定した Visual Studio インスタンスへの登録。
  * [拡張フォルダー](set-install-root.md)外部でのインストール。
  * プロセッサ アーキテクチャの検出。
  * 言語で区切られた言語パックの依存関係。
  * [NGEN サポート](ngen-support.md)を使用したインストール。

## <a name="building-an-extension-for-visual-studio-2017"></a>Visual Studio 2017 用拡張機能の構築

新しい VSIX v3 マニフェスト形式を作成するためのデザイナー ツールは、現在 Visual Studio 2017 で使用できます。 デザイナー ツールの使用に関する詳細や、 VSIX v3 拡張機能を開発するためのプロジェクトおよびマニフェストの手動アップデートに関する詳細については、関連ドキュメント [How to: Migrate Extensibility Projects to Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)(方法: 機能拡張プロジェクトを Visual Studio 2017 に移行する) を参照してください。

## <a name="change-visual-studio-user-data-path"></a>変更: Visual Studio ユーザー データ パス

これまで Visual Studio の各メジャー リリースは 1 つのコンピューターにつき 1 つまでしかインストールすることができませんでした。 Visual Studio 2017 ではサイド バイ サイド インストールをサポートするために、複数の Visual Studio ユーザー データ パスをユーザーのコンピューターに存在させることができます。

Visual Studio プロセスの内部で実行されているコードは Visual Studio の設定マネージャーを使用するように更新する必要があります。 Visual Studio プロセスの外部で実行されているコードは [このガイダンスに従って](locating-visual-studio.md) 特定の Visual Studio インストールのユーザー パスを検索することができます。

## <a name="change-global-assembly-cache-gac"></a>変更: グローバル アセンブリ キャッシュ (GAC)

ほとんどの Visual Studio コア アセンブリは GAC にインストールされません。 Visual Studio のプロセスで実行されるコードはまだ実行時に必要なアセンブリを検出できるように、次の変更が行われました。

> [!NOTE]
> [INSTALLDIR] Visual Studio のインストールのルート ディレクトリを参照して次に示します。 自動的に、この設定が、展開のカスタム コードを記述するをお読みくださいは VSIXInstaller.exe [Visual Studio の検索](locating-visual-studio.md)です。

* アセンブリを GAC にインストールされただけの:
  * [INSTALLDIR] \Common7\IDE にこれらのアセンブリがインストールされるようになりました\,[INSTALLDIR] \Common7\IDE\PublicAssemblies または [INSTALLDIR] \Common7\IDE\PrivateAssemblies です。 これらのフォルダーは、Visual Studio プロセスのプローブ パスの一部です。
* 非プローブ パスに、GAC にインストールされたアセンブリの場合:
  * GAC 内のコピーは、セットアップから削除されました。
  * アセンブリのコードの基本エントリを指定する .pkgdef ファイルが追加されました。

    例:
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    実行時に、Visual Studio pkgdef サブシステムがマージされます ([VSAPPDATA]\devenv.exe.config) Visual Studio プロセスのランタイム構成ファイルにこれらのエントリとして[`<codeBase>`](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx)要素。 これは、パスがプローブによる検索しないため、Visual Studio プロセスが、アセンブリを検索することをお勧めします。

### <a name="reacting-to-this-breaking-change"></a>この重要な変更に反応します。

* 場合は、拡張機能は、Visual Studio プロセス内で実行しています。
  * コードは、Visual Studio コア アセンブリを検索することができます。
  * 必要に応じて、アセンブリへのパスを指定する .pkgdef ファイルを使用してください。
* 場合は、拡張機能は Visual Studio のプロセスの外部で実行しています。
  * [INSTALLDIR] \Common7\IDE Visual Studio コア アセンブリを探してを検討してください\,[INSTALLDIR] \Common7\IDE\PublicAssemblies または構成ファイルまたはアセンブリの競合回避モジュールを使用して、[INSTALLDIR] \Common7\IDE\PrivateAssemblies です。

## <a name="change-reduce-registry-impact"></a>レジストリの影響の削減に変更します。

### <a name="global-com-registration"></a>グローバルの COM 登録

* 以前は、Visual Studio は、ネイティブの COM 登録をサポートするために HKEY_CLASSES_ROOT および HKEY_LOCAL_MACHINE ハイブに多くのレジストリ キーをインストールします。 Visual Studio をこの影響を回避するのには今すぐ[COM コンポーネントの登録を必要としないアクティベーション](https://msdn.microsoft.com/en-us/library/ms973913.aspx)です。
* その結果、ほとんどの TLB/OLB/、%programfiles (x86) %\Common files \microsoft Shared\MSEnv DLL ファイルは Visual Studio で既定ではインストールされません。 Visual Studio ホスト プロセスによって使用される対応する登録を必要としない COM マニフェストでは、[INSTALLDIR] の下でこれらのファイルはインストールされました。
* その結果、Visual Studio の COM インターフェイスの COM 登録をグローバルに依存する外部のコードは不要になったこれらの登録を検索します。 Visual Studio プロセス内で実行中のコードでは、違いは表示されません。

### <a name="visual-studio-registry"></a>Visual Studio レジストリ

* 以前は、Visual Studio は、Visual Studio 固有キーの下で、システムの HKEY_LOCAL_MACHINE、HKEY_CURRENT_USER ハイブに多くのレジストリ キーをインストールしました。
  * HKLM\Software\Microsoft\VisualStudio\\**バージョン**: MSI インストーラーとコンピューターごとの拡張機能によって作成されたレジストリ キー。
  * HKCU\Software\Microsoft\VisualStudio\\**バージョン**: ユーザーに固有の設定を格納する Visual Studio によって作成されたレジストリ キー。
  * HKCU\Software\Microsoft\VisualStudio\\**バージョン**_Config: .pkgdef ファイルから拡張機能によって、上記の Visual Studio HKLM キーとレジストリ キーのコピーとマージします。
* レジストリへの影響を減らすためには、Visual Studio を今すぐ使用して、 [RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx) [VSAPPDATA]\privateregistry.bin 下にあるプライベートのバイナリ ファイル内のレジストリ キーを格納する関数。 Visual Studio 固有のキーの数が非常に小さいだけは、システム レジストリに残ります。
* 既存のコードを Visual Studio プロセス内で実行中は影響はありません。 Visual Studio は HKCU Visual Studio 固有のキーの下のすべてのレジストリ操作をプライベート レジストリにリダイレクトします。 読み取りと書き込みを他のレジストリの場所は、システム レジストリを使用し続けます。
* 外部コードは、Visual Studio のレジストリ エントリに対して、このファイルから読み込んだりする必要があります。

### <a name="reacting-to-this-breaking-change"></a>この重要な変更に反応します。

* 同様に COM コンポーネントの登録を必要としないアクティベーションを使用する外部コードを変換する必要があります。
* 外部コンポーネントは、Visual Studio の場所を見つけることができます[ここガイダンスに従って](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)です。
* 外部コンポーネントが使用することをお勧め、[外部の設定マネージャー](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx) Visual Studio のレジストリ キーに直接読み取り/書き込みの代わりにします。
* 登録のためのもう 1 つの方法は、拡張機能を使用してコンポーネントに実装がかどうかを確認してください。 たとえば、デバッガー拡張機能があります、新しい活用するために[msvsmon JSON ファイルの COM 登録](migrate-debugger-COM-registration.md)です。
