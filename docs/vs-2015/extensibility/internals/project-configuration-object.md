---
title: プロジェクト構成オブジェクト |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 12e633b3de120d1454e715837f54d4a5222a0137
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245233"
---
# <a name="project-configuration-object"></a>プロジェクト構成オブジェクト
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

プロジェクトの構成オブジェクトは、UI に構成情報の表示を管理します。  
  
 ![Visual Studio のプロジェクト構成](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
プロジェクト構成プロパティ ページ  
  
 プロジェクトの構成プロバイダーは、プロジェクト構成を管理します。 環境および他のパッケージをプロジェクトの構成に関する情報を取得、プロジェクトの構成プロバイダーのオブジェクトにアタッチされているインターフェイスの呼び出しにアクセスします。  
  
> [!NOTE]
>  作成またはソリューションの構成ファイルをプログラムで編集できません。 使用する必要があります`DTE.SolutionBuilder`します。 参照してください[ソリューション構成](../../extensibility/internals/solution-configuration.md)詳細についてはします。  
  
 構成 UI で使用する表示名を発行するプロジェクトを実装する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>します。 環境は<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>の一覧が返されます`IVsCfg`環境の UI に一覧表示する構成とプラットフォームの情報の表示名を取得するのに使用できるポインター。 アクティブな構成とプラットフォームについては、アクティブなソリューション構成に格納されているプロジェクトの構成によって決まります。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>アクティブ プロジェクトの構成を取得するメソッドを使用できます。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>にオブジェクトを実装することができます必要に応じて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>オブジェクトを<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>オブジェクトを取得できるように、`IVsProjectCfg2`オブジェクトに基づく標準的なプロジェクト構成名。  
  
 実装を提供するプロジェクトの環境および他のプロジェクトをプロジェクト構成にアクセスできるようにすることもできますが、`IVsCfgProvider2::GetCfgs`を 1 つまたは複数の構成オブジェクトを返すメソッド。 プロジェクトが実装することも<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>から継承される`IVsProjectCfg`とそれによって`IVsCfg`構成に固有の情報を提供します。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> 追加、削除、およびプロジェクト構成の名前を変更するのには、プラットフォーム、および機能をサポートしています。  
  
> [!NOTE]
>  Visual Studio は、2 つの構成の種類に制限がなくなりました、多くの構成に関する前提条件の構成を処理するコードが書き込まれませんする必要がありますもことを想定して記述する必要がありますのでをいずれかのみを含むプロジェクト構成は、デバッグまたは製品版のいずれかとは限りません。 これにより、使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A>廃止されています。  
  
 呼び出す`QueryInterface`から返されるオブジェクトで`IVsGetCfgProvider::GetCfgProvider`取得`IVsCfgProvider2`します。 場合`IVsGetCfgProvider`呼び出してが見つからない`QueryInterface`上、`IVsProject3`プロジェクト オブジェクトを呼び出すことによって、構成プロバイダー オブジェクトをアクセスできます`QueryInterface`に対して返されるオブジェクトの階層のルート ブラウザー オブジェクトで`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`、または返される構成プロバイダーへのポインター`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`します。  
  
 `IVsProjectCfg2` 主にビルド、デバッグへのアクセスと管理の展開オブジェクトを提供しを自由にグループの出力を使用するには、プロジェクト。 メソッド`IVsProjectCfg`と`IVsProjectCfg2`を実装するために使用できる<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>ビルド処理を管理して<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>構成の出力グループのポインター。  
  
 プロジェクトには、同じグループ内に含まれる出力の数は構成で異なる場合がありますもサポートしている構成ごとにグループ数を返す必要があります。 グループも必要 (正規名、表示名、およびグループ情報) は、同じ識別子情報構成からプロジェクト内です。 詳細については、次を参照してください。[出力用のプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)します。  
  
 デバッグを有効にする、構成を実装する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>します。 `IVsDebuggableProjectCfg` プロジェクトの構成を起動するデバッガーによって実装される、省略可能なインターフェイスは、構成オブジェクトが実装されている`IVsCfg`と`IVsProjectCfg`します。 F5 キーを押してデバッガーを起動するときに、環境を呼び出します。  
  
 `ISpecifyPropertyPages` `IDispatch`を取得し、構成に依存する情報をユーザーに表示するプロパティ ページと組み合わせて使用されます。 詳細については、次を参照してください。[プロパティ ページ](../../extensibility/internals/property-pages.md)します。  
  
## <a name="see-also"></a>関連項目  
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [ビルドするためのプロジェクト構成](../../extensibility/internals/project-configuration-for-building.md)   
 [出力のプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)   
 [プロパティ ページ](../../extensibility/internals/property-pages.md)   
 [ソリューション構成](../../extensibility/internals/solution-configuration.md)

