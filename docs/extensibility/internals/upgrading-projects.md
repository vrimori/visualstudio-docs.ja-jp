---
title: プロジェクトのアップグレード |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb64d71a50cb59a3c981dd87695bbb685f793761
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="upgrading-projects"></a>プロジェクトのアップグレード
プロジェクトのモデルを 1 つのバージョンから変更[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]へ必要がありますプロジェクトおよびソリューション アップグレードすること、新しいバージョンで実行できるようにします。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]独自のプロジェクトのアップグレードのサポートを実装するために使用するインターフェイスを提供します。  
  
## <a name="upgrade-strategies"></a>アップグレードの戦略  
 アップグレードをサポートするためにプロジェクト システムの実装する必要がありますを定義して、アップグレード戦略を実装します。 方法を決定するのには、サイド バイ サイド (SxS) バックアップ、コピー バックアップ、またはその両方をサポートするために選択できます。  
  
-   SxS バックアップでは、プロジェクトがアップグレードする代わりに、たとえば、適切なファイルの名前サフィックスを追加".old という"必要なファイルのみをコピーすることを意味します。  
  
-   コピー バックアップでは、プロジェクトが、ユーザー指定のバックアップの場所へのすべてのプロジェクト項目をコピーすることを意味します。 元のプロジェクトの場所に関連するファイルはアップグレードされます。  
  
## <a name="how-upgrade-works"></a>機能をアップグレードする方法  
 以前のバージョンで作成されたソリューションと[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]は新バージョンにアップグレードする必要があるかどうかを決定するファイルのソリューション IDE チェックで開かれます。 アップグレードが必要な場合、**アップグレード ウィザード**アップグレード プロセスのすべての要素が自動的に起動します。  
  
 ソリューションでは、アップグレードする必要がある、そのアップグレードの戦略の場合は、各プロジェクト ファクトリを照会します。 戦略は、プロジェクト ファクトリが、コピーまたは SxS のバックアップをサポートしているかどうかを判断します。 情報を送信、**アップグレード ウィザード**をバックアップに必要な情報を収集し、ユーザーに適切なオプションを表示します。  
  
### <a name="multi-project-solutions"></a>マルチ プロジェクト ソリューション  
 場合は、ソリューションに複数のプロジェクトが含まれているし、アップグレードの戦略が異なる場合、プロジェクト ファクトリがアップグレード戦略をネゴシエートする必要があります SxS バックアップのみをサポートする C++ プロジェクトと Web プロジェクトのみバックアップ コピーをサポートするなどです。  
  
 ソリューションの各プロジェクト ファクトリの照会<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>です。 呼び出して<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A>グローバル プロジェクト ファイルをアップグレードする必要があるかどうかを参照して、サポートされているアップグレードの戦略を決定します。 **アップグレード ウィザード**呼び出されます。  
  
 ユーザーと、ウィザードの完了後に<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>は、実際のアップグレードを実行するには、各プロジェクト ファクトリに対して呼び出されます。 バックアップを容易に IVsProjectUpgradeViaFactory メソッドを提供、<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>サービスのアップグレード プロセスの詳細ログに記録します。 このサービスをキャッシュすることはできません。  
  
 すべての関連するグローバル ファイルを更新した後に各プロジェクト ファクトリは、プロジェクトのインスタンスを作成するを選択できます。 プロジェクトの実装をサポートする必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>です。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>すべての関連するプロジェクト項目を更新するメソッドが呼び出されます。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>メソッドが SVsUpgradeLogger サービスを提供していません。 このサービスを呼び出すことによって取得できます<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>です。  
  
## <a name="best-practices"></a>ベスト プラクティス  
 使用して、<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>編集する前にファイルを編集することができ、保存する前に保存できるかどうかをチェックするサービスです。 これによって、バックアップ、およびアップグレードの実装によってソース管理下にあるプロジェクト ファイル、ファイルの権限の不足などに処理します。  
  
 使用して、<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>バックアップのすべてのフェーズ中にサービスのアップグレード プロセスの成否についての情報にアップグレードするとします。  
  
 バックアップして、プロジェクトのアップグレードに関する詳細については、「コメントの IVsProjectUpgrade vsshell2.idl です。  
  
## <a name="upgrading-custom-projects"></a> カスタム プロジェクトのアップグレード
プロジェクト ファイルに永続化されている情報を、ご使用の製品の異なる Visual Studio バージョン間で変更する場合、プロジェクト ファイルの旧バージョンから新しいバージョンへのアップグレードをサポートする必要があります。 アップグレードに参加することをサポートするために、 **Visual Studio 変換ウィザード**、実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>インターフェイスです。 このインターフェイスにはコピーのアップグレードに使用できる機能しか含まれていません。 プロジェクトのアップグレードは、ソリューションを開くことの一部として行われます。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>インターフェイスはプロジェクト ファクトリによって実装またはプロジェクト ファクトリから取得可能な少なくともする必要があります。  
  
 従来の機能を使用する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>インターフェイスは、引き続きサポートされますが、概念的に開いているプロジェクトの一部として、プロジェクト システムをアップグレードします。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>によってインターフェイスが呼び出されるため、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境場合であっても、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>インターフェイスが呼び出されるかを実装します。 この方法では、使用できます。<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>コピーを実装し、プロジェクトのアップグレードの一部にしかし、での一括 (通常は新しい場所) を実行する作業の残りの部分を委任する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>インターフェイスです。  
  
 実装のサンプルについて<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>を参照してください[VSSDK のサンプル](http://aka.ms/vs2015sdksamples)です。  
  
 プロジェクトのアップグレードに伴って次の状況が発生します。  
  
-   プロジェクトがサポートできるものよりもファイルの形式が新しい場合、そのことを示すエラーを返す必要があります。 これは、古いバージョン製品にはバージョンを確認するコードが含まれていると仮定します。  
  
-   場合、<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>でフラグが指定されて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>メソッド、アップグレードがしようとするプロジェクトを開く前に、インプレース アップグレードとして実装されます。  
  
-   場合、<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>でフラグが指定されて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>メソッド、アップグレードはコピーのアップグレードとして実装します。  
  
-   場合、<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>でフラグが指定されて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>を呼び出すには、ユーザーに、プロジェクトが開かれた後に、インプレース アップグレードとしてプロジェクト ファイルをアップグレードする環境で求められて、します。 たとえば、ユーザーが古いバージョンのソリューションを開いた場合、環境からユーザーに対してアップグレードを促すダイアログが表示されます。  
  
-   場合、<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>でフラグが指定されていない、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>を呼び出すには、プロジェクト ファイルをアップグレードするユーザーを要求する必要があります。  
  
     以下は、アップグレードのプロンプト メッセージの例です。  
  
     "プロジェクト '%1' は、古いバージョンの Visual Studio で作成されています。 このバージョンの Visual Studio でこのプロジェクトを開くと、Visual Studio の以前のバージョンでは開くことができなくなる場合があります。 続行してこのプロジェクトを開きますか?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>IVsProjectUpgradeViaFactory を実装するには  
  
1.  メソッドを実装して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>インターフェイス、特に、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>メソッド プロジェクト ファクトリの実装にしたり、その実装は、プロジェクト ファクトリの実装から呼び出すことです。  
  
2.  ソリューションを開くことの一部として、インプレース アップグレードを実行する場合は、フラグを指定します。<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>として、`VSPUVF_FLAGS`内のパラメーター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>実装します。  
  
3.  ソリューションを開くことの一部として、インプレース アップグレードを実行する場合は、フラグを指定します。<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>として、`VSPUVF_FLAGS`内のパラメーター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>実装します。  
  
4.  両方の手順 2. および 3.、実際のファイルのアップグレード手順についてを使用して<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>、」の説明に従って実装することができます、"実装`IVsProjectUpgade`"、後述の「またはへ実際のファイル アップグレードを委任する<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>です。  
  
5.  メソッドを使用して<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>アップグレードを投稿するには、Visual Studio 変換ウィザードを使用してユーザーのメッセージが関連します。  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> インターフェイスを使用して、任意の種類のプロジェクトのアップグレードの一部として実行する必要があるファイルのアップグレードを実装します。 このインターフェイスからは呼び出されません<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>、プロジェクト システムはメイン プロジェクト システムの一部であるファイルをアップグレードするためのメカニズムを直接に認識できない可能性がありますとして提供されます。 たとえば、コンパイラ関連のファイルとプロパティが、プロジェクト システムの残りを扱うのと同じ開発チームによって扱われない場合に、この状況が発生する可能性があります。  
  
### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade の実装  
 プロジェクト システムを実装する場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>のみ、それに参加できません、 **Visual Studio 変換ウィザード**です。 ただし、実装する場合でも、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>インターフェイス、委任することものファイル アップグレードを<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>実装します。  
  
#### <a name="to-implement-ivsprojectupgrade"></a>IVsProjectUpgrade を実装するには  
  
1.  ユーザーは、プロジェクトを開こうとしたとき、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>メソッドが呼び出される環境で、プロジェクトが開かれ、他のユーザーの前に、プロジェクトに対してアクションを実行できます。 ユーザーが既にされてメッセージが表示されたら、ソリューションをアップグレードする、<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>フラグが渡された、`grfUpgradeFlags`パラメーター。 ユーザー プロジェクトを開き、直接、そのような場合を使用する、**既存プロジェクトの追加**コマンドを次に、<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>フラグが渡されないと、プロジェクトをアップグレードするように求める必要があります。  
  
2.  応答、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>の呼び出しで、プロジェクトは、プロジェクト ファイルをアップグレードするかどうかを評価する必要があります。 プロジェクトはプロジェクトの種類を新しいバージョンにアップグレードする必要はありませんし、単純に返すことができるかどうか、<xref:Microsoft.VisualStudio.VSConstants.S_OK>フラグ。  
  
3.  プロジェクトがプロジェクトの種類を新しいバージョンにアップグレードする必要があるかどうかは、プロジェクト ファイルを呼び出すことによって変更できるかどうかを確認する必要がある、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>メソッドとの値に渡す<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>の`rgfQueryEdit`パラメーター。 次いでプロジェクトは次の操作を行う必要があります。  
  
    -   場合、`VSQueryEditResult`に返される値、`pfEditCanceled`パラメーターは<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>、プロジェクト ファイルを書き込むことがあるため、アップグレードを続行し、します。  
  
    -   場合、`VSQueryEditResult`に返される値、`pfEditCanceled`パラメーターは<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>と`VSQueryEditResult`値には、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>ビットが設定し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>アクセス許可の問題を自分のユーザーを解決するために、エラーを返す必要があります。 次いでプロジェクトは次の操作を行う必要があります。  
  
         呼び出しによってユーザーに、エラーを報告<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>を返すと、<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>エラー コードを<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>です。  
  
    -   場合、`VSQueryEditResult`値は<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>と`VSQueryEditResultFlags`値には、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>プロジェクト ファイルを呼び出すことによってチェック アウトする必要がありますし、ビットが設定<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>、 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...)。  
  
4.  場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>アウト、チェックインするファイルと最新バージョンを取得するには、プロジェクト ファイルでの呼び出しが発生し、プロジェクトをアンロードして再読み込みします。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>プロジェクトの別のインスタンスを作成した後、メソッドが再度呼び出さです。 この 2 つ目の呼び出しで、プロジェクト ファイルをディスクに書き込むことができるようになります。プロジェクトが、以前の形式でプロジェクト ファイルのコピーを保存してこれに拡張子 .OLD を付け、必要なアップグレードの変更を行い、新しい形式でプロジェクト ファイルを保存することをお勧めします。 ここでも、アップグレード プロセスの一部が失敗した場合、メソッド示す必要がありますエラーを返すことによって<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>です。 これにより、ソリューション エクスプローラーでプロジェクトがアンロードされます。  
  
     環境を内のケースで発生したすべてのプロセスを理解することが重要への呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>メソッド (値 reportonly を指定の指定) を返します、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>と<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>フラグ。  
  
5.  ユーザーは、プロジェクト ファイルを開こうとします。  
  
6.  環境の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>実装します。  
  
7.  場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>返します`true`、し、環境の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>実装します。  
  
8.  環境の呼び出し、 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> Project1 ファイルを開き、オブジェクトを初期化、プロジェクト、たとえばを実装します。  
  
9. プロジェクト ファイルをアップグレードする必要があるかどうかを判断するために、環境は `IVsProjectUpgrade::UpgradeProject` の実装を呼び出します。  
  
10. 呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>しの値で渡す<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>の`rgfQueryEdit`パラメーター。  
  
11. 環境を返します<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>の`VSQueryEditResult`と<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>ビットが設定されて`VSQueryEditResultFlags`です。  
  
12. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>実装`IVsQueryEditQuerySave::QueryEditFiles`(<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>、 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>)。  
  
 この呼び出しによって、プロジェクト ファイルを再度読み込む必要が生じるだけでなく、プロジェクト ファイルの新しいコピーがチェックアウトされ、最新バージョンが取得される可能性もあります。 この時点で、次の 2 つのいずれかが行われます。  
  
-   独自のプロジェクト再度読み込みを処理する場合、環境は、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) の実装です。 この呼び出しを受け取ったら、プロジェクトの最初のインスタンス (Project1) を再度読み込んで、プロジェクト ファイルのアップグレードを続けてください。 環境を返す場合は、独自のプロジェクト再度読み込みを処理することを知っている`true`の<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>)。  
  
-   独自のプロジェクト再度読み込み、処理しないかどうかは、戻る`false`の<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>)。 この例では、前に<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting、QEF_DisallowInMemoryEdits) を返します、環境が次のように、プロジェクト、Project2 などの別の新しいインスタンスを作成します。  
  
    1.  環境の呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A>最初プロジェクト オブジェクト (project1)、非アクティブ状態でしたがってこのオブジェクトを配置します。  
  
    2.  環境は、プロジェクトの 2 つ目のインスタンス (Project2) を作成するために、 `IVsProjectFactory::CreateProject` の実装を呼び出します。  
  
    3.  環境は、ファイルを開き、2 つ目のプロジェクト オブジェクト (Project2) を初期化するために、 `IPersistFileFormat::Load` の実装を呼び出します。  
  
    4.  環境は、プロジェクト オブジェクトをアップグレードする必要があるかどうかを判断するために、2 度目に `IVsProjectUpgrade::UpgradeProject` を呼び出します。 しかし、この呼び出しは、プロジェクトの新しい 2 番目のインスタンス (Project2) に対して行われます。 これは、ソリューションで開くプロジェクトです。  
  
        > [!NOTE]
        >  非アクティブの状態で、最初のプロジェクト (project1) を配置し、次に返す必要がありますインスタンスで<xref:Microsoft.VisualStudio.VSConstants.S_OK>最初の呼び出しから、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>実装します。  
  
    5.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>しの値で渡す<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>の`rgfQueryEdit`パラメーター。  
  
    6.  環境を返します<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>プロジェクト ファイルを書き込むことがあるため、アップグレードを続行します。  
  
 アップグレードに失敗した場合に返す<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>から`IVsProjectUpgrade::UpgradeProject`です。 アップグレードの必要がない場合、またはアップグレードしないことにした場合は、操作なしとして `IVsProjectUpgrade::UpgradeProject` 呼び出しを処理します。 返す場合<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>、プレース ホルダーのノードが、プロジェクトのソリューションに追加します。  
  
## <a name="upgrading-project-items"></a>プロジェクト項目のアップグレード
  
追加または実装していないプロジェクト システム内のアイテムを管理する場合は、プロジェクトのアップグレード プロセスに参加する必要があります。 Crystal Reports は、プロジェクト システムに追加できるアイテムの例を示します。  
  
 通常、プロジェクト項目の実装時は参照は、どのようなプロジェクトとどのようなその他のプロジェクトのプロパティがありますアップグレードの決定を行うを知っている必要があるため、既に完全にインスタンス化されると、アップグレードされたプロジェクトを活用するとします。  
  
### <a name="to-get-the-project-upgrade-notification"></a>プロジェクトのアップグレード通知を取得するには  
  
1.  設定、<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading>フラグ (vsshell80.idl で定義されている) プロジェクト項目の実装です。 これが原因で、プロジェクト項目を自動的に VSPackage を読み込むときに、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]シェル アップグレードの過程において、プロジェクト システムがあると判断します。  
  
2.  通知、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>インターフェイスを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A>メソッドです。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>インターフェイスは、プロジェクト システムの実装には、アップグレード操作が完了し、新しいアップグレードされたプロジェクトを作成した後に発生します。 シナリオによっては、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>インターフェイスが後に発生した、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>、または<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>メソッドです。  
  
### <a name="to-upgrade-the-project-item-files"></a>プロジェクト項目ファイルをアップグレードするには  
  
1.  プロジェクト項目の実装で、ファイルのバックアップ プロセスを慎重に管理する必要があります。 サイド バイ サイド バックアップでは、具体的には適用される場所、`fUpgradeFlag`のパラメーター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>メソッドに設定されている<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>に沿って".old"として指定されている側のファイルがバックアップされたファイルが置かれる、します。 プロジェクトのアップグレードされると、システム時刻よりも古いバックアップ ファイルは、古いものとして指定できます。 さらに、これを防止する具体的な手順を実行しない限り、このそれらを上書き可能性があります。  
  
2.  プロジェクト項目がプロジェクトのアップグレードの通知を取得時に、 **Visual Studio 変換ウィザード**は引き続き表示されます。 そのためのメソッドを使用する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>ウィザードの UI にアップグレード メッセージを提供するインターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト](../../extensibility/internals/projects.md)   
