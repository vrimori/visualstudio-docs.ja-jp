---
title: Visual Studio 相互運用機能アセンブリの使用 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 34
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 942db931178cedba21468f42e7412ba3e93a1aa6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546072"
---
# <a name="using-visual-studio-interop-assemblies"></a>Visual Studio 相互運用機能アセンブリの使用
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Studio 相互運用機能アセンブリを使用して](https://docs.microsoft.com/visualstudio/extensibility/internals/using-visual-studio-interop-assemblies)します。  
  
Visual Studio 相互運用機能アセンブリは、マネージ アプリケーションを Visual Studio 拡張機能を提供する COM インターフェイスへのアクセスを許可します。 直線の COM インターフェイスとその相互運用機能のバージョンとの間には、いくつか違いがあります。 たとえば、Hresult は、通常、整数値として表されます、例外と同じ方法で処理する必要があり、(特に out パラメーター) のパラメーターが異なる方法で扱われます。  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>COM からマネージド コードに返される HRESULT の処理  
 マネージド コードから COM インターフェイスを呼び出す場合は、HRESULT 値を確認し、必要な場合に例外をスローします。 <xref:Microsoft.VisualStudio.ErrorHandler>クラスが含まれています、<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>に渡されたメソッドは、HRESULT の値に応じて、COM 例外をスローします。  
  
 既定では、<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>を 0 より小さい値を持つ HRESULT を渡されるたびに、例外をスローします。 このような Hresult が許容される値と、例外をスローする必要がありますに追加 HRESULT の値を渡す必要があります<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>後の値がテストされます。 テスト対象の HRESULT が明示的に渡された HRESULT 値と一致するかどうか<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>例外はスローされません。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants>クラスに含まれる定数共通 hresult は、たとえば、<xref:Microsoft.VisualStudio.VSConstants.S_OK>と<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>、および[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]HRESULT、たとえば、<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>と<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>します。 <xref:Microsoft.VisualStudio.VSConstants> 用意されています、<xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A>と<xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>メソッドで、COM の SUCCEEDED および FAILED マクロに対応しています  
  
 たとえば、次の関数呼び出しを<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>は許容される戻り値が他の HRESULT エラーを表す 0 未満です。  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 1 つ以上使用可能な戻り値がある場合への呼び出しリストに追加の HRESULT 値だけできます追加されます<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>します。  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>マネージド コードから COM に HRESULT を返す  
 例外が発生しない場合は、マネージ コードを返します。<xref:Microsoft.VisualStudio.VSConstants.S_OK>という名前の COM 関数にします。 COM 相互運用では、マネージド コードで厳密に型指定される一般的な例外がサポートされます。 許容できないを受信するメソッドなど、`null`引数がスローされます、<xref:System.ArgumentNullException>します。  
  
 使用することができます、COM に取得するを特定する例外をスローするが、HRESULT がわかって、<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>適切な例外をスローするメソッド。 たとえば、非標準のエラーを使用しても動作この<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>します。 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> HRESULT をマップする試行は、厳密に型指定された例外に渡されます。 できない場合は、代わりに一般的な COM 例外をスローします。 最終的には、HRESULT に渡すこと<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>という名前の COM 関数をマネージ コードからが返されます。  
  
> [!NOTE]
>  例外によって、パフォーマンスが低下します。例外は、異常なプログラムの条件を示すことを目的としています。 頻繁に発生する条件は、スローされた例外ではなく、インラインで処理をする必要があります。  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown パラメーターの型 void * * として渡されます  
 [Out] パラメーター型として定義されている検索`void **`、COM では、としてがインターフェイスを定義します。`[``iid_is``]`で、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]相互運用機能アセンブリのメソッド プロトタイプ。  
  
 場合によっては、COM インターフェイスの生成、`IUnknown`オブジェクト、および COM インターフェイスから渡します型として`void **`します。 これらのインターフェイスは特に重要ですので、として変数が定義されている場合、IDL では、[出力]、`IUnknown`オブジェクトが参照カウントを`AddRef`メソッド。 オブジェクトが正しく処理されない場合は、メモリ リークが発生します。  
  
> [!NOTE]
>  `IUnknown`が明示的に解放されない場合、COM インターフェイスによって作成され、[out] 変数で返されるオブジェクトがメモリ リークが発生します。  
  
 このようなオブジェクトを処理する管理対象のメソッドを扱う必要があります<xref:System.IntPtr>へのポインターとして、`IUnknown`オブジェクト、および呼び出し、<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>オブジェクトを取得するメソッド。 呼び出し元にどのような型が適切な戻り値をキャストする必要があります。 オブジェクトが不要になったときに呼び出す<xref:System.Runtime.InteropServices.Marshal.Release%2A>を解放します。  
  
 呼び出し元の例を次に、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>メソッドと処理、`IUnknown`正しくオブジェクトします。  
  
```  
MyClass myclass;  
Object object;  
IntPtr pObj;  
Guid iid = Typeof(MyClass).Guid;  
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);     
if (NativeMethods.Succeeded(hr))   
{  
    try   
    {  
        object = Marshal.GetObjectForIUnknown(pObj);  
        myclass = object;  
    }  
    finally   
    {  
        Marshal.Release(pObj);  
    }  
}  
else   
{  
    // error calling QueryViewInterface  
}  
```  
  
> [!NOTE]
>  次のメソッドが渡す呼ばれる`IUnknown`オブジェクト ポインターの型として<xref:System.IntPtr>します。 このセクションで説明したは、それらを処理します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>[Out] パラメーターは省略可能です。  
 [Out] として定義されているパラメーターの参照データ型 (`int`、`object`など)、COM で同じデータ型の配列としてがインターフェイスを定義します。、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]相互運用機能アセンブリのメソッド プロトタイプ。  
  
 などのいくつかの COM インターフェイス<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>、[out] パラメーターを省略可能として扱います。 これらの COM インターフェイスを返すかどうかは、オブジェクトは必要ありません、 `null` [out] オブジェクトを作成する代わりにそのパラメーターの値としてのポインター。 これは仕様に基づく制限事項です。 これらのインターフェイスの`null`ポインターは、VSPackage の正しい動作の一部としてと見なされ、エラーは返されません。  
  
 CLR である [out] パラメーターの値が許可されないため`null`、これらのインターフェイスのデザインの振る舞いの一部がマネージ コード内で直接ご利用いただけません。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]影響を受けるインターフェイスの相互運用機能アセンブリのメソッドが CLR を渡すことのできるので、配列として、関連するパラメーターを定義することで問題を回避する`null`配列。  
  
 これらのメソッドのマネージ実装を配置する必要があります、`null`が何も返されるときに、パラメーターの配列。 それ以外の場合、適切な型の 1 つの要素の配列を作成し、戻り値を配列に格納します。  
  
 管理オプションの [out] とのインターフェイスから情報を受け取るメソッドのパラメーターが配列としてパラメーターを受け取ります。 配列の最初の要素の値を調べるだけです。 ない場合`null`、元のパラメーターの場合と同様、最初の要素を処理します。  
  
## <a name="passing-constants-in-pointer-parameters"></a>ポインター パラメーターの引き渡し定数  
 定義されているように [] で、COM インターフェイス ポインターとして定義されているパラメーターを探して、<xref:System.IntPtr>で入力、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]相互運用機能アセンブリのメソッド プロトタイプ。  
  
 同様の問題では、COM インターフェイスは、0、-1、またはオブジェクトのポインターではなく、– 2 などの特殊な値を通過するときに発生します。 異なり[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]CLR では、定数をオブジェクトとしてキャストすることはできません。 代わりに、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]相互運用機能アセンブリの定義、パラメーターとして、<xref:System.IntPtr>型。  
  
 これらのメソッドのマネージ実装を活用して、ファクトを<xref:System.IntPtr>クラスには両方とも`int`と`void *`を作成するコンス トラクター、<xref:System.IntPtr>オブジェクトまたは整数の定数のいずれかからとして適切な。  
  
 受け取るメソッドがマネージ<xref:System.IntPtr>この型のパラメーターを使用する必要があります、<xref:System.IntPtr>結果を処理する変換演算子を入力します。 最初の変換、<xref:System.IntPtr>に`int`関連する整数の定数に対してテストします。 値が一致しない場合は、必要な型のオブジェクトに変換して、続行します。  
  
 この例については、次を参照してください。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>します。  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE を返す値として渡される [out] パラメーター  
 持つメソッドを探して、 `retval` 、COM インターフェイスでの戻り値が、`int`戻り値と [out] 配列パラメーターを追加、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]相互運用機能アセンブリのメソッド プロトタイプ。 オフのために、これらのメソッドが特別な処理を必要とする必要がある、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]メソッド プロトタイプの相互運用機能アセンブリが COM インターフェイスのメソッドよりも 1 つのパラメーターがあります。  
  
 OLE のアクティビティを処理する多くの COM インターフェイスを呼び出し元のプログラムに格納されている OLE 状態に関する情報を送信する、`retval`インターフェイスの値を返します。 対応する戻り値を使用する代わりに[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]相互運用機能アセンブリのメソッドを呼び出し元のプログラムが [out] に格納されている情報を送信するパラメーターの配列。  
  
 これらのメソッドのマネージ実装は、[out] パラメーターと同じ型の単一要素の配列を作成し、パラメーターに配置する必要があります。 配列の要素の値には、適切な COM と同じである必要があります`retval`します。  
  
 この型のインターフェイスを呼び出すマネージ メソッドには、[out] 配列から最初の要素をプルする必要があります。 この要素は、場合と同様に扱うことができます、`retval`対応する COM インターフェイスからの戻り値。  
  
## <a name="see-also"></a>関連項目  
 [アンマネージ コードとの相互運用](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)

