---
title: Properties Window Fields and インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 31ff83f412380de4ea0eda37d2be53ccb8b59d41
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512198"
---
# <a name="properties-window-fields-and-interfaces"></a>プロパティ ウィンドウのフィールドとインターフェイス
モデルの選択で表示される情報を決定する、**プロパティ**ウィンドウは IDE でフォーカスのあるウィンドウに基づきます。 すべてのウィンドウと、選択したウィンドウ内のオブジェクトには、その選択コンテキスト オブジェクトのグローバルの選択コンテキストにプッシュされることができます。 環境は、そのウィンドウにフォーカスがあるときに、ウィンドウ フレームの値でグローバルの選択コンテキストを更新します。 フォーカスが変更されたときにも選択コンテキスト。  
  
## <a name="tracking-selection-in-the-ide"></a>IDE での選択の追跡  
 ウィンドウ フレームまたは、IDE によって所有されているサイトと呼ばれるサービスを持つ<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>します。 もう 1 つ開いているウィンドウにフォーカスを変更するか、内の別のプロジェクト項目を選択すると、ユーザーが原因と、選択した方法を変更に、次の手順が表示**ソリューション エクスプ ローラー**、に表示される内容を変更するのには**プロパティ**ウィンドウ。  
  
1.  選択したウィンドウの呼び出しでは配置されている VSPackage によって作成されたオブジェクト<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>が<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>します。  
  
2.  選択したウィンドウ、によって提供される、選択コンテナーを作成、独自<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>オブジェクト。 呼び出すときに、選択内容、VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>環境では、すべてのリスナーに通知するなど、**プロパティ**ウィンドウで、変更します。 新しい選択範囲に関連する階層と項目の情報へのアクセスも提供します。  
  
3.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>で選択した階層アイテムを渡すと、`VSHPROPID_BrowseObject`パラメーターは設定します、<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>オブジェクト。  
  
4.  派生したオブジェクト、 [IDispatch インターフェイス](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)に対して返される<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>、項目は、次の要求、および環境にラップします、 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (次の手順を参照してください)。 環境は、2 番目の呼び出しの呼び出しが失敗した場合、 `IVsHierarchy::GetProperty`、選択コンテナーを渡す<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>階層アイテムまたはアイテムを指定します。  
  
     VSPackage を作成できませんが、プロジェクト<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>を実装する VSPackage に、環境が指定したウィンドウのため (たとえば、**ソリューション エクスプ ローラー**) を構築します<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>の代わりに。  
  
5.  環境のメソッドを呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>に基づいてオブジェクトを取得、`IDispatch`インターフェイスを埋めるために、**プロパティ**ウィンドウ。  
  
 内の値、**プロパティ**ウィンドウが変更には、Vspackage 実装`IVsTrackSelectionEx::OnElementValueChangeEx`と`IVsTrackSelectionEx::OnSelectionChangeEx`要素の値に変更を報告します。 環境が呼び出され、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>または<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>に表示される情報を保持する、**プロパティ**ウィンドウは、プロパティの値と同期します。 詳細については、次を参照してください。[プロパティ ウィンドウでプロパティ値を更新](#updating-property-values-in-the-properties-window)します。  
  
 別の選択をするだけでなくプロジェクト項目で**ソリューション エクスプ ローラー**その項目に関連するプロパティを表示するで使用可能なドロップダウン リストを使用して、フォームまたはドキュメント ウィンドウ内から別のオブジェクトも選択できます、**プロパティ**ウィンドウ。 詳細については、次を参照してください。[プロパティ ウィンドウのオブジェクト一覧](../../extensibility/internals/properties-window-object-list.md)します。  
  
 情報の表示方法を変更することができます、**プロパティ**からアルファベット順をカテゴリ別のウィンドウのグリッドまた、、で適切なボタンをクリックして、選択したオブジェクトのプロパティページを開くことも、使用可能な場合。**プロパティ**ウィンドウ。 詳細については、次を参照してください。[プロパティ ウィンドウのボタン](../../extensibility/internals/properties-window-buttons.md)と[プロパティ ページ](../../extensibility/internals/property-pages.md)します。  
  
 最後に、下部にある、**プロパティ**ウィンドウで選択したフィールドの説明も含まれています、**プロパティ** ウィンドウのグリッド。 詳細については、次を参照してください。[プロパティ ウィンドウからフィールドの説明を取得する](#getting-field-descriptions-from-the-properties-window)します。  
  
## <a name="updating-property-values-in-the-properties-window"></a> [プロパティ] ウィンドウでプロパティ値を更新します。
**[プロパティ]** ウィンドウをプロパティ値の変更と同期するには、2 つの方法があります。 最初に呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>へのアクセスと、環境によって提供されるツールとドキュメント ウィンドウの作成など、基本的なウィンドウ操作機能へのアクセスを提供するインターフェイス。 次の手順は、この同期プロセスを説明したものです。  
  
### <a name="updating-property-values-using-ivsuishell"></a>IVsUIShell を使ってプロパティ値を更新する  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>IVsUIShell インターフェイスを使ってプロパティ値を更新するには  
  
1.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>(を通じて<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>サービス) いつでも、Vspackage、プロジェクト、またはエディターを作成したり、ツールまたはドキュメント ウィンドウを列挙したりする必要があります。  
  
2.  実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A>保持する、**プロパティ**ウィンドウとプロジェクトのプロパティの変更を同期 (またはによって参照されているその他の選択したオブジェクト、**プロパティ**ウィンドウ)を実装することがなく<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>および発生<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A>イベント。  
  
3.  実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>メソッド<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>を確立し、それぞれ実装するために、階層を必要とせず、階層イベントのクライアント通知を無効にする<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>します。  
  
### <a name="updating-property-values-using-iconnection"></a>IConnection を使ってプロパティ値を更新する  
 **[プロパティ]** ウィンドウとプロパティ値の変更を同期する 2 番目の方法は、接続可能なオブジェクトに `IConnection` を実装することにより、発信インターフェイスの存在を示すことです。 プロパティ名をローカライズする場合は、派生オブジェクトの<xref:System.ComponentModel.ICustomTypeDescriptor>します。 <xref:System.ComponentModel.ICustomTypeDescriptor>実装が返すプロパティ記述子を変更して、プロパティの名前を変更します。 説明をローカライズするから派生する属性を作成します。<xref:System.ComponentModel.DescriptionAttribute>と説明のプロパティをオーバーライドします。  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>IConnection インターフェイスを実装する際の考慮事項  
  
1.  `IConnection` 列挙子サブオブジェクトへのアクセスを提供します、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>インターフェイス。 すべての接続ポイント サブオブジェクトへのアクセスも用意されています。 それぞれの実装、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>インターフェイス。  
  
2.  すべての参照オブジェクトを実装する責任を負いますが、<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>イベント。 **[プロパティ]** ウィンドウは、 `IConnection`を通してイベントを設定することをお勧めします。  
  
3.  接続ポイントの実装でできます (1 つまたは複数) の接続の数を制御する<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>します。 1 つだけのインターフェイスをできるようにする接続ポイントを返すことができます<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>から、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>メソッド。  
  
4.  クライアントが呼び出すことができます、`IConnection`で列挙子サブオブジェクトへのアクセスを取得するインターフェイス、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>インターフェイス。 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>インターフェイスは、各発信インターフェイス ID (IID) の接続ポイントを列挙し、呼び出すことができます。  
  
5.  `IConnection` 接続でのポイント サブオブジェクトへのアクセスの取得を呼び出すこともできます、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>各発信 IID のインターフェイス。 を通じて、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>インターフェイス、クライアントが開始または接続可能オブジェクトとクライアントの同期のアドバイザリ ループを終了します。クライアントが呼び出すことも、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>を持つ列挙子オブジェクトを取得するインターフェイス、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections>について認識して接続を列挙するインターフェイス。  
  
## <a name="getting-field-descriptions-from-the-properties-window"></a> [プロパティ] ウィンドウからフィールドの説明の取得
**[プロパティ]** ウィンドウの下部にある説明領域に、選択したプロパティ フィールドに関連する情報が表示されます。 この機能は既定で有効になっています。 説明フィールドを非表示にするには、 **[プロパティ]** ウィンドウを右クリックし、 **[説明]** をクリックします。 これにより、メニュー ウィンドウの **[説明]** タイトルの横のチェック マークが削除されます。 同じ手順を行って **[説明]** の表示をオンに戻すことにより、フィールドを再度表示できます。  
  
 説明フィールド内の情報に由来<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>します。 それぞれのメソッド、インターフェイス、コクラスなどには、タイプ ライブラリのローカライズされていない `helpstring` 属性を適用できます。 **プロパティ**ウィンドウから文字列を取得する<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>します。  
  
### <a name="to-specify-localized-help-strings"></a>ローカライズされたヘルプ文字列を指定するには  
  
1.  タイプ ライブラリ ( `helpstringdll` ) のライブラリ ステートメントに`typelib`属性を追加します。  
  
    > [!NOTE]
    >  この手順は、タイプ ライブラリがオブジェクト ライブラリ (.olb) ファイルにある場合は省略可能です。  
  
2.  文字列の `helpstringcontext` 属性を指定します。 `helpstring` 属性を指定することもできます。  
  
     これらの属性は、実際の.chm ファイルのヘルプ トピックに含まれる `helpfile` 属性と `helpcontext` 属性とは異なります。  
  
 強調表示されているプロパティ名に表示される説明情報を取得する、**プロパティ**ウィンドウ呼び出し<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A>が選択されているプロパティの指定、必要な`lcid`属性を文字列を出力します。 内部的には、<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2>で指定された .dll ファイルを検索、`helpstringdll`属性と呼び出し`DLLGetDocumentation`で指定したコンテキストを使ってその .dll ファイルと`lcid`属性。  
  
 `DLLGetDocumentation` の署名と実装は次のとおりです。  
  
```cpp  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 `DLLGetDocumentation` 関数はDLL の .def ファイルで定義されているエクスポートである必要があります。  
  
 内部的には、実際には DLL である .olb ファイルが作成されます。 この DLL には、1 つのリソース、タイプ ライブラリ (.tlb) ファイル、および 1 つのエクスポートされた `DLLGetDocumentation`関数が含まれます。  
  
 .olb ファイルの場合は、 `helpstringdll` 属性は.tlb ファイル自体を含む同じファイルであるため省略可能です。  
  
 したがって、 **[説明]** ウィンドウに表示する文字列を取得するために最低限必要な操作は、タイプ ライブラリに `helpstring` 属性を指定することです。 これらの文字列をローカライズする場合は、 `helpstringdll` (省略可能) 属性と `helpstringcontext` (必須) 属性を指定し、 `DLLGetDocumentation`を実装する必要があります  
  
 idl の `helpstringcontext` 属性と `DLLGetDocumentation`によって取得したローカライズされた情報を取得する場合は、実装する必要のある追加のインターフェイスはありません。  
  
 実装することで、ローカライズされた名前とプロパティの説明を取得する別の方法は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>します。 このメソッドの実装に関する詳細については、次を参照してください。 [Properties Window Fields and インターフェイス](../../extensibility/internals/properties-window-fields-and-interfaces.md)します。  

## <a name="see-also"></a>関連項目  
 [プロパティの拡張](../../extensibility/internals/extending-properties.md)