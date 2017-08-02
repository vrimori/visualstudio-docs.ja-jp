---
title: "VSPackage のセットアップのシナリオ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vspackages にある、展開に関する考慮事項"
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# VSPackage のセットアップのシナリオ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ことが重要、vs パッケージ インストーラーの柔軟性を設計します。 たとえば、今後は、セキュリティ更新プログラムをリリースする必要があります。 またはサイド バイ サイドの完全なバージョン管理サポートが必要なビジネス戦略を変更することがあります。  
  
 [Visual Studio の複数のバージョンをサポートします。](../../extensibility/supporting-multiple-versions-of-visual-studio.md), 、長所とのサイド バイ サイド インストールのサポートの問題に関する記事を参照する [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 、VSPackage の共有またはサイド バイ サイド インストールする場合。 要するに、サイド バイ サイド Vspackage を使用する、最も柔軟の新機能をサポートするために [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
 このトピックで説明したシナリオは、唯一の選択肢ではありませんが、推奨されるベスト プラクティスとして示されています。  
  
## コンポーネント、プライバシー、および共有  
  
##### コンポーネントを独立させる  
 識別し、コンポーネントを設定すると、割り当て、 `GUID`, 、コンポーネントを展開して、その構成を変更することはできません。 結果として得られるコンポーネントは、新しいコンポーネントを新しい場合は、コンポーネントの構成を変更すると、 `GUID`です。 これらの情報を指定するには、各コンポーネント頼らずに知見、独立したユニットをすることで柔軟性のバージョン管理が付与されました。 コンポーネントに適用される規則の詳細については、次を参照してください。 [コンポーネントのコードを変更する](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) と [場合の対処、コンポーネントのルールは、分類?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)します。  
  
##### コンポーネント内の共有とプライベートのリソースを混在させないでください。  
 参照カウントは、コンポーネント レベルで発生します。 その結果、1 つのコンポーネントで共有およびプライベートのリソースを混在させることはなくなりますも共有リソースを上書きすることがなく、実行可能ファイルなどのリソースをプライベートを更新します。 このシナリオでは、旧バージョンと互換性の問題が発生し、サイド バイ サイド機能を作成するを制限します。  
  
 レジストリ値が、VSPackage での登録に使用するなど、 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] で維持するか、コンポーネント、VSPackage での登録に使用される 1 つから独立した [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 共有ファイルまたはレジストリ値は、さらに別のコンポーネントに移動します。  
  
## シナリオ 1: 共有 vs パッケージ  
 このシナリオでは、共有 vs パッケージで \(の複数のバージョンをサポートする単一のバイナリ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\)、Windows インストーラー パッケージに付属しています。 各バージョンと共に登録 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] はユーザーが選択可能な機能によって制御されます。 ある機能を個別に割り当てると、各コンポーネントを選択できる個別にインストールまたはアンインストールのほか、さまざまなバージョンに VSPackage を統合するコントロールで、ユーザーを設定することも意味 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 \(を参照してください [Windows インストーラーの機能の](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) 詳細について、Windows インストーラー パッケージの機能を使用します\)。  
  
 ![VS 共有 VS パッケージ グラフィック](~/docs/extensibility/internals/media/vs_sharedpackage.gif "VS\_SharedPackage")  
共有 vs パッケージ インストーラー  
  
 図に示すように共有コンポーネントには、常にインストールされている Feat\_Common 機能の一部は行われます。 Feat\_VS2002 および Feat\_VS2003 の機能を表示するには、のどのバージョンに、ユーザーがインストール時に選択できる [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage を統合します。 ユーザーは追加またはをここでの追加または削除 VSPackage 登録情報のさまざまなバージョンの機能を削除する Windows インストーラーのメンテナンス モードを使用する [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
> [!NOTE]
>  機能の表示の列を 0 に設定するに非表示にします。 1 などの低レベルの列の値により、常にインストールされます。 詳細については、次を参照してください。 [INSTALLLEVEL プロパティ](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) と [機能テーブル](http://msdn.microsoft.com/library/aa368585.aspx)します。  
  
## シナリオ 2: 共有 vs パッケージ更新  
 このシナリオでは、シナリオ 1 で vs パッケージ インストーラーの更新バージョンが付属しています。 詳細については、目的のサポートが追加、更新プログラム [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], 、シンプルなセキュリティ修正プログラムまたはバグ修正サービス パックの場合もありますが、します。 新しいコンポーネントをインストールするための Windows インストーラーの規則では、システムに既に変更されていないコンポーネントが再コピーしないことが必要です。 この場合は、バージョン 1.0 が既に組み込まれていると、システムは Comp\_MyVSPackage.dll 更新済みのコンポーネントを上書きし、Comp\_VS2005\_Reg のコンポーネントの新機能 Feat\_VS2005 を追加するか選択します。  
  
> [!CAUTION]
>  VSPackage を複数のバージョンの間で共有するたびに [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], 、VSPackage の今後のリリースが以前のバージョンとの下位互換性を維持することが重要である [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 下位互換性を維持することはできませんが、サイド バイ サイドのプライベート VSPackages を使用する必要があります。 詳細については、「[Visual Studio の複数のバージョンをサポートします。](../../extensibility/supporting-multiple-versions-of-visual-studio.md)」を参照してください。  
  
 ![VS 共有 VS パッケージ更新イメージ](~/docs/extensibility/internals/media/vs_sharedpackageupdate.gif "VS\_SharedPackageUpdate")  
共有 vs パッケージ更新プログラムのインストーラー  
  
 このシナリオでは、小規模なアップグレードの Windows インストーラーのサポートを活用すること、新しい vs パッケージ インストーラーを表示します。 ユーザーが単にバージョン 1.1 をインストールし、バージョン 1.0 のアップグレードが行わします。 ただし、システムのバージョンは 1.0 する必要はありません。 同一のインストーラーは、バージョン 1.0 のないシステムでバージョン 1.1 がインストールされます。 この方法でマイナー アップグレードを提供することの利点は、ことは、アップグレードのインストーラーと全製品のインストーラーの開発作業を経由する必要はありません。 1 つのインストーラーは、両方のジョブを実行します。 セキュリティ修正プログラムまたはサービス パックが代わりに Windows インストーラーの修正プログラムを利用します。 詳細については、次を参照してください。 [修正プログラムの適用とアップグレード](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx)します。  
  
## シナリオ 3: サイド バイ サイド vs パッケージ  
 このシナリオでは、2 つの vs パッケージ インストーラー\-Visual Studio .NET 2003年のバージョンごとに 1 つと [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 各インストーラーに並行して、プライベート、VSPackage をインストール \(具体的にビルドし、特定のバージョンのインストールされている 1 つ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\)。 各 vs パッケージは、独自のコンポーネントです。 その結果、それぞれ個別に処理されると修正プログラムやメンテナンスを解放します。 VSPackage DLL は、バージョン固有では今すぐであるために、DLL と同じコンポーネントに、登録情報を含めるも安全です。  
  
 ![VS サイド バイ サイド VS パッケージ グラフィック](~/docs/extensibility/internals/media/vs_sbys_package.gif "VS\_SbyS\_Package")  
サイド バイ サイド vs パッケージ インストーラー  
  
 各インストーラーには、2 つのインストーラーの間で共有されるコードも含まれています。 共有コードが共通の場所にインストールされている場合両方の .msi ファイルをインストールする、インストール共有コード 1 回だけです。 2 番目のインストーラーには、コンポーネントの参照カウントだけインクリメントします。 参照カウントが vspackages にあるのいずれかがアンインストールされると、共有コードは引き続き他の VSPackage の実現します。 2 番目の VSPackage がもアンインストールされた場合は、共有コードが削除されます。  
  
## シナリオ 4: サイド バイ サイド vs パッケージ更新  
 このシナリオに対して、VSPackage で [!INCLUDE[vsprvslong](../../code-quality/includes/vsprvslong_md.md)] を検出しましたからセキュリティの脆弱性とする必要があります、更新プログラムを発行します。 シナリオ 2 と同様に、既存のインストールをセキュリティ修正が含まれてできるだけでなく、場所に既にセキュリティ修正により新しいインストールの展開を更新するための新しい .msi ファイルを作成できます。  
  
 この場合は、VSPackage には、グローバル アセンブリ キャッシュ \(GAC\) にインストールされているマネージ VSPackage です。 セキュリティ修正プログラムを追加するため、再構築するときは、アセンブリのバージョン番号のリビジョン番号の部分を変更する必要があります。 登録情報原因で、以前のバージョンを上書きすると、新しいアセンブリ バージョン番号の [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 固定のアセンブリを読み込みます。  
  
 ![VS サイド バイ サイド VS パッケージ更新グラフィック](~/docs/extensibility/internals/media/vs_sbys_packageupdate.gif "VS\_SbyS\_PackageUpdate")  
サイド バイ サイド vs パッケージ更新プログラムのインストーラー  
  
 **注** サイド バイ サイド アセンブリの展開の詳細については、次を参照してください。 [展開の簡略化すると、.NET Framework と共に DLL Hell を解決する](http://msdn.microsoft.com/library/ms973843.aspx)します。  
  
## 参照  
 [Windows インストーラー](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Visual Studio の複数のバージョンをサポートします。](../../extensibility/supporting-multiple-versions-of-visual-studio.md)