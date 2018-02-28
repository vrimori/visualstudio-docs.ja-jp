---
title: "VSPackage のセットアップ シナリオ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dea9d25f211ca5042234c0400b2a10086136f49c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="vspackage-setup-scenarios"></a>VSPackage のセットアップのシナリオ
ことが重要、VSPackage インストーラーによって、柔軟性をデザインします。 たとえば、今後は、セキュリティ更新プログラムをリリースする必要があります。 またはサイド バイ サイドの完全なバージョン管理サポートが必要なビジネス戦略を変更する可能性があります。  
  
 [をサポートする複数のバージョンの Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)、長所とのサイド バイ サイド インストールのサポートの問題について[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage の共有またはサイド バイ サイド インストールする場合。 つまり、サイド バイ サイドの Vspackage を使用する最も柔軟の新機能をサポートするために[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
 このトピックで説明したシナリオは、唯一の選択肢ではありませんが、推奨されるベスト プラクティスとして記載されています。  
  
## <a name="components-privacy-and-sharing"></a>コンポーネント、プライバシー、および共有  
  
##### <a name="make-your-components-independent"></a>コンポーネントを独立させる  
 識別し、コンポーネントを設定すると、割り当てる、`GUID`コンポーネントの配置し、その構成を変更することはできません。 結果として得られるコンポーネントを新しい新しいコンポーネントである必要があります、コンポーネントの構成を変更すると場合、`GUID`です。 これらのファクトを指定するには、最大限のバージョン管理の柔軟性が利用可能になる各コンポーネントの制御、独立した単位をすることによりします。 コンポーネントに適用される規則の詳細については、次を参照してください。[コンポーネントのコードを変更する](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx)と[場合の対処、コンポーネントのルールごとに分割されて?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)です。  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>コンポーネントで共有およびプライベートのリソースを混在させないでください。  
 参照カウントは、コンポーネント レベルで発生します。 その結果、1 つのコンポーネントで共有およびプライベートのリソースを混在させる不可能でも共有リソースを上書きすることがなく、実行可能ファイルなどのプライベート リソースを更新します。 このシナリオでは、旧バージョンと互換性の問題を作成し、サイド バイ サイド機能を作成するを制限します。  
  
 VSPackage を登録するレジストリ値を使用するなど、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]は別々 に保存するコンポーネントのいずれかで、VSPackage を登録するために使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 共有ファイルまたはレジストリ値は、まだ別のコンポーネントに移動します。  
  
## <a name="scenario-1-shared-vspackage"></a>シナリオ 1: VSPackage の共有  
 このシナリオでは、共有の VSPackage で (1 つのバイナリの複数のバージョンをサポートする[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)])、Windows インストーラー パッケージに付属しています。 各バージョンと共に登録[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ユーザー選択可能な機能によって制御されます。 機能を個別に割り当てると、各コンポーネント選択できるように個別にインストールまたはアンインストールを減らし、ユーザーが異なるバージョンへの VSPackage の統合を制御することも意味[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 (を参照してください[Windows インストーラーの機能の](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx)詳細について、Windows インストーラー パッケージの機能を使用します)。  
  
 ![VS 共有 vs パッケージ グラフィック](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")  
共有の VSPackage インストーラー  
  
 図に示すように、共有コンポーネントには、常にインストールされている Feat_Common 機能の一部が行われます。 Feat_VS2002 と Feat_VS2003 の機能を表示するには、どのバージョンに、ユーザーがインストール時に選択できます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage を統合します。 ユーザーまたは追加または削除、機能をここで追加の異なるバージョンから VSPackage の登録情報を削除する Windows インストーラーのメンテナンス モードを使用できますも[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
> [!NOTE]
>  機能の表示の列を 0 に設定を非表示にします。 1 などの低レベルの列の値により、常にインストールされます。 詳細については、次を参照してください。 [INSTALLLEVEL プロパティ](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx)と[機能テーブル](http://msdn.microsoft.com/library/aa368585.aspx)です。  
  
## <a name="scenario-2-shared-vspackage-update"></a>シナリオ 2: 共有 vs パッケージ更新  
 このシナリオでは、シナリオ 1 で VSPackage インストーラーの更新バージョンが付属しています。 詳細については、ここでのサポートを追加する、更新[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、シンプルなセキュリティ更新プログラムまたはバグ修正サービス パックの場合もありますが、します。 新しいコンポーネントをインストールするための Windows インストーラーの規則は、システムに既に変更されていないコンポーネントがない再びコピーされることが必要です。 ここでは、バージョン 1.0 がまだ存在してシステムは更新されたコンポーネント Comp_MyVSPackage.dll を上書きし、Comp_VS2005_Reg そのコンポーネントの新機能 Feat_VS2005 を追加することができます。  
  
> [!CAUTION]
>  VSPackage を複数のバージョンの間で共有されるたびに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、VSPackage の今後のリリースでの以前のバージョンとの下位互換性を維持できる重要[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 旧バージョンとの互換性を維持することはできません、場所は、サイド バイ サイドでプライベートの Vspackage を使用する必要があります。 詳細については、次を参照してください。[をサポートする複数のバージョンの Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)です。  
  
 ![VS 共有 VS パッケージ更新イメージ](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")  
VSPackage の更新プログラムのインストーラーを共有  
  
 このシナリオでは、新しい VSPackage インストーラー、マイナー アップグレード用の Windows インストーラーのサポートの利用について説明します。 ユーザーは単にバージョン 1.1 をインストールし、バージョン 1.0 をアップグレードします。 ただし、システムのバージョンは 1.0 する必要はありません。 同一のインストーラーは、バージョン 1.0 のないシステムでバージョン 1.1 がインストールされます。 このようなマイナー アップグレードを提供する場合はことは、インストーラーにアップグレードし、製品インストーラーの開発作業を通過する必要はありません。 1 つのインストーラーは、どちらのジョブです。 セキュリティ修正プログラムまたはサービス パックが代わりに Windows インストーラー修正プログラムの利点を活かすします。 詳細については、次を参照してください。[修正プログラムの適用とアップグレード](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx)です。  
  
## <a name="scenario-3-side-by-side-vspackage"></a>シナリオ 3: サイド バイ サイド vs パッケージ  
 このシナリオでは、VSPackage の 2 つのインストーラー: Visual Studio .NET 2003 のバージョンごとに 1 つと[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 各インストーラーは、サイド バイ サイド、またはプライベート、VSPackage がインストールされます (具体的にはビルドされ、特定のバージョンの用にインストールされている[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)])。 各 VSPackage は、独自のコンポーネントです。 そのため、それぞれ個別に処理されると修正プログラムやメンテナンスを解放します。 VSPackage DLL は、バージョン固有では今すぐであるために、DLL と同じコンポーネントにその登録情報を追加しても安全です。  
  
 ![VS サイド &#45; によって &#45;です。サイド VS パッケージ グラフィック](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")  
サイド バイ サイド vs パッケージ インストーラー  
  
 各インストーラーには、2 つのインストーラーの間で共有されるコードも含まれています。 共有コードが共通の場所にインストールされている場合両方の .msi ファイルのインストールはインストール共有コード 1 回だけします。 2 番目のインストーラーには、コンポーネントの参照カウントだけインクリメントします。 参照カウント、Vspackage のいずれかがアンインストールされると、共有コードには引き続き他の VSPackage のことを確認します。 2 番目の VSPackage がもアンインストールされると、共有コードが削除されます。  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>シナリオ 4: サイド バイ サイド vs パッケージ更新  
 このシナリオでは、VSPackage で[!INCLUDE[vsprvslong](../../code-quality/includes/vsprvslong_md.md)]があって、セキュリティの脆弱性とする必要があります更新プログラムを発行します。 シナリオ 2 と同様に、既存のインストールをセキュリティ修正プログラムを含めるできるだけでなく、新しい場所に既にのセキュリティ修正プログラム、インストールの展開を更新する新しい .msi ファイルを作成できます。  
  
 ここでは、VSPackage は、グローバル アセンブリ キャッシュ (GAC) にインストールされているマネージ VSPackage です。 セキュリティ修正プログラムを含むように再構築するときは、アセンブリのバージョン番号のリビジョン番号部分を変更する必要があります。 登録情報の原因で、新しいアセンブリ バージョン番号は、以前のバージョンを上書きの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]固定のアセンブリを読み込めません。  
  
 ![VS サイド &#45; によって &#45;です。サイド VS パッケージ更新グラフィック](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")  
サイド バイ サイド vs パッケージ更新プログラムのインストーラー  
  
 **注**サイド バイ サイド アセンブリの展開の詳細については、次を参照してください。[の簡略化の展開と .NET Framework での DLL ヘルの解決](http://msdn.microsoft.com/library/ms973843.aspx)です。  
  
## <a name="see-also"></a>参照  
 [Windows インストーラー](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [複数バージョンの Visual Studio をサポートする](../../extensibility/supporting-multiple-versions-of-visual-studio.md)