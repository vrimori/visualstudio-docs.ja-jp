---
title: VSPackage のセットアップ シナリオ |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3dfe3f3c135cb3ed16c7550fc62d334cc548cd1
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510667"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage のセットアップ シナリオ

柔軟性を高めるため、VSPackage のインストーラーの設計に重要です。 たとえば、今後は、セキュリティ更新プログラムをリリースする必要があります。 またはサイド バイ サイドでの完全なバージョン管理サポートが必要なビジネス戦略を変更する可能性があります。

[をサポートしている複数のバージョンの Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)、長所とのサイド バイ サイドでインストールをサポートの問題について[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage の共有またはサイド バイ サイドでインストールします。 つまり、サイド バイ サイドで Vspackage、最も柔軟性の新機能をサポートするために[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。

このトピックで説明したシナリオは、唯一の選択肢ではありませんが、推奨されるベスト プラクティスとして表示されます。

## <a name="components-privacy-and-sharing"></a>コンポーネント、プライバシー、および共有

### <a name="make-your-components-independent"></a>コンポーネントを独立させる

識別し、コンポーネントを設定すると、割り当て、`GUID`コンポーネントの配置しは、その構成を変更することはできません。 コンポーネントの構成を変更する場合、結果として得られるコンポーネントは新しいコンポーネントを新しいをする必要があります`GUID`します。 これらのファクトを指定するには、各コンポーネントの制御、独立したユニットのことで最大のバージョン管理の柔軟性が提供します。 コンポーネントを制御する規則の詳細については、次を参照してください。[コンポーネントのコードを変更する](/windows/desktop/Msi/changing-the-component-code)と[場合の対処、コンポーネントの規則は分割されますか?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)。

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>コンポーネント内の共有とプライベートのリソースを混在させないでください。

参照カウントは、コンポーネント レベルで発生します。 その結果、1 つのコンポーネントでの共有とプライベートのリソースを混在させるが不可能も共有リソースを上書きすることがなく、実行可能ファイルなどのプライベート リソースを更新します。 このシナリオでは、旧バージョンとの互換性の問題を作成しをサイド バイ サイドでの機能を作成することを制限します。

VSPackage を登録するレジストリ値を使用するなど、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]が別々 に保存するコンポーネントのいずれかの Visual Studio で、VSPackage を登録するために使用します。 共有ファイルまたはレジストリ値は、まだ別のコンポーネントに移動します。

## <a name="scenario-1-shared-vspackage"></a>シナリオ 1: 共有 VSPackage

このシナリオでは、(Visual Studio の複数のバージョンをサポートする 1 つのバイナリは、Windows インストーラー パッケージに付属しています共有 VSPackage で。 各バージョンの Visual Studio に登録すると、ユーザーが選択可能な機能によって制御されます。 機能を個別に割り当てると、各コンポーネント選択できるように個別にインストールまたはアンインストール、異なるバージョンに VSPackage を統合するコントロールにユーザーを配置することも意味[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 (を参照してください[Windows インストーラーの機能](/windows/desktop/Msi/windows-installer-features)Windows インストーラー パッケージで機能の使い方の詳細についてはします)。

![VS 共有 vs パッケージ インストーラー](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

図に示すように共有コンポーネントには、常にインストールされている Feat_Common 機能の一部が行われます。 によって Feat_VS2002 と Feat_VS2003 機能を表示するには、ユーザーを統合する VSPackage をする、Visual Studio のバージョンにインストール時に選択できます。 ユーザーは、Windows インストーラーのメンテナンス モードを使用して、追加またはをここで追加または異なるバージョンの Visual Studio から VSPackage の登録情報を削除、機能を削除することができますも。

> [!NOTE]
> 機能の表示の列を 0 に設定します。 非表示にします。 1 などの低レベルの列値によりは常にインストールするようになります。 詳細については、次を参照してください。 [INSTALLLEVEL プロパティ](/windows/desktop/Msi/installlevel)と[機能テーブル](/windows/desktop/Msi/feature-table)します。

## <a name="scenario-2-shared-vspackage-update"></a>シナリオ 2: 共有 vs パッケージ更新

このシナリオでは、シナリオ 1 で、VSPackage のインストーラーの更新バージョンが付属しています。 便宜上、更新プログラムは、Visual Studio のサポートを追加しますが、でしたも単純なセキュリティ更新プログラムをするか、またはバグ修正のサービス パック。 新しいコンポーネントをインストールするための Windows インストーラーの規則では、システムに既に変更されていないコンポーネントが再コピーしないことが必要です。 この場合は、バージョン 1.0 が既に存在すると、システムは Comp_MyVSPackage.dll 更新されたコンポーネントを上書きし、Comp_VS2005_Reg そのコンポーネントの新機能 Feat_VS2005 を追加することもできます。

> [!CAUTION]
> VSPackage を複数のバージョンの間で共有されるたびに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage の今後のリリースが Visual Studio の以前のバージョンとの下位互換性を維持することが重要です。 下位互換性を維持することはできませんがサイド バイ サイドで、プライベートの Vspackage を使用する必要があります。 詳細については、次を参照してください。[をサポートしている複数のバージョンの Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)します。

![VS 共有 VS パッケージ更新プログラムのインストーラー](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

このシナリオは、マイナー アップグレード用の Windows インストーラーのサポートの活用、新しい VSPackage インストーラーを表示します。 ユーザーが単純にバージョン 1.1 をインストールし、バージョン 1.0 をアップグレードします。 ただし、バージョンは 1.0 システムにする必要はありません。 同じインストーラーは、バージョン 1.0 のないシステムでバージョン 1.1 がインストールされます。 この方法でマイナー アップグレードを提供することの利点は、ことは、アップグレードのインストーラーと完全な製品インストーラーの開発の作業を経由する必要はありません。 1 つのインストーラーは、両方のジョブです。 セキュリティ修正プログラムまたはサービス パックが代わりに Windows インストーラーの修正プログラムの利点を活かす。 詳細については、次を参照してください。[パッチとアップグレード](/windows/desktop/Msi/patching-and-upgrades)します。

## <a name="scenario-3-side-by-side-vspackage"></a>シナリオ 3: サイド バイ サイド vs パッケージ

このシナリオでは、2 つの VSPackage インストーラー-Visual Studio .NET 2003 と Visual Studio のバージョンごとに 1 つ。 各インストーラーには、並列でまたはプライベート、VSPackage (具体的には構築および特定のバージョンの Visual Studio 用にインストールされているもの) がインストールされます。 各 VSPackage は、独自のコンポーネントです。 その結果、それぞれ個別に処理されると修正プログラムやメンテナンスを解放します。 VSPackage の DLL は、バージョン固有ではこれであるため、DLL と同じコンポーネントにその登録情報を含めるも安全です。

![VS サイド バイ サイド VS パッケージ インストーラー](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

各インストーラーには、2 つのインストーラーの間で共有されるコードも含まれています。 共有コードが共通の場所にインストールされている、両方の .msi ファイルのインストールはインストール共有コード 1 回だけ。 2 番目のインストーラーは、だけでは、コンポーネントの参照カウントをインクリメントします。 参照カウントを確実に、Vspackage のいずれかをアンインストールする場合は、共有コードは、その他の VSPackage の保ちます。 2 つ目の VSPackage をもアンインストールする場合は、共有コードは削除されます。

## <a name="scenario-4-side-by-side-vspackage-update"></a>シナリオ 4: サイド バイ サイド vs パッケージ更新プログラム

このシナリオでは、セキュリティの脆弱性から Visual Studio の VSPackage を検出しましたし、更新プログラムを発行する必要があります。 シナリオ 2 のように更新プログラムの既存のインストールを新しい場所に既にのセキュリティ修正プログラム、インストールをデプロイできるだけでなく、セキュリティの修正プログラムが含まれている新しい .msi ファイルを作成できます。

この場合は、VSPackage は、グローバル アセンブリ キャッシュ (GAC) にインストールされているマネージ VSPackage は。 セキュリティ修正プログラムを含むように再構築するときは、アセンブリのバージョン番号のリビジョン番号部分を変更する必要があります。 登録情報の新しいアセンブリ バージョン番号は、以前のバージョンを上書き、原因[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]固定のアセンブリを読み込みます。

![VS サイド バイ サイド VS パッケージ更新プログラムのインストーラー](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

サイド バイ サイド アセンブリの展開の詳細については、次を参照してください。[展開の簡素化すると、.NET Framework での DLL Hell の解決](http://msdn.microsoft.com/library/ms973843.aspx)します。

## <a name="see-also"></a>関連項目

[Windows インストーラー](/windows/desktop/Msi/windows-installer-portal)  
[複数バージョンの Visual Studio をサポートする](../../extensibility/supporting-multiple-versions-of-visual-studio.md)