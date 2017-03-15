---
title: "方法: ツールボックスのドラッグ アンド ドロップ機能のサポート | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドラッグ アンド ドロップ、ツールボックスでのサポート"
  - "ツールボックス (Visual Studio SDK)、クライアント"
  - "ツールボックス (Visual Studio SDK)、ドラッグ アンド ドロップ"
ms.assetid: 2f73a03c-1eb1-4b88-9c1b-d63ba0e2ac90
caps.latest.revision: 18
caps.handback.revision: 18
manager: "douge"
---
# 方法: ツールボックスのドラッグ アンド ドロップ機能のサポート
> [!NOTE]
>  ツールボックスにカスタム コントロールを追加する場合、Visual Studio 10 SDK に付属するツールボックス コントロール テンプレートを使用する方法をお勧めします。このテンプレートは、ドラッグ アンド ドロップをサポートしています。 このトピックは、下位互換性を保ち、既存のコントロールを使用して作業する目的でのみ保持されています。  
>   
>  テンプレートを使用してツールボックス コントロールを作成する方法の詳細については、「[方法: Windows フォームを使用するツールボックス コントロールを作成する](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)」および「[WPF ツールボックス コントロールを作成します。](../extensibility/creating-a-wpf-toolbox-control.md)」をご覧ください。  
  
 VSPackage で、エディターやデザイナーなどの文書の表示に**ツールボックス** コントロールを使用する場合は、ドラッグ アンド ドロップのサポートを実装する必要があります。  
  
 既定で、<xref:System.Windows.Forms.Control?displayProperty=fullName> から派生した [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] オブジェクトはすべて、**ツールボックス** コントロールを使用するためのサポートを自動的かつ透過的に提供するため、以下に示す手順は必要ありません。 デザイナーを作成すると、基本機能を拡張できます。  
  
 詳細については、[Windows フォームの概要](../Topic/Windows%20Forms%20Overview.md) および [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md) を参照してください。  
  
### 基本的なドラッグ アンド ドロップ機能を実装するには  
  
1.  <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget> をビュー オブジェクトに実装して、ドラッグ アンド ドロップのサポートを提供します。 これにより、ビューでの OLE ドラッグ アンド ドロップ機能やコントロールのシリアル化が可能になります。  
  
     ドラッグ アンド ドロップ機能を実装する方法については、「[ドラッグ アンド ドロップ \(OLE\)](/visual-cpp/mfc/drag-and-drop-ole)」をご覧ください。  
  
     ドロップできるのは、クリップボード アイテムか、デザイナーにドロップされるコントロールのいずれかです。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **ツールボックス**でサポートされる標準のクリップボード形式については、「[ツールボックスの拡張](../misc/extending-the-toolbox.md)」をご覧ください。  
  
2.  ドキュメント ビューの <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> インターフェイスの基本的な実装を提供します。  
  
     ユーザーがツールボックス コントロールをビューにドラッグしようとすると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] シェルはビューの VSPackage にクエリを実行して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> インターフェイスが実装されているか確認します。  
  
    1.  ドロップ先がサポートする**ツールボックス**形式に対して <xref:Microsoft.VisualStudio.VSConstants.S_OK> を返すようにするには、<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A> を実装します。 次の例では、データ オブジェクトがカスタム クリップボード形式 \(`CF_CUSTOM_FORMAT`\) であるかどうか、および ActiveX コントロールであるかどうかをチェックします。  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::IsSupported(IDataObject* pDO) { HRESULT hr; STGMEDIUM stm; if (!pDO) return E_POINTER; // Determine if the data object is in the Custom clip board format // fetc is the dialog editor toolbox item template. FORMATETC fetc = { m_CF_CUSTOM_FORMAT, //Value set with RegisterClipboardFormat NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (FAILED(hr = pDO->GetData(&fetc, &stm))) { // Determine if the object is in the class-id clipboard format ... this // would be the case if the control is an activeX toolbox item. FORMATETC xfetc = { m_CF_CLSID, NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (SUCCEEDED(hr = pDO->GetData(&xfetc,&stm))) { USES_CONVERSION; GUID guid; LPSTR pData = (LPSTR)GlobalLock(stm.hGlobal); if (pData) { // Convert from the string format to a binary GUID. if (CLSIDFromString(A2W(pData), &guid) != S_OK) return E_FAIL; // HTML data objects could have CLSID format ... so any data object could // be returned as a NULL guid ... fail on null guid, obviously they are // not active X controls. if (guid == GUID_NULL) return E_FAIL; } } } return hr; }  
        ```  
  
         IDE は、ビューのウィンドウが初めて読み込まれるときにこの情報をチェックします。また、ユーザーが IDE の **\[ツールボックス**の**カスタマイズ\]** ダイアログ ボックスから**ツールボックス**をリセットした後でビューのウィンドウをアクティブ化する時にも毎回チェックします。 通常、サポートされていない**ツールボックス** アイテムは、**ツールボックス**に表示されません。  
  
         ユーザーは、常にツールボックスのすべてのページが表示されるようにオプションを設定できます。 この場合、環境は <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A> のエディターに対してクエリを実行しません。  
  
    2.  上記で説明したような <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget> の実装により、ドロップされたコンポーネントが正常に処理された後で、ビュー オブジェクトは <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.DataUsed%2A> を呼び出して [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 環境にこれを通知する必要があります。  
  
     必要に応じ、VSPackage の <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> 実装を拡張して、VSPackage のドラッグ アンド ドロップのサポートを拡張できます。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> の実装で、マウスの操作ではなく、選択による**ツールボックス** アイテムのウィンドウへのドラッグをサポートできます。 つまり、ユーザーが**ツールボックス** アイテムをダブルクリックするか、シングルクリックして ENTER キーを押すことでドラッグできるようになります。 この操作を行うには、次の手順を実行します。  
  
    1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A> メソッドを実装します。  
  
         このメソッドは、IDE によって呼び出され、クリックするか ENTER キーを押すことにより選択されます。  
  
         このメソッドでは、**ツールボックス** アイテムをターゲット ウィンドウに挿入することが必要です。  
  
    2.  選択による実装をサポートしない場合、メソッドは <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> を返します。  
  
         次の例では、<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A> メソッドの実装で、選択したオブジェクトがサポートされているか確認し、サポートされている場合は、オブジェクトをコードに逆シリアル化します。  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::ItemPicked(IDataObject* pDataObject) { if (!pDataObject) return E_POINTER; UINT nIDTool; if (IsSupported(pDataObject) == S_OK) { SetToolCursor(); m_pDataObject = pDataObject; nIDTool = DeserializeObject(); // Get the focus back m_pResObject->m_spWndFrame->Show(); return S_OK; } }  
        ```  
  
4.  次の手順を実行して、アプリケーションに適したフォーカスが維持されていることを確認します。  
  
    1.  エディター ウィンドウが、異なる 2 つのビューではなく、異なる 2 つのウィンドウを実装する場合は、エディター ウィンドウ内でウィンドウのアクティブ化を切り替えるときに <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.UpdateToolboxUI%2A> メソッドを呼び出します。 ウィンドウ内でアクティブ化の変更が発生するタイミングはユーザーだけがわかります。  
  
    2.  ウィンドウを正常にアクティブ化し、コマンド ルーティングが正常に更新されるようにするには、コンポーネントで <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> メソッドを呼び出す必要があります。 この操作は、ツールボックスを含むドラッグ アンド ドロップ操作によって作成されるか変更された、エディターなどのコンポーネント ウィンドウにフォーカスが設定されているときに実行する必要があります。  
  
 VSPackage がドラッグ操作に介入し、ドロップされたアイテムを <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook> インターフェイスを介して変更することが必要な場合があります。  
  
 たとえば、新しい**ツールボックス** コントロールを明示的に**ツールボックス**に加えるのではなく、標準の**ツールボックス**がドロップされるときに VSPackage がインターセプトし、カスタム実装に置き換える場合があります。  
  
### ツールボックス コントロールを動的に変更するには  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook> メソッドを実装します。  
  
     **ツールボックス** アイテムが選択されるかドロップされると、**ツールボックス**は必ずドロップ先に対してクエリを実行し、ターゲットが <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook> インターフェイスをサポートしているか確認して、サポートしている場合は <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A> メソッドを呼び出します。  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A> メソッドは、元の <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject> の代わりに使用する新しい <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject> オブジェクトを返す必要があります。  
  
     ドロップ先がデータ オブジェクトを上書きする必要がない場合は、入力を返します。  
  
 VSPackage では、Ctrl キーと Shift キーを押しながら V キーを押すと、クリップボードのコンテンツを切り替えることができます。  
  
### クリップボード リングをサポートするには  
  
1.  次のものを使用して、`CMDIDPasteNextTBXCBItem` コマンドのハンドラーを実装します。  
  
    -   相互運用アセンブリ ベースの VSPackage 用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
    -   Managed Package Framework ベースの VSPackage 用 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>。<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler> インターフェイス。  
  
2.  コマンド ハンドラーに、切り替えられるクリップボード オブジェクトがあるかどうかを判断するための <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.AreDataObjectsAvailable%2A> メソッドを実装します。  
  
    1.  ツールボックスのクリップボードにアイテムがない場合、環境はシステム クリップボードにアイテムがあるかどうかを確認します。  
  
    2.  アイテムがツールボックスのクリップボードにはなく、システム クリップボードにある場合、クリップボード リングにシステム アイテムが設定されます。  
  
    3.  リスト内の次のアイテムを選択する場合、この実装は <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.GetAndSelectNextDataObject%2A> メソッドを呼び出します。  
  
    4.  クリップボード サイクルの先頭に戻るには、<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.BeginCycle%2A> メソッドを呼び出します。  
  
## 参照  
 [ツールボックスの拡張](../misc/extending-the-toolbox.md)   
 [方法: 相互運用アセンブリを使用したカスタム ツールボックス項目の提供](../Topic/How%20to:%20Provide%20Custom%20Toolbox%20Items%20By%20Using%20Interop%20Assemblies.md)   
 [高度なツールボックス コントロールの開発](/visual-cpp/misc/advanced-toolbox-control-development)   
 [ツールボックスのサポート機能の登録](../misc/registering-toolbox-support-features.md)   
 [ツールボックスの管理](/visual-cpp/misc/managing-the-toolbox)