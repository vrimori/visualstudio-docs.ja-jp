---
title: プロジェクトのアップグレード |Microsoft Docs
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
ms.openlocfilehash: ea5c29819d0035e45f97122fd108ea1f51d60806
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057535"
---
# <a name="upgrading-projects"></a>プロジェクトのアップグレード

次の 1 つのバージョンの Visual Studio からプロジェクト モデルの変更は、新しいバージョンで実行できるようにプロジェクトおよびソリューションをアップグレードする必要があります。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]独自のプロジェクトのアップグレードのサポートを実装するために使用できるインターフェイスを提供します。

## <a name="upgrade-strategies"></a>アップグレードの戦略

アップグレードをサポートするには、プロジェクト システムの実装が定義し、アップグレードの戦略を実装する必要があります。 戦略を決定するのには、サイド バイ サイド (SxS) のバックアップ、バックアップのコピー、またはその両方をサポートするために選択できます。

-   SxS バックアップでは、プロジェクトがアップグレード インプレースでは、たとえば、適切なファイル名サフィックスを追加".old"必要があるファイルのみをコピーを意味します。

-   コピー バックアップでは、プロジェクトが、ユーザーが指定したバックアップの場所へのすべてのプロジェクト項目をコピーすることを意味します。 元のプロジェクトの場所に関連するファイルは、アップグレードします。

## <a name="how-upgrade-works"></a>アップグレードする方法の動作

新しいバージョンの Visual Studio の以前のバージョンで作成されたソリューションを開くと、IDE は、ソリューション ファイルをアップグレードする必要があるかどうかは決まりますをチェックします。 アップグレードが必要な場合、**アップグレード ウィザード**がアップグレードのプロセスを順を追ってに自動的に起動します。

ソリューションでは、アップグレードする必要があります、そのアップグレードの戦略の場合は、各プロジェクト ファクトリを照会します。 戦略は、プロジェクト ファクトリが、コピーまたは SxS のバックアップをサポートしているかどうかを判断します。 情報に送信、**アップグレード ウィザード**バックアップに必要な情報を収集およびユーザーに適切なオプションを表示します。

### <a name="multi-project-solutions"></a>マルチ プロジェクト ソリューション

ソリューションには、複数のプロジェクトが含まれています。 プロジェクト ファクトリがアップグレード戦略をネゴシエートする必要がありますのみ SxS のバックアップをサポートする C++ プロジェクトと Web プロジェクトのみバックアップ コピーをサポートするなど、アップグレードの戦略が異なる場合。

ソリューションのクエリの各プロジェクト ファクトリ<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>します。 呼び出して<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A>グローバル プロジェクト ファイルのアップグレードに必要なかどうかを参照して、サポートされているアップグレードの戦略を決定します。 **アップグレード ウィザード**呼び出されます。

ユーザーが、ウィザードを完了した後<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>は実際のアップグレードを実行するには、各プロジェクト ファクトリに対して呼び出されます。 IVsProjectUpgradeViaFactory メソッドを提供するバックアップを容易に、<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>アップグレード プロセスの詳細を記録するサービス。 このサービスをキャッシュすることはできません。

関連するすべてのグローバル ファイルを更新した後は、各プロジェクト ファクトリは、プロジェクトをインスタンス化を選択できます。 プロジェクトの実装をサポートする必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>します。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>すべての関連するプロジェクト項目のアップグレードにはメソッドが呼び出されます。

> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>メソッドが SVsUpgradeLogger サービスを提供できません。 このサービスを呼び出すことによって取得できる<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>します。

## <a name="best-practices"></a>ベスト プラクティス

使用して、<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>編集する前にファイルを編集することができ、保存する前に保存できるかどうかにチェックするサービス。 これにより、バックアップと、アップグレードの実装がソース管理下にあるプロジェクト ファイル、権限の不足などのファイルを処理します。

使用して、<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>バックアップのすべてのフェーズ中にサービスし、アップグレード、アップグレード処理の成否に関する情報を提供します。

バックアップして、プロジェクトのアップグレードの詳細については、コメントを参照して IVsProjectUpgrade の vsshell2.idl でします。

## <a name="upgrading-custom-projects"></a> カスタム プロジェクトのアップグレード

プロジェクト ファイルに永続化されている情報を、ご使用の製品の異なる Visual Studio バージョン間で変更する場合、プロジェクト ファイルの旧バージョンから新しいバージョンへのアップグレードをサポートする必要があります。 参加するためのアップグレードをサポートするために、 **Visual Studio 変換ウィザード**、実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>インターフェイス。 このインターフェイスにはコピーのアップグレードに使用できる機能しか含まれていません。 プロジェクトのアップグレードは、ソリューションを開くことの一部として行われます。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>インターフェイスは、プロジェクト ファクトリによって実装されますまたはプロジェクト ファクトリから取得可能な以上である必要があります。

使用する従来の機能、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>インターフェイスは、引き続きサポートされますが、概念的には、開いているプロジェクトの一部として、プロジェクト システムをアップグレードします。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>インターフェイスが Visual Studio 環境のいてによって呼び出されるため、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>インターフェイスが呼び出されるかを実装します。 このアプローチでは、使用できます。<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>コピーを実装し、プロジェクトのアップグレードの一部にしか、残りのインプレース (場合によっては新しい場所) で実行する作業を委任し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>インターフェイス。

実装のサンプルについて<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>を参照してください[VSSDK のサンプル](http://aka.ms/vs2015sdksamples)します。

プロジェクトのアップグレードに伴って次の状況が発生します。

-   プロジェクトがサポートできるものよりもファイルの形式が新しい場合、そのことを示すエラーを返す必要があります。 これは、古いバージョン製品にはのバージョンを確認するためのコードが含まれていると仮定します。

-   場合、<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>でフラグが指定されて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>メソッドでは、アップグレードは、プロジェクトを開く前に、インプレース アップグレードとして実装することです。

-   場合、<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP>でフラグが指定されて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>メソッド、アップグレードはコピーのアップグレードとして実装されます。

-   場合、<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE>でフラグが指定されて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>呼び出すには、そのプロジェクトが開かれた後に、インプレース アップグレードとしてプロジェクト ファイルをアップグレードする環境で、ユーザーに求められています。 たとえば、ユーザーが古いバージョンのソリューションを開いた場合、環境からユーザーに対してアップグレードを促すダイアログが表示されます。

-   場合、<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE>でフラグが指定されていない、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>呼び出すには、その後、プロジェクト ファイルをアップグレードするようユーザーにダイアログを表示する必要があります。

     以下は、アップグレードのプロンプト メッセージの例です。

     "プロジェクト '%1' は、古いバージョンの Visual Studio で作成されています。 このバージョンの Visual Studio でこのプロジェクトを開くと、Visual Studio の以前のバージョンでは開くことができなくなる場合があります。 続行してこのプロジェクトを開きますか?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>IVsProjectUpgradeViaFactory を実装するには

1.  メソッドを実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>具体的には、インターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>プロジェクト ファクトリの実装のメソッドか、実装をプロジェクト ファクトリの実装から呼び出すことです。

2.  ソリューションを開くことの一部として、インプレース アップグレードを実行する場合は、フラグを指定します。<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>として、`VSPUVF_FLAGS`パラメーター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>実装します。

3.  ソリューションを開くことの一部として、インプレース アップグレードを実行する場合は、フラグを指定します。<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP>として、`VSPUVF_FLAGS`パラメーター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>実装します。

4.  両方の手順 2 および 3、実際のファイル アップグレードを使用して、手順<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>、」の説明に従って実装することができます、"実装`IVsProjectUpgade`"セクションまたはへの実際のファイル アップグレードを委任する<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>します。

5.  メソッドを使用して<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>アップグレードを投稿する Visual Studio 移行ウィザードを使用してユーザーのメッセージに関連します。

6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> インターフェイスは、任意の種類のプロジェクトのアップグレードの一部として実行する必要があるファイルのアップグレードを実装するために使用されます。 このインターフェイスからは呼び出されません<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>は、プロジェクト システムが、メイン プロジェクト システムの一部であるファイルをアップグレードするためのメカニズムを直接に認識できない可能性がありますとして提供されます。 たとえば、コンパイラ関連のファイルとプロパティが、プロジェクト システムの残りを扱うのと同じ開発チームによって扱われない場合に、この状況が発生する可能性があります。

### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade の実装

プロジェクト システムを実装する場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>に参加しないできますのみ、 **Visual Studio 変換ウィザード**します。 ただし、実装する場合でも、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>インターフェイスへのファイル アップグレードも委任できます<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>実装します。

#### <a name="to-implement-ivsprojectupgrade"></a>IVsProjectUpgrade を実装するには

1.  ユーザーがプロジェクトを開いてしようとした場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>メソッドは、プロジェクトを開くし、プロジェクトで、他のユーザーの前にアクションを実行する、環境によって呼び出されます。 ユーザーが既にされてメッセージが表示されたら、ソリューションをアップグレードする、<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE>フラグが渡された、`grfUpgradeFlags`パラメーター。 ユーザー、プロジェクトを開く、直接このような場合を使用して同様、**既存プロジェクトの追加**コマンド、<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE>フラグが渡されないと、プロジェクトをアップグレードするユーザーに確認する必要があります。

2.  応答、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>呼び出し、プロジェクトは、プロジェクト ファイルをアップグレードするかどうかを評価する必要があります。 プロジェクトがプロジェクトの種類を新しいバージョンにアップグレードする必要はありませんし、単に返すことができるかどうか、<xref:Microsoft.VisualStudio.VSConstants.S_OK>フラグ。

3.  プロジェクトがプロジェクトの種類を新しいバージョンにアップグレードする必要があるかどうかは、プロジェクト ファイルを呼び出すことによって変更できるかどうかを判断する必要がありますが、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>メソッドとの値を渡すこと<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>の`rgfQueryEdit`パラメーター。 次いでプロジェクトは次の操作を行う必要があります。

    -   場合、`VSQueryEditResult`で返された値、`pfEditCanceled`パラメーターが<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>、プロジェクト ファイルが書き込まれるので、アップグレードを続行できます。

    -   場合、`VSQueryEditResult`で返された値、`pfEditCanceled`パラメーターが<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK>と`VSQueryEditResult`値が、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc>ビットが設定し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>アクセス許可の問題を自分のユーザーを解決するために、エラーを返す必要があります。 次いでプロジェクトは次の操作を行う必要があります。

         呼び出すことによって、ユーザーに、エラーを報告<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>戻って、<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>エラー コードを<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>します。

    -   場合、`VSQueryEditResult`値は<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK>と`VSQueryEditResultFlags`値が、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>プロジェクト ファイルを呼び出すことによってチェック アウトする必要がありますし、ビットが設定、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>、 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...)。

4.  場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>プロジェクト ファイルでの呼び出しと、チェック アウトするファイルと最新のバージョンを取得するには、その後、プロジェクトのアンロードおよび再読み込みします。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>プロジェクトの別のインスタンスが作成されると、メソッドが再度呼び出さします。 この 2 つ目の呼び出しで、プロジェクト ファイルをディスクに書き込むことができるようになります。プロジェクトが、以前の形式でプロジェクト ファイルのコピーを保存してこれに拡張子 .OLD を付け、必要なアップグレードの変更を行い、新しい形式でプロジェクト ファイルを保存することをお勧めします。 ここでも、アップグレード プロセスの一部が失敗した場合、メソッド示す必要がありますエラーを返すことによって<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>します。 これにより、ソリューション エクスプローラーでプロジェクトがアンロードされます。

     環境を内のケースで発生するプロセス全体を理解することが重要への呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>メソッド (値 ReportOnly を指定する) を返します、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK>と<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>フラグ。

5.  ユーザーは、プロジェクト ファイルを開こうとします。

6.  環境は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>実装します。

7.  場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>返します`true`、し、環境は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>実装します。

8.  環境は、 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> Project1 ファイルを開き、たとえば、プロジェクトのオブジェクトの初期化を実装します。

9. プロジェクト ファイルをアップグレードする必要があるかどうかを判断するために、環境は `IVsProjectUpgrade::UpgradeProject` の実装を呼び出します。

10. 呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>の値を渡すと<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly>の`rgfQueryEdit`パラメーター。

11. 環境を返します<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK>の`VSQueryEditResult`と<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>ビットが設定されて`VSQueryEditResultFlags`します。

12. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>実装`IVsQueryEditQuerySave::QueryEditFiles`(<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>、 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>)。

この呼び出しによって、プロジェクト ファイルを再度読み込む必要が生じるだけでなく、プロジェクト ファイルの新しいコピーがチェックアウトされ、最新バージョンが取得される可能性もあります。 この時点で、次の 2 つのいずれかが行われます。

-   独自のプロジェクト再度読み込みを処理する場合、環境は、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) の実装。 この呼び出しを受け取ったら、プロジェクトの最初のインスタンス (Project1) を再度読み込んで、プロジェクト ファイルのアップグレードを続けてください。 環境値を返す場合は、独自のプロジェクト再度読み込みを処理することを知っている`true`の<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>)。

-   独自のプロジェクト再度読み込みを処理しないかどうかは、戻る`false`の<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>)。 この場合は、前に<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting、QEF_DisallowInMemoryEdits) を返します、環境が次のように Project2 など、プロジェクトのもう 1 つの新しいインスタンスを作成します。

    1.  環境は<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A>で、最初プロジェクト オブジェクト (project1)、非アクティブ状態のためこのオブジェクトを配置します。

    2.  環境は、プロジェクトの 2 つ目のインスタンス (Project2) を作成するために、 `IVsProjectFactory::CreateProject` の実装を呼び出します。

    3.  環境は、ファイルを開き、2 つ目のプロジェクト オブジェクト (Project2) を初期化するために、 `IPersistFileFormat::Load` の実装を呼び出します。

    4.  環境は、プロジェクト オブジェクトをアップグレードする必要があるかどうかを判断するために、2 度目に `IVsProjectUpgrade::UpgradeProject` を呼び出します。 しかし、この呼び出しは、プロジェクトの新しい 2 番目のインスタンス (Project2) に対して行われます。 これは、ソリューションで開くプロジェクトです。

        > [!NOTE]
        > インスタンスには、最初のプロジェクト (project1) が非アクティブの状態に配置し、返す必要がありますで<xref:Microsoft.VisualStudio.VSConstants.S_OK>最初の呼び出しから、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>実装します。

    5.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>の値を渡すと<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly>の`rgfQueryEdit`パラメーター。

    6.  環境を返します<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>プロジェクト ファイルが書き込まれるので、アップグレードを続けるとします。

アップグレードに失敗した場合に返す<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>から`IVsProjectUpgrade::UpgradeProject`します。 アップグレードの必要がない場合、またはアップグレードしないことにした場合は、操作なしとして `IVsProjectUpgrade::UpgradeProject` 呼び出しを処理します。 値を返す場合<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>、プレース ホルダーのノードは、プロジェクトのソリューションに追加されます。

## <a name="upgrading-project-items"></a>プロジェクト項目のアップグレード

追加またはを実装していないプロジェクト システム内の項目を管理する場合は、プロジェクトのアップグレード プロセスに参加する必要があります。 Crystal Reports は、プロジェクト システムに追加できる項目の例を示します。

通常、プロジェクト項目の実装者は、参照は、どのようなプロジェクトとその他のプロジェクトのプロパティは何がアップグレードの決定を行う必要があるため、既に完全インスタンス化とアップグレードされたプロジェクトを活用します。

### <a name="to-get-the-project-upgrade-notification"></a>プロジェクトのアップグレード通知を取得するには

1.  設定、<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading>プロジェクト項目の実装では、(vsshell80.idl で定義されている) フラグ。 これにより、プロジェクト システムは、アップグレードの過程において、Visual Studio シェルと判断した場合、自動読み込みを VSPackage プロジェクト項目。

2.  お勧め、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>インターフェイスを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A>メソッド。

3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>プロジェクト システムの実装のアップグレード操作が完了したら、新しいアップグレードされたプロジェクトが作成した後、インターフェイスが発生します。 シナリオによっては、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>インターフェイスが発生した後、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>、または<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>メソッド。

### <a name="to-upgrade-the-project-item-files"></a>プロジェクト項目のファイルをアップグレードするには

1.  プロジェクト項目の実装で、ファイルのバックアップ プロセスを慎重に管理する必要があります。 サイド バイ サイドでバックアップの場合は、具体的には適用される場所、`fUpgradeFlag`のパラメーター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>メソッドに設定されている<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>".old"として指定される側のファイルにバックアップされたファイルを配置する場所。 プロジェクトがアップグレードされたシステム時刻よりも古いバックアップ ファイルは、古いものとして指定できます。 さらに、これを防ぐために特定の手順を実行していない限り、このを上書き可能性があります。

2.  プロジェクト項目がプロジェクトのアップグレードの通知を取得時に、 **Visual Studio 変換ウィザード**が引き続き表示されます。 そのためのメソッドを使用する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>ウィザードの UI にアップグレード メッセージを提供するインターフェイス。

## <a name="see-also"></a>関連項目

- [プロジェクト](../../extensibility/internals/projects.md)