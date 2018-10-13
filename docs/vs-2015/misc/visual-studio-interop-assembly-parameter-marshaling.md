---
title: Visual Studio 相互運用機能アセンブリのパラメーター マーシャ リング |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: douge
ms.openlocfilehash: e18667adb48f565f73acc14f5012f9c96283efe9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195020"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Visual Studio 相互運用機能アセンブリのパラメーター マーシャリング
マネージ コードで記述されている Vspackage は、呼び出しまたはアンマネージ COM コードによって呼び出される必要があります。 通常、メソッドの引数が変換、または、マーシャ リングされる、自動的に相互運用マーシャラーによって。 ただし、場合によって引数は、変換できない簡単な方法でします。 その場合、相互運用機能アセンブリのメソッド プロトタイプのパラメーターは、COM 関数のパラメーターをできるだけ一致に使用されます。 詳細については、次を参照してください。[相互運用マーシャ リング](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)します。  
  
## <a name="general-suggestions"></a>一般的な注意点  
  
##### <a name="read-the-reference-documentation"></a>リファレンス ドキュメントを読む  
 相互運用性の問題を検出する効果的な方法では、各メソッドのリファレンス ドキュメントを読み取るです。  
  
 各メソッドのリファレンス ドキュメントには、次の 3 つの関連するセクションが含まれています。  
  
-   [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] COM 関数のプロトタイプ。  
  
-   相互運用機能アセンブリのメソッド プロトタイプ。  
  
-   COM パラメーターとそれぞれの簡単な説明の一覧。  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>2 つのプロトタイプの相違点を探します  
 ほとんどの相互運用性の問題は、COM インターフェイスで特定の種類の定義とで同じ種類の定義の間の不一致から派生、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]相互運用機能アセンブリ。 たとえばを渡す機能の違いを`null`[out] パラメーターの値。 2 つのプロトタイプの相違点を探し、渡されるデータの影響を考慮する必要があります。  
  
##### <a name="read-the-parameter-definitions"></a>パラメーターの定義を読み取ります。  
 パラメーターの定義を読み取ります。 COM は、1 つのパラメーターのデータのさまざまな種類の混在の詳細については、共通言語ランタイム (CLR) よりも厳密に小さいです。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] COM インターフェイスをこのような柔軟性を最大限に活用します。 パラメーターを渡すことができます、または標準以外の値または型の定数ポインター パラメーターの値などのデータを必要とは、ドキュメントにそのため記載する必要があります。  
  
### <a name="iunknown-objects-passed-as-type-void"></a>型の void * * として IUnknown オブジェクトが渡されます  
 [Out] パラメーター型として定義されている検索`void **`、COM では、としてがインターフェイスを定義します。`[``iid_is``]`で、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]相互運用機能アセンブリのメソッド プロトタイプ。  
  
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
  
### <a name="optional-out-parameters"></a>[Out] パラメーターは省略可能です。  
 [Out] として定義されているパラメーターの参照データ型 (`int`、`object`など)、COM で同じデータ型の配列としてがインターフェイスを定義します。、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]相互運用機能アセンブリのメソッド プロトタイプ。  
  
 などのいくつかの COM インターフェイス<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>、[out] パラメーターを省略可能として扱います。 これらの COM インターフェイスを返すかどうかは、オブジェクトは必要ありません、 `null` [out] オブジェクトを作成する代わりにそのパラメーターの値としてのポインター。 これは仕様に基づく制限事項です。 これらのインターフェイスの`null`ポインターは、VSPackage の正しい動作の一部としてと見なされ、エラーは返されません。  
  
 CLR である [out] パラメーターの値が許可されないため`null`、これらのインターフェイスのデザインの振る舞いの一部がマネージ コード内で直接ご利用いただけません。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]影響を受けるインターフェイスの相互運用機能アセンブリのメソッドが CLR を渡すことのできるので、配列として、関連するパラメーターを定義することで問題を回避する`null`配列。  
  
 これらのメソッドのマネージ実装を配置する必要があります、`null`が何も返されるときに、パラメーターの配列。 それ以外の場合、適切な型の 1 つの要素の配列を作成し、戻り値を配列に格納します。  
  
 管理オプションの [out] とのインターフェイスから情報を受け取るメソッドのパラメーターが配列としてパラメーターを受け取ります。 配列の最初の要素の値を調べるだけです。 ない場合`null`、元のパラメーターの場合と同様、最初の要素を処理します。  
  
### <a name="passing-constants-in-pointer-parameters"></a>ポインター パラメーターの引き渡し定数  
 定義されているように [] で、COM インターフェイス ポインターとして定義されているパラメーターを探して、<xref:System.IntPtr>で入力、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]相互運用機能アセンブリのメソッド プロトタイプ。  
  
 同様の問題では、COM インターフェイスは、0、-1、またはオブジェクトのポインターではなく、– 2 などの特殊な値を通過するときに発生します。 異なり[!INCLUDE[vcprvc](../includes/vcprvc-md.md)]CLR では、定数をオブジェクトとしてキャストすることはできません。 代わりに、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]相互運用機能アセンブリの定義、パラメーターとして、<xref:System.IntPtr>型。  
  
 これらのメソッドのマネージ実装を活用して、ファクトを<xref:System.IntPtr>クラスには両方とも`int`と`void *`を作成するコンス トラクター、<xref:System.IntPtr>オブジェクトまたは整数の定数のいずれかからとして適切な。  
  
 受け取るメソッドがマネージ<xref:System.IntPtr>この型のパラメーターを使用する必要があります、<xref:System.IntPtr>結果を処理する変換演算子を入力します。 最初の変換、<xref:System.IntPtr>に`int`関連する整数の定数に対してテストします。 値が一致しない場合は、必要な型のオブジェクトに変換して、続行します。  
  
 この例については、次を参照してください。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>します。  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>OLE を返す値として渡される [out] パラメーター  
 持つメソッドを探して、 `retval` 、COM インターフェイスでの戻り値が、`int`戻り値と [out] 配列パラメーターを追加、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]相互運用機能アセンブリのメソッド プロトタイプ。 オフのために、これらのメソッドが特別な処理を必要とする必要がある、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]メソッド プロトタイプの相互運用機能アセンブリが COM インターフェイスのメソッドよりも 1 つのパラメーターがあります。  
  
 OLE のアクティビティを処理する多くの COM インターフェイスを呼び出し元のプログラムに格納されている OLE 状態に関する情報を送信する、`retval`インターフェイスの値を返します。 対応する戻り値を使用する代わりに[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]相互運用機能アセンブリのメソッドを呼び出し元のプログラムが [out] に格納されている情報を送信するパラメーターの配列。  
  
 これらのメソッドのマネージ実装は、[out] パラメーターと同じ型の単一要素の配列を作成し、パラメーターに配置する必要があります。 配列の要素の値には、適切な COM と同じである必要があります`retval`します。  
  
 この型のインターフェイスを呼び出すマネージ メソッドには、[out] 配列から最初の要素をプルする必要があります。 この要素は、場合と同様に扱うことができます、`retval`対応する COM インターフェイスからの戻り値。  
  
## <a name="see-also"></a>関連項目  
 [相互運用マーシャリング](http://msdn.microsoft.com/en-us/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [相互運用マーシャリング](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [相互運用性のトラブルシューティング](http://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [マネージド VSPackage](../misc/managed-vspackages.md)