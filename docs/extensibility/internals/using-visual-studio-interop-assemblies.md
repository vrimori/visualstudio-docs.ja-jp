---
title: "Visual Studio 相互運用機能アセンブリを使用して |Microsoft ドキュメント"
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
ms.translationtype: MT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 5d4b825b33339367ee331eb74aa2eb210c85206c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="using-visual-studio-interop-assemblies"></a>Visual Studio 相互運用機能アセンブリを使用します。
Visual Studio 相互運用機能アセンブリでは、マネージ アプリケーションの Visual Studio 拡張機能を提供する COM インターフェイスにアクセスできるようにします。 直線の COM インターフェイスとの相互運用機能のバージョンに違いがあります。 たとえば、Hresult int 値として表される一般的に、例外と同じ方法で処理する必要があり、(特に out パラメーター) のパラメーターが異なる方法で扱われます。  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>COM からマネージ コードに返される HRESULT の処理  
 マネージ コードから COM インターフェイスを呼び出す場合は、HRESULT 値を確認し、必要な場合に例外をスローします。 <xref:Microsoft.VisualStudio.ErrorHandler>クラスに含まれる、<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>渡された HRESULT の値に応じて、COM 例外をスローするメソッド。  
  
 既定では、<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>を 0 より小さい値を持つ HRESULT を渡される場合は例外をスローします。 ここでこのような Hresult が許容される値と例外をスローするなしの場合、追加 HRESULT の値に渡す必要があります<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>値がテストした後です。 明示的に渡す HRESULT 値をテスト対象の HRESULT が一致するかどうかは<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>例外はスローされません。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants>クラスに含まれる定数共通 hresult は、たとえば、<xref:Microsoft.VisualStudio.VSConstants.S_OK>と<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>、および[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]HRESULT、たとえば、<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>と<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>です。 <xref:Microsoft.VisualStudio.VSConstants>用意されています、<xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A>と<xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>COM の SUCCEEDED および FAILED マクロに対応するメソッド  
  
 たとえば、次の関数呼び出しの順番<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>は他の HRESULT が許容可能な戻り値、エラーを表す 0 未満です。  
  
 [!code-vb[VSSDKHRESULTInformation 1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb) ] [!code-csharp [VSSDKHRESULTInformation 1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 1 つ以上使用可能な戻り値がある場合 HRESULT 値を追加できますのみ一覧に表示されますへの呼び出しで<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>です。  
  
 [!code-vb[VSSDKHRESULTInformation 2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb) ] [!code-csharp [VSSDKHRESULTInformation 2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>マネージ コードから COM に HRESULT を返す  
 例外が発生しない場合は、マネージ コードを返します<xref:Microsoft.VisualStudio.VSConstants.S_OK>その呼び出し元の COM 関数にします。 COM 相互運用では、マネージ コードで厳密に型指定される一般的な例外がサポートされます。 たとえば、受け入れられないを受け取るメソッド`null`引数がスローされます、<xref:System.ArgumentNullException>です。  
  
 使用することができます、COM に戻したいが不明をスローする例外が HRESULT がわかって、<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>適切な例外をスローするメソッド。 たとえば、非標準のエラーでも動作<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>です。 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>HRESULT をマップしようは、厳密に型指定例外に渡されます。 できない場合は、代わりに一般的な COM 例外をスローします。 最終的には、HRESULT を渡すことを<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>その呼び出し元の COM 関数をマネージ コードからが返されます。  
  
> [!NOTE]
>  例外によって、パフォーマンスが低下します。例外は、異常なプログラムの条件を示すことを目的としています。 頻繁に発生する条件は、スローされた例外ではなく、インラインで処理をする必要があります。  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>型の void * * として IUnknown パラメーターが渡されました  
 [Out] パラメーター型として定義されている検索`void **`COM では、としてインターフェイス、それを定義します。`[``iid_is``]`で、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相互運用機能アセンブリのメソッドのプロトタイプ。  
  
 場合によっては、COM インターフェイスの生成、`IUnknown`オブジェクト、および COM インターフェイスからとして渡します型`void **`です。 これらのインターフェイスは特に重要なためとして変数が定義されている場合、IDL 内では、[出力].、`IUnknown`オブジェクトは、参照カウントを`AddRef`メソッドです。 オブジェクトが正しく処理されない場合は、メモリ リークが発生します。  
  
> [!NOTE]
>  `IUnknown`が明示的に解放されない場合、COM インターフェイスによって作成され、[out] 変数で返されるオブジェクトがメモリ リークを発生します。  
  
 このようなオブジェクトを処理するマネージ メソッドが扱う必要があります<xref:System.IntPtr>へのポインターとして、`IUnknown`オブジェクト、および呼び出し、<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>オブジェクトを取得します。 呼び出し元には、戻り値は、適切なすべての型をキャストし、必要があります。 オブジェクトは必要なくなったときに呼び出す<xref:System.Runtime.InteropServices.Marshal.Release%2A>にそれを解放します。  
  
 呼び出す例を次に示します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>メソッドと処理、`IUnknown`正しくオブジェクトします。  
  
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
>  渡す次の方法が分かった`IUnknown`オブジェクト ポインターの型として<xref:System.IntPtr>です。 このセクションで説明したように、それらを処理します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>[Out] パラメーターは省略可能です  
 [Out] として定義されているパラメーターの参照データ型 (`int`、`object`など)、COM では、同じデータ型の配列としてインターフェイス、それを定義します。、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相互運用機能アセンブリのメソッドのプロトタイプ。  
  
 いくつかの COM インターフェイスなど<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>、[out] パラメーターは省略可能として扱います。 これらの COM インターフェイスを返すかどうか、オブジェクトが必要ない、 `null` [out] オブジェクトを作成する代わりにそのパラメーターの値としてのポインター。 これは仕様に基づく制限事項です。 これらのインターフェイスの`null`ポインターは、VSPackage の正しい動作の一部としてと見なされ、エラーは返されません。  
  
 CLR にある [out] パラメーターの値が許可されないため`null`、これらのインターフェイスの設計上の動作の一部はマネージ コード内で直接使用できます。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]の影響を受けるインターフェイスの相互運用機能アセンブリのメソッドは、CLR の通過を許可しているので、配列として、関連するパラメーターを定義することで問題を回避する`null`配列。  
  
 これらのメソッドのマネージ実装を配置する必要があります、`null`返される nothing を使用する必要がある場合は、パラメーターの配列。 それ以外の場合、適切な型の 1 つの要素の配列を作成し、配列に、戻り値を格納します。  
  
 省略可能な [out] を持つインターフェイスから情報を受け取るメソッドが管理されているパラメーターが配列としてパラメーターを受信します。 配列の最初の要素の値を調べる。 ない場合は`null`、元のパラメーターの場合と同様に、最初の要素を処理します。  
  
## <a name="passing-constants-in-pointer-parameters"></a>ポインター パラメーターの引き渡し定数  
 定義されているように [] で、COM インターフェイス ポインターとして定義されているパラメーターを探して、<xref:System.IntPtr>に入力、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相互運用機能アセンブリのメソッドのプロトタイプ。  
  
 同様の問題は、COM インターフェイスは、0、-1 または-2 は、オブジェクトのポインターではなくなどの特殊な値を通過するときに発生します。 異なり[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]CLR では、定数オブジェクトにキャストすることはできません。 代わりに、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相互運用機能アセンブリを定義として、パラメーター、<xref:System.IntPtr>型です。  
  
 これらのメソッドのマネージ実装を活用して、ファクトを<xref:System.IntPtr>クラスには両方とも`int`と`void *`コンス トラクターを作成、<xref:System.IntPtr>オブジェクトまたは整数の定数で、必要に応じて。  
  
 受け取るメソッドのマネージ<xref:System.IntPtr>この型のパラメーターを使用する必要があります、<xref:System.IntPtr>結果を処理する変換演算子を入力します。 最初の変換、<xref:System.IntPtr>に`int`および関連する整数の定数に対してテストします。 値が一致しない場合は、必要な型のオブジェクトに変換し、続けます。  
  
 この例については、次を参照してください。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>です。  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE を返す値として渡された [out] パラメーター  
 持つメソッドの検索、 `retval` COM インターフェイスでの戻り値が、`int`戻り値と、追加の [out] 配列パラメーター、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相互運用機能アセンブリのメソッドのプロトタイプ。 これらのメソッドでは、ために、特別な処理が必要なことが明確になります、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相互運用機能アセンブリのメソッドのプロトタイプがある COM インターフェイスのメソッドよりも 1 つのパラメーターです。  
  
 OLE のアクティビティを処理する多数の COM インターフェイスに格納されている呼び出し元のプログラムに戻す OLE 状態に関する情報を送信する、`retval`インターフェイスの値を返します。 対応する、戻り値を使用する代わりに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相互運用機能アセンブリのメソッドは、[out] に格納されている呼び出し元のプログラムに情報を送信配列パラメーターです。  
  
 これらのメソッドのマネージ実装は、[out] パラメーターと同じ型の 1 つの要素の配列を作成し、パラメーターに格納する必要があります。 配列要素の値は、適切な COM と同じにする必要があります`retval`です。  
  
 この型のインターフェイスを呼び出すマネージ メソッドには、[out] 配列外の最初の要素をプルする必要があります。 この要素は、場合と同様に扱うことができます、`retval`対応する COM インターフェイスから値を返します。  
  
## <a name="see-also"></a>関連項目  
 [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)
