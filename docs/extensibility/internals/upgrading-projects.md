---
title: プロジェクトのアップグレード |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a6f1d12e5735a0c285918c4621083bf6c1b6769
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949796"
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

プロジェクト ファイルに永続化されている情報を、ご使用の製品の異なる Visual Studio バージョン間で変更する場合、プロジェクト ファイルの旧バージョンから新しいバージョンへのアップグレードをサポートする必要があります。 参加するためのアップグレードをサポートするために、 **Visual Studio 変換ウィザード**、実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>インターフェイス。 このインターフェイスにはコピーのアップグレードに使用できる機能しか含まれていません。 プロジェクトのアップグレードは、ソリューションを開くことの一部として行われます。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> インターフェイスはプロジェクト ファクトリによって実装されます。あるいは、少なくともプロジェクト ファクトリから取得できる必要があります。

<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> インターフェイスを使用する従来の機能は引き続きサポートされますが、概念上はプロジェクトを開くことの一部としてプロジェクト システムをアップグレードします。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>インターフェイスが Visual Studio 環境のいてによって呼び出されるため、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>インターフェイスが呼び出されるかを実装します。 この方法なら、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> を使用してプロジェクトのコピーとアップグレードの部分だけを実装できます。そして、残りの作業を <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> インターフェイスが一括 (通常は新しい場所) で実行するよう委任できます。

実装のサンプルについて<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>を参照してください[VSSDK のサンプル](http://aka.ms/vs2015sdksamples)します。

プロジェクトのアップグレードに伴って次の状況が発生します。

-   プロジェクトがサポートできるものよりもファイルの形式が新しい場合、そのことを示すエラーを返す必要があります。 これは、古いバージョン製品にはのバージョンを確認するためのコードが含まれていると仮定します。

-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> フラグが <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> メソッドで指定された場合、アップグレードはプロジェクトを開く前に一括アップグレードとして実装されます。

-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> フラグが <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> メソッドで指定された場合、アップグレードはコピーのアップグレードとして実装されます。

-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> フラグが <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 呼び出しで指定された場合、プロジェクトが開かれた後に一括アップグレードとしてプロジェクト ファイルをアップグレードするよう、環境からユーザーに対してダイアログが既に表示されています。 たとえば、ユーザーが古いバージョンのソリューションを開いた場合、環境からユーザーに対してアップグレードを促すダイアログが表示されます。

-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> フラグが <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 呼び出しで指定されていない場合は、プロジェクト ファイルのアップグレードを促すダイアログをユーザーに対して表示する必要があります。

     以下は、アップグレードのプロンプト メッセージの例です。

     "プロジェクト '%1' は、古いバージョンの Visual Studio で作成されています。 このバージョンの Visual Studio でこのプロジェクトを開くと、Visual Studio の以前のバージョンでは開くことができなくなる場合があります。 続行してこのプロジェクトを開きますか?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>IVsProjectUpgradeViaFactory を実装するには

1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> インターフェイスのメソッド、特にプロジェクト ファクトリの実装で <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> メソッドを実装するか、その実装をプロジェクト ファクトリの実装から呼び出すことができるようにします。

2.  ソリューションを開くことの一部として一括アップグレードを行う場合は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> の実装の `VSPUVF_FLAGS` パラメーターとして、フラグ <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> を指定します。

3.  ソリューションを開くことの一部として一括アップグレードを行う場合は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> の実装の `VSPUVF_FLAGS` パラメーターとして、フラグ <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> を指定します。

4.  手順 2 と手順 3 の両方で、実際のファイルのアップグレードの手順は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> を使用して、「`IVsProjectUpgade` の実装」のセクションの説明どおりに実装できます。あるいは、実際のファイル アップグレードを <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> に委任できます。

5.  Visual Studio 移行ウィザードを使用するユーザーに、アップグレードに関連したメッセージをポストするために、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> メソッドを使用します。

6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> インターフェイスは、プロジェクト アップグレードの一部として実行する必要がある種類のファイル アップグレードを実装するために使用します。 このインターフェイスは、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> から呼び出されることはありませんが、プロジェクト システムの一部であるファイルをアップグレードするメカニズムとして提供されます。しかし、主なプロジェクト システムはこれを直接に認識しない場合があります。 たとえば、コンパイラ関連のファイルとプロパティが、プロジェクト システムの残りを扱うのと同じ開発チームによって扱われない場合に、この状況が発生する可能性があります。

### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade の実装

プロジェクト システムを実装する場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>に参加しないできますのみ、 **Visual Studio 変換ウィザード**します。 ただし、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> インターフェイスを実装しても、ファイルのアップグレードを <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> の実装に委任することはできます。

#### <a name="to-implement-ivsprojectupgrade"></a>IVsProjectUpgrade を実装するには

1.  ユーザーがプロジェクトを開こうとするときには、プロジェクトが開かれてから、プロジェクト上で他の何らかのユーザー アクションが実行できるようになるまでの間に、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> メソッドが環境によって呼び出されます。 既にユーザーに対してソリューションをアップグレードするよう促すダイアログが表示された場合、<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> フラグが `grfUpgradeFlags` のパラメーターで渡されます。 ユーザー、プロジェクトを開く、直接このような場合を使用して同様、**既存プロジェクトの追加**コマンド、<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE>フラグが渡されないと、プロジェクトをアップグレードするユーザーに確認する必要があります。

2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> の呼び出しに応じて、プロジェクトはプロジェクト ファイルがアップグレードされているかどうかを評価する必要があります。 プロジェクトがプロジェクトの種類を新しいバージョンにアップグレードする必要がない場合は、単に <xref:Microsoft.VisualStudio.VSConstants.S_OK> フラグを返すことができます。

3.  プロジェクトがプロジェクトの種類を新しいバージョンにアップグレードする必要がある場合は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> メソッドを呼び出し、`rgfQueryEdit` パラメーターに値 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> を渡して、プロジェクト ファイルを変更できるかどうかを確認する必要があります。 次いでプロジェクトは次の操作を行う必要があります。

    -   `pfEditCanceled` パラメーターで返される `VSQueryEditResult` 値が <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> である場合、プロジェクト ファイルに書き込みができるので、アップグレードを続けることができます。

    -   `pfEditCanceled` パラメーターで返される `VSQueryEditResult` 値が <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> であり、`VSQueryEditResult` 値に <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> のビットが設定されている場合、ユーザーがアクセス許可の問題を自分で解決する必要があるため、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> はエラーを返す必要があります。 次いでプロジェクトは次の操作を行う必要があります。

         呼び出すことによって、ユーザーに、エラーを報告<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>戻って、<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>エラー コードを<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>します。

    -   `VSQueryEditResult` 値が <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> で、`VSQueryEditResultFlags` 値に <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> ビットが設定されている場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>、...) を呼び出してプロジェクト ファイルをチェックアウトする必要があります。

4.  プロジェクト ファイルで <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> が呼び出されてファイルがチェックアウトされ、最新バージョンが取得されると、プロジェクトがアンロードされて再度読み込まれます。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> メソッドは、プロジェクトの別のインスタンスが作成された後で再び呼び出されます。 この 2 つ目の呼び出しで、プロジェクト ファイルをディスクに書き込むことができるようになります。プロジェクトが、以前の形式でプロジェクト ファイルのコピーを保存してこれに拡張子 .OLD を付け、必要なアップグレードの変更を行い、新しい形式でプロジェクト ファイルを保存することをお勧めします。 アップグレード プロセスのいずれかの部分が失敗した場合は、先と同様、メソッドは <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> を返して失敗したことを示す必要があります。 これにより、ソリューション エクスプローラーでプロジェクトがアンロードされます。

     <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> メソッドの呼び出し (値 ReportOnly を指定) が <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> および <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> フラグを返すケースで環境に発生するプロセス全体を理解することは重要です。

5.  ユーザーは、プロジェクト ファイルを開こうとします。

6.  環境は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> の実装を呼び出します。

7.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> が `true` を返す場合、環境は <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> の実装を呼び出します。

8.  環境は <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> の実装を呼び出してファイルを開き、プロジェクト オブジェクト (Project1 など) を初期化します。

9. プロジェクト ファイルをアップグレードする必要があるかどうかを判断するために、環境は `IVsProjectUpgrade::UpgradeProject` の実装を呼び出します。

10. <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> を呼び出し、値 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> を `rgfQueryEdit` のパラメーターに渡します。

11. 環境は `VSQueryEditResult` に関して <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> を返し、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> ビットが `VSQueryEditResultFlags` に設定されます。

12. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> の実装が `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>) を呼び出します。

この呼び出しによって、プロジェクト ファイルを再度読み込む必要が生じるだけでなく、プロジェクト ファイルの新しいコピーがチェックアウトされ、最新バージョンが取得される可能性もあります。 この時点で、次の 2 つのいずれかが行われます。

-   独自のプロジェクトの再度読み込みを処理する場合、環境は <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) の実装を呼び出します。 この呼び出しを受け取ったら、プロジェクトの最初のインスタンス (Project1) を再度読み込んで、プロジェクト ファイルのアップグレードを続けてください。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>) で `true` を返せば、環境は独自のプロジェクト再度読み込みが処理されることがわかります。

-   独自のプロジェクト再度読み込みを処理しない場合は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>) で `false` を返してください。 この場合は、前に<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting、QEF_DisallowInMemoryEdits) を返します、環境が次のように Project2 など、プロジェクトのもう 1 つの新しいインスタンスを作成します。

    1.  環境は、最初のプロジェクト オブジェクト (Project1) で <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> を呼び出し、このオブジェクトを非アクティブ状態にします。

    2.  環境は、プロジェクトの 2 つ目のインスタンス (Project2) を作成するために、 `IVsProjectFactory::CreateProject` の実装を呼び出します。

    3.  環境は、ファイルを開き、2 つ目のプロジェクト オブジェクト (Project2) を初期化するために、 `IPersistFileFormat::Load` の実装を呼び出します。

    4.  環境は、プロジェクト オブジェクトをアップグレードする必要があるかどうかを判断するために、2 度目に `IVsProjectUpgrade::UpgradeProject` を呼び出します。 しかし、この呼び出しは、プロジェクトの新しい 2 番目のインスタンス (Project2) に対して行われます。 これは、ソリューションで開くプロジェクトです。

        > [!NOTE]
        > 最初のプロジェクト (Project1) を非アクティブ状態にした場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> の実装への最初の呼び出しから <xref:Microsoft.VisualStudio.VSConstants.S_OK> を返す必要があります。

    5.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> を呼び出し、値 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> を `rgfQueryEdit` のパラメーターに渡します。

    6.  環境は <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> を返し、プロジェクト ファイルを書き込める状態になったので、アップグレードを続けることができます。

アップグレードに失敗した場合は、`IVsProjectUpgrade::UpgradeProject` から <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> を返してください。 アップグレードの必要がない場合、またはアップグレードしないことにした場合は、操作なしとして `IVsProjectUpgrade::UpgradeProject` 呼び出しを処理します。 <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> を返すと、プレースホルダーのノードがプロジェクトのソリューションに追加されます。

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