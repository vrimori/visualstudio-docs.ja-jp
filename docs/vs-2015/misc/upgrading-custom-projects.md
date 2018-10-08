---
title: カスタム プロジェクトのアップグレード |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: douge
ms.openlocfilehash: 5c3fd31cfc7cfbf3f7dd687d38483f5bb62703ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539954"
---
# <a name="upgrading-custom-projects"></a>カスタム プロジェクトのアップグレード
プロジェクト ファイルに永続化されている情報を、ご使用の製品の異なる Visual Studio バージョン間で変更する場合、プロジェクト ファイルの旧バージョンから新しいバージョンへのアップグレードをサポートする必要があります。 参加するためのアップグレードをサポートするために、 **Visual Studio 変換ウィザード**、実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>インターフェイス。 このインターフェイスにはコピーのアップグレードに使用できる機能しか含まれていません。 プロジェクトのアップグレードは、ソリューションを開くことの一部として行われます。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>インターフェイスは、プロジェクト ファクトリによって実装されますまたはプロジェクト ファクトリから取得可能な以上である必要があります。  
  
 使用する従来の機能、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>インターフェイスは、引き続きサポートされますが、概念的には、開いているプロジェクトの一部として、プロジェクト システムをアップグレードします。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>によってインターフェイスが呼び出されるため、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]環境の場合でも、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>インターフェイスが呼び出されるかを実装します。 このアプローチでは、使用できます。<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>コピーを実装し、プロジェクトのアップグレードの一部にしか、残りのインプレース (場合によっては新しい場所) で実行する作業を委任し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>インターフェイス。  
  
 実装のサンプルについて<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>を参照してください[VSSDK のサンプル](../misc/vssdk-samples.md)します。  
  
 プロジェクトのアップグレードに伴って次の状況が発生します。  
  
-   プロジェクトがサポートできるものよりもファイルの形式が新しい場合、そのことを示すエラーを返す必要があります。 これは、ご使用の製品の古いバージョン (Visual Studio .NET 2003 など) にバージョンを確認するためのコードがあることを前提としています。  
  
-   場合、<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>でフラグが指定されて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>メソッドでは、アップグレードは、プロジェクトを開く前に、インプレース アップグレードとして実装することです。  
  
-   場合、<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>でフラグが指定されて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>メソッド、アップグレードはコピーのアップグレードとして実装されます。  
  
-   場合、<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>でフラグが指定されて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>呼び出すには、そのプロジェクトが開かれた後に、インプレース アップグレードとしてプロジェクト ファイルをアップグレードする環境で、ユーザーに求められています。 たとえば、ユーザーが古いバージョンのソリューションを開いた場合、環境からユーザーに対してアップグレードを促すダイアログが表示されます。  
  
-   場合、<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>でフラグが指定されていない、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>呼び出すには、その後、プロジェクト ファイルをアップグレードするようユーザーにダイアログを表示する必要があります。  
  
     以下は、アップグレードのプロンプト メッセージの例です。  
  
     "プロジェクト '%1' は、古いバージョンの Visual Studio で作成されています。 このバージョンの Visual Studio でこのプロジェクトを開くと、Visual Studio の以前のバージョンでは開くことができなくなる場合があります。 続行してこのプロジェクトを開きますか?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>IVsProjectUpgradeViaFactory を実装するには  
  
1.  メソッドを実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>具体的には、インターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>プロジェクト ファクトリの実装のメソッドか、実装をプロジェクト ファクトリの実装から呼び出すことです。  
  
2.  ソリューションを開くことの一部として、インプレース アップグレードを実行する場合は、フラグを指定します。<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>として、`VSPUVF_FLAGS`パラメーター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>実装します。  
  
3.  ソリューションを開くことの一部として、インプレース アップグレードを実行する場合は、フラグを指定します。<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>として、`VSPUVF_FLAGS`パラメーター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>実装します。  
  
4.  両方の手順 2 および 3、実際のファイル アップグレードを使用して、手順<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>、」の説明に従って実装することができます、"実装`IVsProjectUpgade`"セクションまたはへの実際のファイル アップグレードを委任する<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>します。  
  
5.  メソッドを使用して<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>アップグレードを投稿する Visual Studio 移行ウィザードを使用してユーザーのメッセージに関連します。  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> インターフェイスは、任意の種類のプロジェクトのアップグレードの一部として実行する必要があるファイルのアップグレードを実装するために使用されます。 このインターフェイスからは呼び出されません<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>は、プロジェクト システムが、メイン プロジェクト システムの一部であるファイルをアップグレードするためのメカニズムを直接に認識できない可能性がありますとして提供されます。 たとえば、コンパイラ関連のファイルとプロパティが、プロジェクト システムの残りを扱うのと同じ開発チームによって扱われない場合に、この状況が発生する可能性があります。  
  
## <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade の実装  
 プロジェクト システムを実装する場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>に参加しないできますのみ、 **Visual Studio 変換ウィザード**します。 ただし、実装する場合でも、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>インターフェイスへのファイル アップグレードも委任できます<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>実装します。  
  
#### <a name="to-implement-ivsprojectupgrade"></a>IVsProjectUpgrade を実装するには  
  
1.  ユーザーがプロジェクトを開いてしようとした場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>メソッドは、プロジェクトを開くし、プロジェクトで、他のユーザーの前にアクションを実行する、環境によって呼び出されます。 ユーザーが既にされてメッセージが表示されたら、ソリューションをアップグレードする、<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>フラグが渡された、`grfUpgradeFlags`パラメーター。 ユーザー、プロジェクトを開く、直接このような場合を使用して同様、**既存プロジェクトの追加**コマンド、<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>フラグが渡されないと、プロジェクトをアップグレードするユーザーに確認する必要があります。  
  
2.  応答、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>呼び出し、プロジェクトは、プロジェクト ファイルをアップグレードするかどうかを評価する必要があります。 プロジェクトがプロジェクトの種類を新しいバージョンにアップグレードする必要はありませんし、単に返すことができるかどうか、<xref:Microsoft.VisualStudio.VSConstants.S_OK>フラグ。  
  
3.  プロジェクトがプロジェクトの種類を新しいバージョンにアップグレードする必要があるかどうかは、プロジェクト ファイルを呼び出すことによって変更できるかどうかを判断する必要がありますが、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>メソッドとの値を渡すこと<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>の`rgfQueryEdit`パラメーター。 次いでプロジェクトは次の操作を行う必要があります。  
  
    -   場合、`VSQueryEditResult`で返された値、`pfEditCanceled`パラメーターが<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>、プロジェクト ファイルが書き込まれるので、アップグレードを続行できます。  
  
    -   場合、`VSQueryEditResult`で返された値、`pfEditCanceled`パラメーターが<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>と`VSQueryEditResult`値が、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>ビットが設定し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>アクセス許可の問題を自分のユーザーを解決するために、エラーを返す必要があります。 次いでプロジェクトは次の操作を行う必要があります。  
  
         呼び出すことによって、ユーザーに、エラーを報告<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>します。 戻って、<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>エラー コードを<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>します。  
  
    -   場合、`VSQueryEditResult`値は<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>と`VSQueryEditResultFlags`値が、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>プロジェクト ファイルを呼び出すことによってチェック アウトする必要がありますし、ビットが設定、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>、 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...)。  
  
4.  場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>プロジェクト ファイルでの呼び出しと、チェック アウトするファイルと最新のバージョンを取得するには、その後、プロジェクトのアンロードおよび再読み込みします。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>プロジェクトの別のインスタンスが作成されると、メソッドが再度呼び出さします。 この 2 つ目の呼び出しで、プロジェクト ファイルをディスクに書き込むことができるようになります。プロジェクトが、以前の形式でプロジェクト ファイルのコピーを保存してこれに拡張子 .OLD を付け、必要なアップグレードの変更を行い、新しい形式でプロジェクト ファイルを保存することをお勧めします。 ここでも、アップグレード プロセスの一部が失敗した場合、メソッド示す必要がありますエラーを返すことによって<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>します。 これにより、ソリューション エクスプローラーでプロジェクトがアンロードされます。  
  
     環境を内のケースで発生するプロセス全体を理解することが重要への呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>メソッド (値 ReportOnly を指定する) を返します、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>と<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>フラグ。  
  
5.  ユーザーは、プロジェクト ファイルを開こうとします。  
  
6.  環境は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>実装します。  
  
7.  場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>返します`true`、し、環境は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>実装します。  
  
8.  環境は、 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> Project1 ファイルを開き、たとえば、プロジェクトのオブジェクトの初期化を実装します。  
  
9. プロジェクト ファイルをアップグレードする必要があるかどうかを判断するために、環境は `IVsProjectUpgrade::UpgradeProject` の実装を呼び出します。  
  
10. 呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>の値を渡すと<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>の`rgfQueryEdit`パラメーター。  
  
11. 環境を返します<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>の`VSQueryEditResult`と<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>ビットが設定されて`VSQueryEditResultFlags`します。  
  
12. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>実装`IVsQueryEditQuerySave::QueryEditFiles`(<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>、 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>)。  
  
 この呼び出しによって、プロジェクト ファイルを再度読み込む必要が生じるだけでなく、プロジェクト ファイルの新しいコピーがチェックアウトされ、最新バージョンが取得される可能性もあります。 この時点で、次の 2 つのいずれかが行われます。  
  
-   独自のプロジェクト再度読み込みを処理する場合、環境は、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) の実装。 この呼び出しを受け取ったら、プロジェクトの最初のインスタンス (Project1) を再度読み込んで、プロジェクト ファイルのアップグレードを続けてください。 環境値を返す場合は、独自のプロジェクト再度読み込みを処理することを知っている`true`の<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>)。  
  
-   独自のプロジェクト再度読み込みを処理しないかどうかは、戻る`false`の<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>)。 この場合は、前に<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>([QEF_ForceEdit_NoPrompting](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True)、 [QEF_DisallowInMemoryEdits](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True)、) を返します、として、環境が別の新しい Project2 など、プロジェクトのインスタンスに作成します.次に示します。  
  
    1.  環境は<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A>で、最初プロジェクト オブジェクト (project1)、非アクティブ状態のためこのオブジェクトを配置します。  
  
    2.  環境は、プロジェクトの 2 つ目のインスタンス (Project2) を作成するために、 `IVsProjectFactory::CreateProject` の実装を呼び出します。  
  
    3.  環境は、ファイルを開き、2 つ目のプロジェクト オブジェクト (Project2) を初期化するために、 `IPersistFileFormat::Load` の実装を呼び出します。  
  
    4.  環境は、プロジェクト オブジェクトをアップグレードする必要があるかどうかを判断するために、2 度目に `IVsProjectUpgrade::UpgradeProject` を呼び出します。 しかし、この呼び出しは、プロジェクトの新しい 2 番目のインスタンス (Project2) に対して行われます。 これは、ソリューションで開くプロジェクトです。  
  
        > [!NOTE]
        >  インスタンスには、最初のプロジェクト (project1) が非アクティブの状態に配置し、返す必要がありますで<xref:Microsoft.VisualStudio.VSConstants.S_OK>最初の呼び出しから、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>実装します。 参照してください[基本的なプロジェクト](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36)の実装について`IVsProjectUpgrade::UpgradeProject`します。  
  
    5.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>の値を渡すと<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>の`rgfQueryEdit`パラメーター。  
  
    6.  環境を返します<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>プロジェクト ファイルが書き込まれるので、アップグレードを続けるとします。  
  
 アップグレードに失敗した場合に返す<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>から`IVsProjectUpgrade::UpgradeProject`します。 アップグレードの必要がない場合、またはアップグレードしないことにした場合は、操作なしとして `IVsProjectUpgrade::UpgradeProject` 呼び出しを処理します。 値を返す場合<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>、プレース ホルダーのノードは、プロジェクトのソリューションに追加されます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio 変換ウィザード](http://msdn.microsoft.com/en-us/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [プロジェクト項目のアップグレード](../misc/upgrading-project-items.md)   
 [プロジェクト](../extensibility/internals/projects.md)