---
title: プロジェクト構成オブジェクト |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7385a5f7768a57fd1a3d9688df152fd60a1ea130
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136030"
---
# <a name="project-configuration-object"></a>プロジェクト構成オブジェクト
プロジェクトの構成オブジェクトは、UI に構成情報の表示を管理します。  
  
 ![Visual Studio プロジェクト構成](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
プロジェクト構成プロパティ ページ  
  
 プロジェクトの構成プロバイダーは、プロジェクト構成を管理します。 環境およびプロジェクトの構成に関する情報を取得し、プロジェクトの構成プロバイダー オブジェクトにアタッチされているインターフェイスを呼び出すアクセスするために、他のパッケージです。  
  
> [!NOTE]
>  作成または、プログラムでソリューション構成ファイルを編集することはできません。 使用する必要があります`DTE.SolutionBuilder`です。 参照してください[ソリューション構成](../../extensibility/internals/solution-configuration.md)詳細についてはします。  
  
 構成 UI で使用する表示名を発行するプロジェクトを実装する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>です。 環境の呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>の一覧を返します`IVsCfg`環境の UI に一覧表示する構成とプラットフォームの情報の表示名の取得に使用できるポインター。 アクティブな構成とプラットフォームは、アクティブなソリューション構成に格納されているプロジェクトの構成によって決まります。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>アクティブ プロジェクトの構成を取得するメソッドを使用できます。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>にオブジェクトを実装することができます必要に応じて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>オブジェクトを<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>オブジェクトを取得できるように、`IVsProjectCfg2`正規プロジェクト構成の名前に基づいてオブジェクト。  
  
 プロジェクト構成にアクセスして、環境とその他のプロジェクトを提供する別の方法は、プロジェクトの実装を提供する、`IVsCfgProvider2::GetCfgs`を 1 つまたは複数の構成オブジェクトを返すメソッド。 プロジェクトが実装することがも<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>から継承される`IVsProjectCfg`とそれによって`IVsCfg`構成に固有の情報を提供します。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> 追加、削除、およびプロジェクトの構成の名前を変更するには、プラットフォーム、および機能をサポートします。  
  
> [!NOTE]
>  Visual Studio が 2 つの構成の種類に制限されない、多くの構成に関する前提条件の構成を処理するコードが書き込まれません必要がありますもことを想定して記述する必要がありますのでことを 1 つだけを持つプロジェクト構成は、デバッグまたは製品版のいずれかとは限りません。 これにより、使用する<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A>今後使用しません。  
  
 呼び出す`QueryInterface`から返されたオブジェクト`IVsGetCfgProvider::GetCfgProvider`取得`IVsCfgProvider2`です。 場合`IVsGetCfgProvider`を呼び出して載っていない`QueryInterface`上、`IVsProject3`プロジェクト オブジェクトを呼び出すことによって構成プロバイダー オブジェクトにアクセスすることができます`QueryInterface`に対して返されるオブジェクトの階層のルート ブラウザー オブジェクトで`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`、またはに対して返される構成プロバイダーへのポインター`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`です。  
  
 `IVsProjectCfg2` 主にビルド、デバッグへのアクセスと管理の展開のオブジェクトを提供でき、プロジェクトを自由にグループ出力できます。 メソッド`IVsProjectCfg`と`IVsProjectCfg2`を実装するために使用できる<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>ビルド プロセスを管理して<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>構成の出力グループ用のポインター。  
  
 プロジェクトには、同じ場合でも、グループ内に含まれる出力の数は変化する構成をサポートしている各構成のグループ数を返す必要があります。 グループ必要もあります (正規の名前、表示名、およびグループ情報) は、同じ識別子情報構成からプロジェクト内で。 詳細については、次を参照してください。[出力用のプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)です。  
  
 デバッグを有効にする、構成を実装する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>です。 `IVsDebuggableProjectCfg` 省略可能なプロジェクトの構成を起動するデバッガーによって実装されるインターフェイスは、構成オブジェクトには実装されて`IVsCfg`と`IVsProjectCfg`です。 F5 キーを押してデバッガーを起動するときに、環境を呼び出します。  
  
 `ISpecifyPropertyPages` および`IDispatch`を取得し、構成に依存する情報をユーザーに表示するプロパティ ページと組み合わせて使用されます。 詳細については、次を参照してください。[プロパティ ページ](../../extensibility/internals/property-pages.md)です。  
  
## <a name="see-also"></a>関連項目  
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [構築するためのプロジェクトの構成](../../extensibility/internals/project-configuration-for-building.md)   
 [出力用のプロジェクトの構成](../../extensibility/internals/project-configuration-for-output.md)   
 [プロパティ ページ](../../extensibility/internals/property-pages.md)   
 [ソリューション構成](../../extensibility/internals/solution-configuration.md)