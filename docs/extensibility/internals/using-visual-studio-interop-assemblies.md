---
title: "Visual Studio の相互運用機能アセンブリを使用する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 33
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 9762ba0404e739c167cadc3e9d3106c7f3ee14e8
ms.lasthandoff: 02/22/2017

---
# <a name="using-visual-studio-interop-assemblies"></a>Visual Studio の相互運用機能アセンブリを使用します。
Visual Studio の相互運用機能アセンブリでは、マネージ アプリケーションが Visual Studio 拡張機能を提供する COM インターフェイスへのアクセスを許可します。 いくつかの違いは、直線の COM インターフェイスとその相互運用機能のバージョンがあります。 たとえば、Hresult は、通常、整数値として表されます例外と同じ方法で処理する必要と (特に out パラメーター) のパラメーターの処理と異なります。  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>COM からマネージ コードに返される HRESULT の処理  
 マネージ コードから COM インターフェイスを呼び出す場合は、HRESULT 値を確認し、必要な場合に例外をスローします。 <xref:Microsoft.VisualStudio.ErrorHandler>クラスには、<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>それに渡された HRESULT の値に応じて、COM 例外をスローするメソッド</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>が含まれています。</xref:Microsoft.VisualStudio.ErrorHandler>  
  
 既定では、<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>を&0; より小さい値を持つ HRESULT を渡される場合は例外をスローします</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>。 このような Hresult が許容される値と、例外をスローする必要がありますに追加する HRESULT の値を渡す必要が<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>、値がテストした後</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>。 テスト対象の HRESULT に明示的に渡す任意の HRESULT 値と一致するかどうかは<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>、例外はスローされません</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants>クラスに含まれる定数の一般的な HRESULT は、たとえば、<xref:Microsoft.VisualStudio.VSConstants.S_OK>と<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>、および[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>.</xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT></xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>などの HRESULT</xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> </xref:Microsoft.VisualStudio.VSConstants.S_OK> </xref:Microsoft.VisualStudio.VSConstants> <xref:Microsoft.VisualStudio.VSConstants>また、<xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A>および<xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>COM の成功と失敗のマクロに対応する方法</xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A></xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A></xref:Microsoft.VisualStudio.VSConstants>  
  
 たとえば、次の関数呼び出しを<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>は許容可能な戻り値が他の HRESULT エラーがゼロより小さいを表します</xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>。  
  
 [!code-vb[VSSDKHRESULTInformation&1;](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb) ] 
 [!code-cs [VSSDKHRESULTInformation&1;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 1 つ以上使用可能な戻り値がある場合は、 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>。</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>への呼び出しでリストに追加の HRESULT 値だけできます。 追加できます。  
  
 [!code-vb[VSSDKHRESULTInformation&2;](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb) ] 
 [!code-cs [VSSDKHRESULTInformation&2;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>マネージ コードから COM に HRESULT を返す  
 マネージ コードが<xref:Microsoft.VisualStudio.VSConstants.S_OK>それを呼び出すことは COM 関数に</xref:Microsoft.VisualStudio.VSConstants.S_OK>戻る場合は例外が発生しません。 COM 相互運用では、マネージ コードで厳密に型指定される一般的な例外がサポートされます。 たとえばを受け取るメソッドを許容できない`null`引数<xref:System.ArgumentNullException>.</xref:System.ArgumentNullException>をスローします。  
  
 使用することができますを COM に戻したいされていない例外をスローすると、HRESULT がわかっている場合、<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>適切な例外をスローするメソッド</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>。 これは、動作も非標準のエラーなど<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>。</xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>HRESULT をマップしようは、厳密に型指定の例外には、それに渡されます。</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> できない場合は、代わりに一般的な COM 例外をスローします。 最終的には、HRESULT を渡すことを<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>マネージ コードからそれを呼び出す COM 関数に返されます</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>  
  
> [!NOTE]
>  例外によって、パフォーマンスが低下します。例外は、異常なプログラムの条件を示すことを目的としています。 頻繁に発生する条件は、スローされた例外ではなく、インラインで処理をする必要があります。  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown パラメーターの型 void * * として渡されます  
 [Out] パラメーター型として定義されている探します`void **`、COM では、としてインターフェイスでは、それを定義します。`[``iid_is``]`で、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相互運用機能アセンブリのメソッドのプロトタイプです。  
  
 場合によっては、COM インターフェイスを生成、`IUnknown`オブジェクト、および COM インターフェイス、として渡します型`void **`します。 これらのインターフェイスは特に重要ですのでとして変数が定義されている場合、IDL では、[出力].、`IUnknown`オブジェクトは、参照カウントを`AddRef`メソッドです。 オブジェクトが正しく処理されない場合は、メモリ リークが発生します。  
  
> [!NOTE]
>  `IUnknown`が明示的に解放されない場合、COM インターフェイスによって作成され、[out] 変数で返されるオブジェクトがメモリ リークを発生します。  
  
 このようなオブジェクトを処理するマネージ メソッドを扱う必要があります<xref:System.IntPtr>へのポインターとして、`IUnknown`オブジェクト、および呼び出し、<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>オブジェクトを取得するメソッド</xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A></xref:System.IntPtr>。 呼び出し元は、どのような型の適切な戻り値をキャストする必要があります。 オブジェクトが不要になったときに<xref:System.Runtime.InteropServices.Marshal.Release%2A>それを解放する</xref:System.Runtime.InteropServices.Marshal.Release%2A>呼び出し  
  
 呼び出しの例を次に示します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>メソッドと処理、`IUnknown`正しくオブジェクト:</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
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
>  渡すため、次の方法が呼ばれる`IUnknown` <xref:System.IntPtr>.</xref:System.IntPtr>の種類としてのポインターをオブジェクト このセクションで説明されているとは、それらを処理します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>[Out] パラメーターは省略可能です  
 [Out] として定義されているパラメーターを探しますデータ型 (`int`、`object`など)、COM で同じデータ型の配列としてインターフェイスでは、それを定義します。、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相互運用機能アセンブリのメソッドのプロトタイプです。  
  
 いくつかの COM インターフェイスなど<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>、[out] パラメーターを省略可能として扱います</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>。 これらの COM インターフェイスを返すかどうかは、オブジェクトが必要ない、 `null` [out] オブジェクトを作成する代わりにパラメーターの値としてのポインター。 これは仕様に基づく制限事項です。 これらのインターフェイスの`null`ポインターは、VSPackage を正常に動作の一部としてと見なされ、エラーは返されません。  
  
 CLR がである [out] パラメーターの値を許可していないので`null`、これらのインターフェイスの設計上の動作のパーツをマネージ コード内で直接使用できません。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]影響を受けるインターフェイスの相互運用機能アセンブリのメソッドは、CLR の通過を許可しているので、配列として適切なパラメーターを定義することで問題を回避する`null`配列。  
  
 これらのメソッドのマネージ実装を配置する必要があります、`null`は何も返されるときに、パラメーターの配列。 それ以外の場合、適切な型の&1; つの要素の配列を作成し、戻り値を配列に格納します。  
  
 省略可能な [out] とのインターフェイスから情報を受け取るメソッドのマネージ パラメーターが配列としてパラメーターを受け取ります。 配列の最初の要素の値を調べる。 ない場合は`null`、元のパラメーターの場合と同様に、最初の要素を処理します。  
  
## <a name="passing-constants-in-pointer-parameters"></a>ポインター パラメーターの引き渡し定数  
 検索パラメーターで定義されているように [] で、COM インターフェイス ポインターとして定義されている、<xref:System.IntPtr>入力、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相互運用機能アセンブリのメソッドのプロトタイプ</xref:System.IntPtr>。  
  
 同様の問題は、COM インターフェイスには、0、-1、またはオブジェクト ポインターではなく、– 2 などの特殊な値が渡されたときに発生します。 異なり[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]CLR では、定数をオブジェクトとしてキャストすることはできません。 代わりに、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相互運用機能アセンブリを定義、パラメーターとして、<xref:System.IntPtr>型です</xref:System.IntPtr>。  
  
 これらのメソッドのマネージ実装を活用して、ファクトを<xref:System.IntPtr>クラスには両方とも`int`と`void *`コンス トラクターを作成、<xref:System.IntPtr>オブジェクトまたは整数定数で、必要に応じて</xref:System.IntPtr></xref:System.IntPtr>。  
  
 受け取るメソッドのマネージ<xref:System.IntPtr>この型のパラメーターを使用する必要があります、<xref:System.IntPtr>結果を処理する変換演算子を入力します</xref:System.IntPtr></xref:System.IntPtr>。 最初の変換、<xref:System.IntPtr>に`int`し関連する整数の定数に対してテストします</xref:System.IntPtr>。 値と一致しない場合は、必要な型のオブジェクトに変換し、続行します。  
  
 この例については、「 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>の使用」を参照していますください。  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE 返す値として渡された [out] パラメーター  
 持つメソッドの検索、 `retval` COM インターフェイスで戻り値が、`int`値と追加 [出力] 配列パラメーターを返す、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相互運用機能アセンブリのメソッドのプロトタイプです。 クリアのために、これらのメソッドが特別な処理を必要とすることが、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相互運用機能アセンブリのメソッドのプロトタイプがある COM インターフェイスのメソッドよりも&1; つのパラメーターです。  
  
 OLE のアクティビティを処理する多くの COM インターフェイスに格納されている呼び出し元のプログラムに戻る OLE 状態に関する情報を送信する、`retval`インターフェイスの値を返します。 対応する、戻り値を使用する代わりに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相互運用機能アセンブリのメソッドを呼び出し元のプログラムが [out] に格納されている情報を送信するパラメーターの配列。  
  
 これらのメソッドのマネージ実装は、[out] パラメーターと同じ型の単一要素の配列を作成し、パラメーターに格納する必要があります。 配列の要素の値が適切な COM の場合と同じにする必要があります`retval`します。  
  
 この型のインターフェイスを呼び出すマネージ メソッドには、[出力] 配列から最初の要素をプルする必要があります。 この要素は、場合と同様に扱うことができます、`retval`対応する COM インターフェイスから値を返します。  
  
## <a name="see-also"></a>関連項目  
 [アンマネージ コードとの相互運用](http://msdn.microsoft.com/Library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
