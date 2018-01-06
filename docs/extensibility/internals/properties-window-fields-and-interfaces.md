---
title: "プロパティ ウィンドウのフィールドとインターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1f238cceb189723e3ec10fbf8db4abbd9675ae21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="properties-window-fields-and-interfaces"></a>プロパティ ウィンドウのフィールドとインターフェイス
モデルの選択で表示される情報を決定する、**プロパティ**ウィンドウは IDE でフォーカスのあるウィンドウに基づきます。 すべてのウィンドウ、および選択した期間内のオブジェクトには、その選択コンテキスト オブジェクトのグローバルの選択コンテキストにプッシュされたことができます。 環境は、そのウィンドウにフォーカスがあるときに、ウィンドウ フレームの値を持つグローバルの選択コンテキストを更新します。 フォーカスが変更されたときにも選択コンテキスト。  
  
## <a name="tracking-selection-in-the-ide"></a>IDE での選択の追跡  
 ウィンドウ フレームや、IDE が所有するサイトが呼び出されるサービス<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>です。 次の手順が別の開いているウィンドウにフォーカスを変更するか、内の別のプロジェクト項目を選択すると、ユーザーによる、選択した方法の変更を表示する**ソリューション エクスプ ローラー**、に表示される内容を変更するのには**プロパティ**ウィンドウです。  
  
1.  選択したウィンドウの呼び出しで配置されている VSPackage によって作成されたオブジェクト<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>が<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>です。  
  
2.  選択した期間によって提供される、選択コンテナーを作成、独自<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>オブジェクト。 選択内容、VSPackage を呼び出すと<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>環境では、リスナーに通知するなど、**プロパティ**ウィンドウで、変更します。 新しい選択に関連する階層と項目の情報へのアクセスも提供します。  
  
3.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>を渡すことで選択した階層アイテム、`VSHPROPID_BrowseObject`パラメーターを設定、<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>オブジェクト。  
  
4.  派生したオブジェクト、 [IDispatch インターフェイス](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)に対して返される<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>アイテムが要求されると、および環境にラップ、 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (次の手順を参照してください)。 環境は、2 つ目の呼び出しの呼び出しが失敗した場合、 `IVsHierarchy::GetProperty`、選択コンテナーを渡す<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>階層アイテムまたはアイテムを提供します。  
  
     VSPackage では作成されません、プロジェクト<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>を実装する、環境が指定したウィンドウ VSPackage のため (たとえば、**ソリューション エクスプ ローラー**) 構築<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>の代わりにします。  
  
5.  環境がのメソッドを呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>に基づいてオブジェクトを取得する、`IDispatch`インターフェイスを埋めるために、**プロパティ**ウィンドウです。  
  
 内の値、**プロパティ**ウィンドウが変更されたが、Vspackage 実装`IVsTrackSelectionEx::OnElementValueChangeEx`と`IVsTrackSelectionEx::OnSelectionChangeEx`要素の値に変更を報告するようにします。 次に、環境を呼び出して<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>または<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>に表示される情報を保持する、**プロパティ**プロパティ値を持つウィンドウが同期されています。 詳細については、次を参照してください。[プロパティ ウィンドウでプロパティの値を更新](#updating-property-values-in-the-properties-window)です。  
  
 別の選択をするだけでなくプロジェクト項目で**ソリューション エクスプ ローラー**その項目に関連するプロパティを表示するで利用可能なドロップダウン リストを使用して、フォームまたはドキュメント ウィンドウ内から別のオブジェクトも選択できます、**プロパティ**ウィンドウです。 詳細については、次を参照してください。[プロパティ ウィンドウのオブジェクト一覧](../../extensibility/internals/properties-window-object-list.md)です。  
  
 情報の表示方法を変更することができます、**プロパティ**をカテゴリ別にアルファベット順から、ウィンドウのグリッド、で適切なボタンをクリックして、選択したオブジェクトのプロパティページを開くことができますも、使用可能な場合とは、**プロパティ**ウィンドウです。 詳細については、次を参照してください。[プロパティ ウィンドウのボタン](../../extensibility/internals/properties-window-buttons.md)と[プロパティ ページ](../../extensibility/internals/property-pages.md)です。  
  
 最後に、下部、**プロパティ**ウィンドウで選択したフィールドの説明も含まれています、**プロパティ** ウィンドウのグリッドです。 詳細については、次を参照してください。[プロパティ ウィンドウからフィールドの説明を取得する](#getting-field-descriptions-from-the-properties-window)です。  
  
## <a name="updating-property-values-in-the-properties-window"></a>[プロパティ] ウィンドウでプロパティ値を更新します。
**[プロパティ]** ウィンドウをプロパティ値の変更と同期するには、2 つの方法があります。 最初に呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>へのアクセスと、環境で提供されるツールとドキュメントのウィンドウの作成など、基本の windowing 機能へのアクセスを提供するインターフェイスです。 次の手順は、この同期プロセスを説明したものです。  
  
### <a name="updating-property-values-using-ivsuishell"></a>IVsUIShell を使ってプロパティ値を更新する  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>IVsUIShell インターフェイスを使ってプロパティ値を更新するには  
  
1.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>(を通じて<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>サービス) を Vspackage では、プロジェクトでは、いつでもまたはエディターを作成したり、ツールまたはドキュメント ウィンドウを列挙したりする必要があります。  
  
2.  実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A>を保持する、**プロパティ**プロジェクトのプロパティの変更と同期ウィンドウ (またはによって参照されるその他の選択したオブジェクト、**プロパティ**ウィンドウ)を実装することがなく<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>を発生させる<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A>イベント。  
  
3.  実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>メソッド<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>を設定し、それぞれ、実装する階層を必要とせず、階層イベントのクライアント通知を無効にする<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>です。  
  
### <a name="updating-property-values-using-iconnection"></a>IConnection を使ってプロパティ値を更新する  
 **[プロパティ]** ウィンドウとプロパティ値の変更を同期する 2 番目の方法は、接続可能なオブジェクトに `IConnection` を実装することにより、発信インターフェイスの存在を示すことです。 プロパティ名をローカライズする場合から、オブジェクトを派生させる<xref:System.ComponentModel.ICustomTypeDescriptor>です。 <xref:System.ComponentModel.ICustomTypeDescriptor>実装を返すプロパティ記述子を変更し、プロパティの名前を変更できます。 派生する属性を作成する説明をローカライズするには、<xref:System.ComponentModel.DescriptionAttribute>と説明のプロパティをオーバーライドします。  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>IConnection インターフェイスを実装する際の考慮事項  
  
1.  `IConnection`列挙子サブオブジェクトへのアクセスを提供、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>インターフェイスです。 すべての接続ポイント サブオブジェクトへのアクセスも用意されています。 各を実装する、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>インターフェイスです。  
  
2.  すべての参照オブジェクトが実装を担当する、<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>イベント。 **[プロパティ]** ウィンドウは、 `IConnection`を通してイベントを設定することをお勧めします。  
  
3.  接続ポイントの実装で許容される接続の数 (1 つまたは複数) を制御する<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>です。 1 つのみのインターフェイスをできるようにする接続ポイントが返すことができる<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>から、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>メソッドです。  
  
4.  クライアントが呼び出すことができます、`IConnection`で列挙子サブオブジェクトへのアクセスを取得するインターフェイス、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>インターフェイスです。 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>インターフェイスは、各発信インターフェイス ID (IID) の接続ポイントを列挙し、呼び出すことができます。  
  
5.  `IConnection`接続でのポイント サブオブジェクトへのアクセスを得るために呼び出すこともできます、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>各発信 IID のインターフェイスです。 を介して、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>インターフェイス、クライアントが起動または接続可能なオブジェクトとクライアント自身の同期のアドバイザリ ループを終了します。クライアントが呼び出すことも、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>を持つ列挙子オブジェクトを取得するインターフェイス、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections>認識されるコネクションを列挙するインターフェイスです。  
  
## <a name="getting-field-descriptions-from-the-properties-window"></a>[プロパティ] ウィンドウからのフィールドの説明を取得します。
**[プロパティ]** ウィンドウの下部にある説明領域に、選択したプロパティ フィールドに関連する情報が表示されます。 この機能は既定で有効になっています。 説明フィールドを非表示にするには、 **[プロパティ]** ウィンドウを右クリックし、 **[説明]**をクリックします。 これにより、メニュー ウィンドウの **[説明]** タイトルの横のチェック マークが削除されます。 同じ手順を行って **[説明]** の表示をオンに戻すことにより、フィールドを再度表示できます。  
  
 説明フィールド内の情報に由来<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>です。 それぞれのメソッド、インターフェイス、コクラスなどには、タイプ ライブラリのローカライズされていない `helpstring` 属性を適用できます。 **プロパティ**ウィンドウから文字列を取得する<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>です。  
  
### <a name="to-specify-localized-help-strings"></a>ローカライズされたヘルプ文字列を指定するには  
  
1.  タイプ ライブラリ ( `helpstringdll` ) のライブラリ ステートメントに`typelib`属性を追加します。  
  
    > [!NOTE]
    >  この手順は、タイプ ライブラリがオブジェクト ライブラリ (.olb) ファイルにある場合は省略可能です。  
  
2.  文字列の `helpstringcontext` 属性を指定します。 `helpstring` 属性を指定することもできます。  
  
     これらの属性は、実際の.chm ファイルのヘルプ トピックに含まれる `helpfile` 属性と `helpcontext` 属性とは異なります。  
  
 強調表示されたプロパティ名を表示する説明情報を取得する、**プロパティ**ウィンドウ呼び出し<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A>が選択されているプロパティを指定すると、必要な`lcid`属性を文字列を出力します。 内部的には、<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2>で指定された .dll ファイルを検索、`helpstringdll`属性と呼び出し`DLLGetDocumentation`その .dll ファイル上で指定したコンテキストと`lcid`属性。  
  
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
  
 実装することにより、ローカライズされた名前とプロパティの説明を取得する別の方法は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>です。 このメソッドの実装に関連する詳細については、次を参照してください。[プロパティ ウィンドウのフィールドとインターフェイス](../../extensibility/internals/properties-window-fields-and-interfaces.md)です。  

## <a name="see-also"></a>参照  
 [プロパティの拡張](../../extensibility/internals/extending-properties.md)