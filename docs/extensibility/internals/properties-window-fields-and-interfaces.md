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
ms.openlocfilehash: 149c02918ec909c03c1102a5fc0f1643b79fb46d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883407"
---
# <a name="properties-window-fields-and-interfaces"></a>プロパティ ウィンドウのフィールドとインターフェイス
モデルの選択で表示される情報を決定する、**プロパティ**ウィンドウは IDE でフォーカスのあるウィンドウに基づきます。 すべてのウィンドウと、選択したウィンドウ内のオブジェクトには、その選択コンテキスト オブジェクトのグローバルの選択コンテキストにプッシュされることができます。 環境は、そのウィンドウにフォーカスがあるときに、ウィンドウ フレームの値でグローバルの選択コンテキストを更新します。 フォーカスが変更されたときにも選択コンテキスト。  
  
## <a name="tracking-selection-in-the-ide"></a>IDE での選択の追跡  
 ウィンドウ フレームまたは、IDE によって所有されているサイトと呼ばれるサービスを持つ<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>します。 もう 1 つ開いているウィンドウにフォーカスを変更するか、内の別のプロジェクト項目を選択すると、ユーザーが原因と、選択した方法を変更に、次の手順が表示**ソリューション エクスプ ローラー**、に表示される内容を変更するのには**プロパティ**ウィンドウ。  
  
1. 選択したウィンドウの呼び出しでは配置されている VSPackage によって作成されたオブジェクト<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>が<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>します。  
  
2. 選択したウィンドウ、によって提供される、選択コンテナーを作成、独自<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>オブジェクト。 呼び出すときに、選択内容、VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>環境では、すべてのリスナーに通知するなど、**プロパティ**ウィンドウで、変更します。 新しい選択範囲に関連する階層と項目の情報へのアクセスも提供します。  
  
3. 呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>で選択した階層アイテムを渡すと、`VSHPROPID_BrowseObject`パラメーターは設定します、<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>オブジェクト。  
  
4. 派生したオブジェクト、 [IDispatch インターフェイス](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)に対して返される<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>、項目は、次の要求、および環境にラップします、 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (次の手順を参照してください)。 環境は、2 番目の呼び出しの呼び出しが失敗した場合、 `IVsHierarchy::GetProperty`、選択コンテナーを渡す<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>階層アイテムまたはアイテムを指定します。  
  
    VSPackage を作成できませんが、プロジェクト<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>を実装する VSPackage に、環境が指定したウィンドウのため (たとえば、**ソリューション エクスプ ローラー**) を構築します<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>の代わりに。  
  
5. 環境のメソッドを呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>に基づいてオブジェクトを取得、`IDispatch`インターフェイスを埋めるために、**プロパティ**ウィンドウ。  
  
   内の値、**プロパティ**ウィンドウが変更には、Vspackage 実装`IVsTrackSelectionEx::OnElementValueChangeEx`と`IVsTrackSelectionEx::OnSelectionChangeEx`要素の値に変更を報告します。 環境が呼び出され、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>または<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>に表示される情報を保持する、**プロパティ**ウィンドウは、プロパティの値と同期します。 詳細については、次を参照してください。[プロパティ ウィンドウでプロパティ値を更新](#updating-property-values-in-the-properties-window)します。  
  
   別の選択をするだけでなくプロジェクト項目で**ソリューション エクスプ ローラー**その項目に関連するプロパティを表示するで使用可能なドロップダウン リストを使用して、フォームまたはドキュメント ウィンドウ内から別のオブジェクトも選択できます、**プロパティ**ウィンドウ。 詳細については、次を参照してください。[プロパティ ウィンドウのオブジェクト一覧](../../extensibility/internals/properties-window-object-list.md)します。  
  
   情報の表示方法を変更することができます、**プロパティ**からアルファベット順をカテゴリ別のウィンドウのグリッドまた、、で適切なボタンをクリックして、選択したオブジェクトのプロパティページを開くことも、使用可能な場合。**プロパティ**ウィンドウ。 詳細については、次を参照してください。[プロパティ ウィンドウのボタン](../../extensibility/internals/properties-window-buttons.md)と[プロパティ ページ](../../extensibility/internals/property-pages.md)します。  
  
   最後に、下部にある、**プロパティ**ウィンドウで選択したフィールドの説明も含まれています、**プロパティ** ウィンドウのグリッド。 詳細については、次を参照してください。[プロパティ ウィンドウからフィールドの説明を取得する](#getting-field-descriptions-from-the-properties-window)します。  
  
## <a name="updating-property-values-in-the-properties-window"></a> [プロパティ] ウィンドウでプロパティ値を更新します。
**[プロパティ]** ウィンドウをプロパティ値の変更と同期するには、2 つの方法があります。 1 番目の方法は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> インターフェイスを呼び出すことです。このインターフェイスは、環境によって用意されているツール ウィンドウやドキュメント ウィンドウのアクセスや作成を含む、基本的なウィンドウ操作機能へのアクセスを提供します。 次の手順は、この同期プロセスを説明したものです。  
  
### <a name="updating-property-values-using-ivsuishell"></a>IVsUIShell を使ってプロパティ値を更新する  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>IVsUIShell インターフェイスを使ってプロパティ値を更新するには  
  
1.  VSPackage、プロジェクト、エディターがツール ウィンドウまたはドキュメント ウィンドウを作成したり列挙したりする必要が生じた時点で、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> を (<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> サービスを通じて) 呼び出します。  
  
2.  実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A>保持する、**プロパティ**ウィンドウとプロジェクトのプロパティの変更を同期 (またはによって参照されているその他の選択したオブジェクト、**プロパティ**ウィンドウ)を実装することがなく<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>および発生<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A>イベント。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> のメソッド <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> および <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> を実装します。この 2 つのメソッドは、それぞれ、階層イベントのクライアント通知を設定および無効化します。これにより、階層で <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> を実装する必要がなくなります。  
  
### <a name="updating-property-values-using-iconnection"></a>IConnection を使ってプロパティ値を更新する  
 **[プロパティ]** ウィンドウとプロパティ値の変更を同期する 2 番目の方法は、接続可能なオブジェクトに `IConnection` を実装することにより、発信インターフェイスの存在を示すことです。 プロパティ名をローカライズする場合は、オブジェクトを <xref:System.ComponentModel.ICustomTypeDescriptor> から派生させます。 <xref:System.ComponentModel.ICustomTypeDescriptor> の実装では、実装から返すプロパティ記述子を変更し、プロパティの名前を変更できます。 説明をローカライズするには、<xref:System.ComponentModel.DescriptionAttribute> から派生させた属性を作成し、Description プロパティをオーバーライドします。  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>IConnection インターフェイスを実装する際の考慮事項  
  
1.  `IConnection` は、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> インターフェイスを持つ列挙子サブオブジェクトへのアクセスを提供します。 また、すべての接続ポイント サブオブジェクトへのアクセスも提供し、それぞれは <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> インターフェイスを実装します。  
  
2.  すべての参照オブジェクトは、<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> イベントを実装する必要があります。 **[プロパティ]** ウィンドウは、 `IConnection`を通してイベントを設定することをお勧めします。  
  
3.  接続ポイントは、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> の実装で許容される接続数 (1 つまたは複数) を制御します。 インターフェイスを 1 つのみ許容する接続ポイントでは、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> メソッドから <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> を返すことができます。  
  
4.  クライアントは、`IConnection` インターフェイスを呼び出すことにより、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> インターフェイスを持つ列挙子サブオブジェクトへのアクセスを取得できます。 その後、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> インターフェイスを呼び出すと、各発信インターフェイス ID (IID) の接続ポイントを列挙することができます。  
  
5.  また、`IConnection` を呼び出すことにより、各発信 IID への <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> インターフェイスを持つ接続ポイント サブオブジェクトへのアクセスを取得することもできます。 クライアントは、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> インターフェイスを通して、接続可能オブジェクトとクライアント自身の同期のアドバイザリ ループを開始または終了します。クライアントは、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> インターフェイスを呼び出すこともできます。これにより、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> インターフェイスを持つ列挙子オブジェクトを取得して、既知の接続を列挙します。  
  
## <a name="getting-field-descriptions-from-the-properties-window"></a> [プロパティ] ウィンドウからフィールドの説明の取得
**[プロパティ]** ウィンドウの下部にある説明領域に、選択したプロパティ フィールドに関連する情報が表示されます。 この機能は既定で有効になっています。 説明フィールドを非表示にするには、 **[プロパティ]** ウィンドウを右クリックし、 **[説明]** をクリックします。 これにより、メニュー ウィンドウの **[説明]** タイトルの横のチェック マークが削除されます。 同じ手順を行って **[説明]** の表示をオンに戻すことにより、フィールドを再度表示できます。  
  
 説明フィールド内の情報は <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> から取得されます。 それぞれのメソッド、インターフェイス、コクラスなどには、タイプ ライブラリのローカライズされていない `helpstring` 属性を適用できます。 **プロパティ**ウィンドウから文字列を取得する<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>します。  
  
### <a name="to-specify-localized-help-strings"></a>ローカライズされたヘルプ文字列を指定するには  
  
1. タイプ ライブラリ ( `helpstringdll` ) のライブラリ ステートメントに`typelib`属性を追加します。  
  
   > [!NOTE]
   >  この手順は、タイプ ライブラリがオブジェクト ライブラリ (.olb) ファイルにある場合は省略可能です。  
  
2. 文字列の `helpstringcontext` 属性を指定します。 `helpstring` 属性を指定することもできます。  
  
    これらの属性は、実際の.chm ファイルのヘルプ トピックに含まれる `helpfile` 属性と `helpcontext` 属性とは異なります。  
  
   強調表示されているプロパティ名に表示される説明情報を取得する、**プロパティ**ウィンドウ呼び出し<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A>が選択されているプロパティの指定、必要な`lcid`属性を文字列を出力します。 内部的には、<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> は `helpstringdll` 属性で指定された .dll ファイルを検索し、指定されたコンテキストと `lcid` 属性を使ってその .dll ファイル上に `DLLGetDocumentation` を呼び出します。  
  
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
  
 idl の `helpstringcontext` 属性と `DLLGetDocumentation` によって取得したローカライズされた情報を取得する場合は、実装する必要のある追加のインターフェイスはありません。  
  
 別の方法でプロパティのローカライズされた名前と説明の取得には、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> を実装します。 このメソッドの実装に関する詳細については、「 [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md)」を参照してください。  

## <a name="see-also"></a>関連項目  
 [プロパティの拡張](../../extensibility/internals/extending-properties.md)