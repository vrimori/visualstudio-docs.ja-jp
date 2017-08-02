---
title: "構成オブジェクトをプロジェクト |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 0518e4844dd7fa7710935f742bf44943a5ef945d
ms.lasthandoff: 02/22/2017

---
# <a name="project-configuration-object"></a>プロジェクト構成オブジェクト
プロジェクトの構成オブジェクトは、UI に構成情報の表示を管理します。  
  
 ![Visual Studio プロジェクトの構成](~/docs/extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
プロジェクト構成のプロパティ ページ  
  
 プロジェクトの構成プロバイダーは、プロジェクト構成を管理します。 環境であり、プロジェクトの構成に関する情報を取得し、プロジェクトの構成プロバイダー オブジェクトにアタッチされているインターフェイスの呼び出しにアクセスするために他のパッケージ。  
  
> [!NOTE]
>  作成またはプログラムを使用してソリューション構成ファイルを編集できません。 使用する必要があります`DTE.SolutionBuilder`します。 参照してください[ソリューション構成](../../extensibility/internals/solution-configuration.md)の詳細。  
  
 構成 UI で使用する表示名を発行するには、プロジェクトが<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>を実装します。 環境の呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>の一覧が返されます`IVsCfg`を環境内の UI に記述する構成とプラットフォームの情報の表示名を取得するポインター</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> 。 アクティブな構成とプラットフォームについては、アクティブなソリューション構成に格納されているプロジェクトの構成によって決まります。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>メソッドを使用して、アクティブ プロジェクトの構成を取得することです</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>にオブジェクトを実装することができます必要に応じて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>オブジェクトを<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>オブジェクトを取得できるように、`IVsProjectCfg2`オブジェクトに基づいて、標準的なプロジェクト構成名</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>。  
  
 環境および他のプロジェクトをプロジェクト構成にアクセスできるようにする別の方法は、プロジェクトの実装を提供する、 `IVsCfgProvider2::GetCfgs`&1; つまたは複数の構成オブジェクトを返すメソッド。 プロジェクトを実装も<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>から継承される`IVsProjectCfg`とそれによって`IVsCfg`構成に固有の情報を指定する</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>追加、削除、およびプロジェクトの構成の名前を変更するのには、プラットフォーム、および機能をサポートしています。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>  
  
> [!NOTE]
>  Visual Studio は、2 つの構成の種類に制限は不要になったであるため、多くの構成に関する前提条件で構成を処理するコードが記述されなかった必要がありますに書き込む&1; つだけの構成を持つプロジェクトは、必ずしもことを想定してデバッグまたは製品版のいずれか。 これにより、使用する<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A>今後使用しません</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>。  
  
 呼び出す`QueryInterface`から返されたオブジェクト`IVsGetCfgProvider::GetCfgProvider`取得`IVsCfgProvider2`します。 場合`IVsGetCfgProvider`を呼び出してが見つからない`QueryInterface`上、`IVsProject3`プロジェクト オブジェクトを呼び出すことによって構成プロバイダー オブジェクトにアクセスすることができます`QueryInterface`に対して返されるオブジェクトの階層のルート ブラウザー オブジェクトに`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`、またはに対して返される構成プロバイダーへのポインターを介した`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`します。  
  
 `IVsProjectCfg2`主にビルド、デバッグにアクセスして展開の管理オブジェクトとグループの出力に自由度を使用するプロジェクト。 メソッド`IVsProjectCfg`と`IVsProjectCfg2`を実装するために使用できる<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>ビルド プロセスを管理して<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>構成の出力グループ用のポインター</xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> </xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> 。  
  
 プロジェクトには、同じグループ内に含まれる出力の数は、構成を異なる場合がありますが、サポートする構成ごとにグループ数を返す必要があります。 グループが必要 (正規名、表示名、およびグループ情報) は、同じ識別子情報構成からプロジェクト内でです。 詳細については、次を参照してください。[出力のプロジェクト構成を](../../extensibility/internals/project-configuration-for-output.md)します。  
  
 デバッグを有効にするには、構成が<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>を実装します。 `IVsDebuggableProjectCfg`プロジェクトの構成を起動するデバッガーによって実装される省略可能なインターフェイスで、使用して、構成オブジェクトで実装`IVsCfg`と`IVsProjectCfg`です。 F5 キーを押してデバッガーを起動するときに、環境を呼び出します。  
  
 `ISpecifyPropertyPages``IDispatch`プロパティ ページと組み合わせて取得し、構成依存の情報をユーザーに表示するために使用します。 詳細については、次を参照してください。[プロパティ ページ](../../extensibility/internals/property-pages.md)します。  
  
## <a name="see-also"></a>関連項目  
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [構築するためのプロジェクトの構成](../../extensibility/internals/project-configuration-for-building.md)   
 [出力のプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)   
 [プロパティ ページ](../../extensibility/internals/property-pages.md)   
 [ソリューション構成](../../extensibility/internals/solution-configuration.md)
