---
title: "Visual Studio 2017 拡張機能における重大な変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
caps.latest.revision: 1
author: gregvanl
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
ms.sourcegitcommit: 221f4911981deec0330f76a82c0cc8a1b968e56e
ms.openlocfilehash: 081a569fc7e38fecc8cc1ae5b0f8138ae8f25521
ms.lasthandoff: 02/22/2017

---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Visual Studio 2017 機能拡張の変更

>**注:**このドキュメントは暫定版であり、Visual Studio 2017 RC リリースに基づいています。

Visual Studio 2017 年で提供して、[高速、軽量な Visual Studio のインストール エクスペリエンス](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer)Visual Studio のユーザーのシステムへの影響を削減するためのワークロードとインストールされている機能をより多くの選択肢をユーザーに提供中にします。 これらの機能強化をサポートするためにはお機能拡張モデルに変更を行ったし、Visual Studio 拡張機能にいくつか大きな変更が加えします。 このドキュメントでは、これらの変更、および対処できるの技術的な詳細を説明します。 なお、一部の情報が特定の時点の実装の詳細についてで、後から変更することがあります。

## <a name="changes-affecting-vsix-format-and-installation"></a>VSIX 形式とインストールに影響する変更

VSIX v3 掲載し、軽量のインストール環境をサポートするために (バージョン 3) 形式です。

VSIX 形式への変更は次のとおりです。

* セットアップの前提条件の宣言。 今すぐインストーラーはを軽量で高速インストールすると、Visual Studio の約束を実現するには、ユーザーに多くの構成オプションを提供します。 その結果、機能と拡張機能により必要なコンポーネントがインストールされていることを確認するには、拡張機能はその依存関係を宣言する必要があります。
  * RC のリリースで、自動的に取得および拡張機能のインストールの一部として、ユーザーに必要なコンポーネントをインストールするに Visual Studio 2017 インストーラーが提供されます。
  * 構築されなかった、新しい VSIX v3 形式を使用して 15.0 を対象とすると、マニフェストでマークされている場合でも、拡張機能をインストールしようとすると、ユーザーは警告も。
* VSIX 形式の強化された機能です。 実現する、[影響の少ないインストール](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install)サイド バイ サイド インストールをサポートする Visual Studio での不要になったほとんどの構成データをシステム レジストリに保存し、GAC から Visual Studio 固有のアセンブリに移動します。 また引き上げました VSIX 形式と VSIX インストール エンジンの機能ではなく、MSI、EXE を使用して、インストールの種類によって、拡張機能をインストールすることができます。

  新しい機能は次のとおりです。

  * 指定した Visual Studio インスタンスに登録します。
  * 外部のインストール、[機能拡張フォルダー](set-install-root.md)します。
  * プロセッサ アーキテクチャを検出します。
  * 言語で区切られた言語パックに依存します。
  * 使用してインストール[NGEN サポート](ngen-support.md)します。

## <a name="building-an-extension-for-visual-studio-2017"></a>Visual Studio 2017 用拡張機能の構築

新しいの作成を行うツール デザイナー VSIX v3 マニフェスト形式は今すぐ Visual Studio 2017 で利用可能なです。 付属のドキュメントを参照してください[方法: Visual Studio 2017 を機能拡張プロジェクトの移行](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)詳細については、デザイナーのツールを使用する、プロジェクトを手動で更新したことでと VSIX v3 の拡張機能を開発するマニフェスト。

## <a name="change-visual-studio-user-data-path"></a>Visual Studio のユーザー データ パスを変更します。

以前は、Visual Studio の各メジャー リリースの&1; つだけインストールは、各コンピューターに存在でした。 Visual Studio 2017 のサイド バイ サイド インストールをサポートするために、ユーザーのコンピューターに Visual Studio の複数のユーザー データ パスがあります。

Visual Studio のプロセス内で実行されるコードは、Visual Studio の設定マネージャーを使用して更新する必要があります。 Visual Studio のプロセスの外部で実行されているコードには、特定の Visual Studio インストールのユーザーのパスを見つける[ここでのガイダンスに従って、](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)です。

## <a name="change-global-assembly-cache-gac"></a>グローバル アセンブリ キャッシュ (GAC) を変更します。

ほとんどの Visual Studio コア アセンブリは GAC にインストールされません。 Visual Studio のプロセスで実行されるコードは引き続き実行時に必要なアセンブリを検出できるように、次の変更が行われました。

* アセンブリを GAC にインストールされただけの:
  * これらのアセンブリが %VsFolder%\Common7\IDE インストールされた\,%VsFolder%\Common7\IDE\PublicAssemblies または %vsfolder%\common7\ide\privateassemblies します。 これらのフォルダーは、Visual Studio のプロセスのプローブ パスの一部です。
* 非プローブ パスと、GAC にインストールされているアセンブリの場合:
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
    実行時に、Visual Studio pkgdef サブシステムではマージ %vsappdatafolder%\devenv.exe.config) Visual Studio のプロセスの実行時の構成ファイルにこれらのエントリとして[ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx)要素。 これは、プローブ パスによる検索を回避するので、Visual Studio プロセスが独自のアセンブリを検索することをお勧めします。

### <a name="reacting-to-this-breaking-change"></a>この互換性に影響する変更に反応します。

* 場合は、拡張機能は、Visual Studio のプロセス内で実行しています。
  * コードは Visual Studio の中核となるアセンブリを検索することになります。
  * 必要に応じて、アセンブリへのパスを指定する .pkgdef ファイルを使用してください。
* 場合は、拡張機能は Visual Studio のプロセスの外部で実行しています。
  * %VsFolder%\Common7\IDE Visual Studio の中核となるアセンブリの検索を検討してください\,%VsFolder%\Common7\IDE\PublicAssemblies または %VsFolder%\Common7\IDE\PrivateAssemblies 構成ファイルまたはアセンブリの競合回避モジュールを使用します。

## <a name="change-reduce-registry-impact"></a>変更します。 レジストリの影響を軽減します。

### <a name="global-com-registration"></a>グローバルの COM 登録

* 以前は、Visual Studio では、ネイティブの COM 登録をサポートするために HKEY_CLASSES_ROOT および HKEY_LOCAL_MACHINE ハイブに多くのレジストリ キーがインストールされます。 この影響をなくすためには、Visual Studio がここでは使用[COM コンポーネントの登録を必要としないアクティベーション](https://msdn.microsoft.com/en-us/library/ms973913.aspx)します。
* その結果、ほとんどの TLB/OLB/、% %programfiles (x86) %\Common files \microsoft Shared\MSEnv DLL のファイルは Visual Studio では、既定ではインストールされません。 これらのファイルは、Visual Studio ホスト プロセスによって使用される登録を必要としない COM マニフェストの対応すると共に VsFolder % 今すぐインストールされます。
* その結果、Visual Studio COM インターフェイス用のグローバルの COM 登録に依存する外部のコードは不要になったこれらの登録を検索します。 Visual Studio のプロセス内で実行されるコードでは、違いが見られない。

### <a name="visual-studio-registry"></a>Visual Studio レジストリ

* 以前は、Visual Studio では、Visual Studio 固有のキーの下で、システムの HKEY_LOCAL_MACHINE と HKEY_CURRENT_USER ハイブに多くのレジストリ キーをインストールします。
  * Hklm \software\microsoft\visualstudio\\**バージョン**: MSI インストーラーではコンピュータ単位の拡張機能によって作成されたレジストリ キーです。
  * Hkcu \software\microsoft\visualstudio\\**バージョン**: ユーザーに固有の設定を格納する Visual Studio によって作成されたレジストリ キーです。
  * Hkcu \software\microsoft\visualstudio\\**バージョン**_Config: 拡張機能で .pkgdef ファイルから、上の Visual Studio HKLM キーとレジストリ キーのコピーをマージします。
* レジストリへの影響を減らすためには、Visual Studio を今すぐ使用して、 [RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx) %vsappdatafolder%\privateregistry.bin プライベート バイナリ ファイル内のレジストリ キーを保存します。 Visual Studio 固有のキーの数が非常に少ないだけは、システム レジストリに残ります。
* Visual Studio のプロセス内で実行される既存のコードは影響はありません。 Visual Studio は HKCU Visual Studio 固有のキーの下のすべてのレジストリ操作をプライベート レジストリにリダイレクトします。 読み取りと書き込みを他のレジストリの場所は、システム レジストリを使用し続けます。
* 外部コードは、Visual Studio のレジストリ エントリは、このファイルから読み込んだりする必要があります。

### <a name="reacting-to-this-breaking-change"></a>この互換性に影響する変更に反応します。

* 同様に COM コンポーネントの登録を必要としないアクティベーションを使用する外部コードを変換する必要があります。
* 外部コンポーネントは、Visual Studio の場所を見つけることができます[ここでのガイダンスに従って、](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)です。
* 外部コンポーネントを使用していることをお勧めします[外部設定マネージャー](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx) Visual Studio のレジストリ キーに直接、読み取り/書き込みではなく。
* 登録のためのもう&1; つの方法は、拡張機能を使用して、コンポーネントに実装がかどうかを確認してください。 たとえば、デバッガー拡張機能があります、新しい活用するために[msvsmon JSON ファイルの COM 登録](migrate-debugger-COM-registration.md)します。

## <a name="change-lightweight-solution-load"></a>軽量なソリューションの読み込みに変更します。

軽量なソリューションを読み込む (LSL) では、完全には、ユーザーがそれらに作業を開始するまでにプロジェクトを読み込むことによってソリューションの読み込み時間が減少します。 これは、プロジェクトが完全に読み込まれると想定する拡張機能に影響を与えます。 参照してください[ライトウェイト ソリューションの読み込み](lightweight-solution-load-extension-impact.md)拡張機能が受ける可能性がありますおよび拡張機能を更新する方法のガイダンスが用意されているかどうかを確認します。

