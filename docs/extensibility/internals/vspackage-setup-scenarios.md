---
title: VSPackage のセットアップ シナリオ |Microsoft ドキュメント
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
ms.openlocfilehash: b58400330bb2032354d28a7b76729a5d7f85fd3c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="vspackage-setup-scenarios"></a>VSPackage のセットアップのシナリオ

ことが重要、VSPackage インストーラーによって、柔軟性をデザインします。 たとえば、今後は、セキュリティ更新プログラムをリリースする必要があります。 またはサイド バイ サイドの完全なバージョン管理サポートが必要なビジネス戦略を変更する可能性があります。

[をサポートする複数のバージョンの Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)、長所とのサイド バイ サイド インストールのサポートの問題について[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage の共有またはサイド バイ サイド インストールする場合。 つまり、サイド バイ サイドの Vspackage を使用する最も柔軟の新機能をサポートするために[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。

このトピックで説明したシナリオは、唯一の選択肢ではありませんが、推奨されるベスト プラクティスとして記載されています。

## <a name="components-privacy-and-sharing"></a>コンポーネント、プライバシー、および共有

### <a name="make-your-components-independent"></a>コンポーネントを独立させる

識別し、コンポーネントを設定すると、割り当てる、`GUID`コンポーネントの配置し、その構成を変更することはできません。 結果として得られるコンポーネントを新しい新しいコンポーネントである必要があります、コンポーネントの構成を変更すると場合、`GUID`です。 これらのファクトを指定するには、最大限のバージョン管理の柔軟性が利用可能になる各コンポーネントの制御、独立した単位をすることによりします。 コンポーネントに適用される規則の詳細については、次を参照してください。[コンポーネントのコードを変更する](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx)と[場合の対処、コンポーネントのルールごとに分割されて?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)です。

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>コンポーネントで共有およびプライベートのリソースを混在させないでください。

参照カウントは、コンポーネント レベルで発生します。 その結果、1 つのコンポーネントで共有およびプライベートのリソースを混在させる不可能でも共有リソースを上書きすることがなく、実行可能ファイルなどのプライベート リソースを更新します。 このシナリオでは、旧バージョンと互換性の問題を作成し、サイド バイ サイド機能を作成するを制限します。

VSPackage を登録するレジストリ値を使用するなど、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]は別々 に保存するコンポーネントのいずれかの Visual Studio で、VSPackage を登録するために使用します。 共有ファイルまたはレジストリ値は、まだ別のコンポーネントに移動します。

## <a name="scenario-1-shared-vspackage"></a>シナリオ 1: VSPackage の共有

このシナリオでは、(Visual Studio の複数のバージョンをサポートする単一のバイナリは、Windows インストーラー パッケージに付属して共有 VSPackage でいます。 各バージョンの Visual Studio に登録することは、ユーザーが選択可能な機能によって制御されます。 機能を個別に割り当てると、各コンポーネント選択できるように個別にインストールまたはアンインストールを減らし、ユーザーが異なるバージョンへの VSPackage の統合を制御することも意味[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 (を参照してください[Windows インストーラーの機能の](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx)詳細について、Windows インストーラー パッケージの機能を使用します)。

![VS 共有 vs パッケージ インストーラー](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

図に示すように、共有コンポーネントには、常にインストールされている Feat_Common 機能の一部が行われます。 によって、Feat_VS2002 および Feat_VS2003 の機能を表示するには、ユーザーのどのバージョンの Visual Studio に統合する VSPackage するインストール時に選択できます。 ユーザーは、Windows インストーラーのメンテナンス モードを使用して、または追加または削除、機能をここで追加 VSPackage の登録情報を別のバージョンの Visual Studio から削除することができますも。

> [!NOTE]
> 機能の表示の列を 0 に設定を非表示にします。 1 などの低レベルの列の値により、常にインストールされます。 詳細については、次を参照してください。 [INSTALLLEVEL プロパティ](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx)と[機能テーブル](http://msdn.microsoft.com/library/aa368585.aspx)です。

## <a name="scenario-2-shared-vspackage-update"></a>シナリオ 2: 共有 vs パッケージ更新

このシナリオでは、シナリオ 1 で VSPackage インストーラーの更新バージョンが付属しています。 詳細については、ここでは、Visual Studio のサポートを追加しますが、でしたもシンプルなセキュリティ パッチをするか、またはサービス パックのバグ修正。 新しいコンポーネントをインストールするための Windows インストーラーの規則は、システムに既に変更されていないコンポーネントがない再びコピーされることが必要です。 ここでは、バージョン 1.0 がまだ存在してシステムは更新されたコンポーネント Comp_MyVSPackage.dll を上書きし、Comp_VS2005_Reg そのコンポーネントの新機能 Feat_VS2005 を追加することができます。

> [!CAUTION]
> VSPackage を複数のバージョンの間で共有されるたびに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage の今後のリリースが Visual Studio の以前のバージョンとの下位互換性を維持することが重要です。 旧バージョンとの互換性を維持することはできません、場所は、サイド バイ サイドでプライベートの Vspackage を使用する必要があります。 詳細については、次を参照してください。[をサポートする複数のバージョンの Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)です。

![VS 共有 VS パッケージ更新プログラムのインストーラー](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

このシナリオでは、新しい VSPackage インストーラー、マイナー アップグレード用の Windows インストーラーのサポートの利用について説明します。 ユーザーは単にバージョン 1.1 をインストールし、バージョン 1.0 をアップグレードします。 ただし、システムのバージョンは 1.0 する必要はありません。 同一のインストーラーは、バージョン 1.0 のないシステムでバージョン 1.1 がインストールされます。 このようなマイナー アップグレードを提供する場合はことは、インストーラーにアップグレードし、製品インストーラーの開発作業を通過する必要はありません。 1 つのインストーラーは、どちらのジョブです。 セキュリティ修正プログラムまたはサービス パックが代わりに Windows インストーラー修正プログラムの利点を活かすします。 詳細については、次を参照してください。[修正プログラムの適用とアップグレード](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx)です。

## <a name="scenario-3-side-by-side-vspackage"></a>シナリオ 3: サイド バイ サイド vs パッケージ

このシナリオでは、VSPackage の 2 つのインストーラー: Visual Studio .NET 2003 および Visual Studio のバージョンごとに 1 つです。 各インストーラーは、サイド バイ サイド、またはプライベート、VSPackage (具体的にはビルドされ、Visual Studio の特定のバージョン用にインストールされているもの) をインストールします。 各 VSPackage は、独自のコンポーネントです。 そのため、それぞれ個別に処理されると修正プログラムやメンテナンスを解放します。 VSPackage DLL は、バージョン固有では今すぐであるために、DLL と同じコンポーネントにその登録情報を追加しても安全です。

![VS サイド バイ サイド VS パッケージ インストーラー](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

各インストーラーには、2 つのインストーラーの間で共有されるコードも含まれています。 共有コードが共通の場所にインストールされている場合両方の .msi ファイルのインストールはインストール共有コード 1 回だけします。 2 番目のインストーラーには、コンポーネントの参照カウントだけインクリメントします。 参照カウント、Vspackage のいずれかがアンインストールされると、共有コードには引き続き他の VSPackage のことを確認します。 2 番目の VSPackage がもアンインストールされると、共有コードが削除されます。

## <a name="scenario-4-side-by-side-vspackage-update"></a>シナリオ 4: サイド バイ サイド vs パッケージ更新

このシナリオでセキュリティの脆弱性から Visual Studio の VSPackage が発生したし、更新プログラムを発行する必要があります。 シナリオ 2 と同様に、既存のインストールをセキュリティ修正プログラムを含めるできるだけでなく、新しい場所に既にのセキュリティ修正プログラム、インストールの展開を更新する新しい .msi ファイルを作成できます。

ここでは、VSPackage は、グローバル アセンブリ キャッシュ (GAC) にインストールされているマネージ VSPackage です。 セキュリティ修正プログラムを含むように再構築するときは、アセンブリのバージョン番号のリビジョン番号部分を変更する必要があります。 登録情報の原因で、新しいアセンブリ バージョン番号は、以前のバージョンを上書きの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]固定のアセンブリを読み込めません。

![VS サイド バイ サイド VS パッケージ更新プログラムのインストーラー](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

サイド バイ サイド アセンブリの展開の詳細については、次を参照してください。[の簡略化の展開と .NET Framework での DLL ヘルの解決](http://msdn.microsoft.com/library/ms973843.aspx)です。

## <a name="see-also"></a>関連項目

[Windows インストーラー](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)  
[複数バージョンの Visual Studio をサポートする](../../extensibility/supporting-multiple-versions-of-visual-studio.md)